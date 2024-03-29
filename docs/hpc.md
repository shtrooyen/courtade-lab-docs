# HPC Stuff

## Passwordless login
`cd ~/.ssh` and `ssh-keygen` then edit config as below.

### ~/.ssh/config
```
Host *
User username
Compression yes
ForwardX11 yes
ForwardX11Trusted yes
XAuthLocation /opt/X11/bin/xauth

AddKeysToAgent yes
UseKeychain yes

Host ntnu
HostName login.ansatt.ntnu.no

IdentityFile ~/.ssh/mykey
```
Then execute `ssh-copy-id -i mykey.pub ntnu` to copy to host.

## Software installation
### Packages needed in herod
cmake
gnuplot
openmpi-bin
libopenmpi-dev
xclip

### GROMACS compile
Install cuda-toolkit from conda -c nvidia
activate conda environment

```
rm -r build
mkdir build
GMX_DIR=$(pwd)
cd build
cmake .. -DGMX_BUILD_OWN_FFTW=ON -DREGRESSIONTEST_DOWNLOAD=ON -DGMX_GPU=CUDA -DMPI_C_COMPILER=mpicc -DMPI_CXX_COMPILER=mpicxx -DCMAKE_INSTALL_PREFIX=$GMX_DIR
make
make check
```

Alternative, in case cmake and openmpi have to be manually compiled

```
#!/bin/bash

cmake=/cluster/courtade/software/cmake-3.25.0-linux-x86_64/bin/cmake
rm -r build
mkdir build
cd build
$cmake .. -DGMX_BUILD_OWN_FFTW=ON -DREGRESSIONTEST_DOWNLOAD=ON -DGMX_GPU=CUDA -DMPI_C_COMPILER=/cluster/courtade/software/openmpi-4.1.4/bin/mpicc -DMPI_CXX_COMPILER=/cluster/courtade/software/openmpi-4.1.4/bin/mpicxx
make
make check
make install
source /usr/local/gromacs/bin/GMXRC
```

### plumed installation
```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/courtade/programs/plumed-2.8.1/lib
export PLUMED_KERNEL=/home/courtade/programs/plumed-2.8.1/lib/libplumedKernel.so
plumed=/home/courtade/programs/plumed-2.8.1/bin/plumed
```

## slurm
### slurm.conf
```
# instant slurm file, automatically generated
ClusterName=herod
SlurmctldHost=localhost
SlurmdUser=root
MpiDefault=none
ProctrackType=proctrack/cgroup
ReturnToService=1
SlurmctldPidFile=/var/run/slurmctld.pid
SlurmctldPort=6817
SlurmdPidFile=/var/run/slurmd.pid
SlurmdPort=6818
SlurmdSpoolDir=/var/spool/slurmd
StateSaveLocation=/var/spool/slurmctld
SwitchType=switch/none
TaskPlugin=task/cgroup,task/affinity
InactiveLimit=0
KillWait=30
MinJobAge=300
SlurmctldTimeout=120
SlurmdTimeout=300
Waittime=0
SchedulerType=sched/builtin
SelectType=select/cons_tres
SelectTypeParameters=CR_Core_Memory
AccountingStorageType=accounting_storage/none
JobCompType=jobcomp/none
JobAcctGatherFrequency=30
JobAcctGatherType=jobacct_gather/none
SlurmctldDebug=info
SlurmctldLogFile=/var/log/slurmctld.log
SlurmdDebug=info
SlurmdLogFile=/var/log/slurmd.log

# node conf with gpu
GresTypes=gpu
PartitionName=normal Nodes=localhost Default=YES MaxTime=UNLIMITED State=UP
NodeName=localhost CPUs=32 Boards=1 SocketsPerBoard=2 CoresPerSocket=8 ThreadsPerCore=2 RealMemory=30000 Gres=gpu:2
```
### gres.conf
```
Name=gpu File=/dev/nvidia[0-1] Count=2
```

### cgroup.conf
```
CgroupAutomount=yes
ConstrainCores=no
ConstrainDevices=yes
ConstrainRAMSpace=no
ConstrainSwapSpace=no
```

## daily backup
The daily-backup.sh script

```bash
#!/bin/bash
# ----------------------------------------------------------------------
# mikes handy rotating-filesystem-snapshot utility
# ----------------------------------------------------------------------
# this needs to be a lot more general, but the basic idea is it makes
# rotating backup-snapshots of /home whenever called
# ----------------------------------------------------------------------
# GC: deletes oldest daily backup when running out of space
# GC: makes a new folder with date
#

unset PATH	# suggestion from H. Milz: avoid accidental use of $PATH

# ------------- system commands used by this script --------------------
ID=/usr/bin/id;
ECHO=/bin/echo;

MOUNT=/bin/mount;
UMOUNT=/bin/umount;
RM=/bin/rm;
MV=/bin/mv;
CP=/bin/cp;
TOUCH=/bin/touch;

RSYNC=/usr/bin/rsync;

DATE=/usr/bin/date;
DF=/usr/bin/df;
AWK=/usr/bin/awk;
FIND=/usr/bin/find;
SORT=/usr/bin/sort;
# ------------- file locations -----------------------------------------

MOUNT_DEVICE=/dev/sda1;
SNAPSHOT_RW=/backup;
EXCLUDES=/home/courtade/backup_exclude;


# ------------- the script itself --------------------------------------

# make sure we're running as root
if (( `$ID -u` != 0 )); then { $ECHO "Sorry, must be root.  Exiting..."; exit; } fi

# attempt to remount the RW mount point as RW; else abort
$UMOUNT $SNAPSHOT_RW ;
$MOUNT -o rw $MOUNT_DEVICE $SNAPSHOT_RW ;
if (( $? )); then
{
	$ECHO "snapshot: could not remount $SNAPSHOT_RW readwrite";
	exit;
}
fi;


# step 1:  get date
today=$($DATE +%F);

# step 2:  free space if necessary
cd $SNAPSHOT_RW/work/
a=$($DF . | $AWK 'NR>1 {print $4}')
a2=${a::-1}
$ECHO "$a2"
while [[ $a2 < 20000000 ]];
do
	IFS= read -r -d $'\0' line < <($FIND . -maxdepth 1 -type d -printf '%T@ %p\0' \
		2>/dev/null | $SORT -z -n)
	file="${line#* }"
        $RM -r  $file
done

cd /

# step 3: rsync from the system into the latest snapshot (notice that
# rsync behaves like cp --remove-destination by default, so the destination
# is unlinked first.  If it were not so, this would copy over the other
# snapshot(s) too!
$RSYNC										\
	-va --delete --delete-excluded --exclude-from="$EXCLUDES"  --mkpath	\
	/work/ $SNAPSHOT_RW/work/$today ;


# and thats it for home.

# now remount the RW snapshot mountpoint as readonly
$UMOUNT $SNAPSHOT_RW ;
$MOUNT -o ro $MOUNT_DEVICE $SNAPSHOT_RW ;
if (( $? )); then
{
	$ECHO "snapshot: could not remount $SNAPSHOT_RW readonly";
	exit;
} fi;
```

Run by placing the following script inide `/etc/cron.daily`. Remember to make it executable wih `chmod +x`.
```
#!/bin/bash
exec /usr/local/bin/daily-backup.sh
```

## sbatch script example
```
#!/bin/bash
#
#SBATCH --job-name=bench2
#SBATCH --gres=gpu:0
#SBATCH --mem=2G
#SBATCH --ntasks=1
#SBATCH --cpus-per-task=4
#SBATCH --partition=normal
#SBATCH --time=00:10:00
rm \#*
gmx=/home/courtade/programs/gromacs-2022.3/build/bin/gmx
#export GMX_DISABLE_GPU_DETECTION=1
cp benchMEM.tpr $SLURM_JOB_NAME.tpr
$gmx mdrun -deffnm $SLURM_JOB_NAME -ntmpi $SLURM_NTASKS -ntomp $SLURM_CPUS_PER_TASK
```

## ~/.bshrc
```
# User specific aliases and functions
export DISPLAY=$(echo $SSH_CLIENT | awk '{ print $1}'):0.0
export SLURMD=/usr/sbin/slurmd
export SLURMCONF=/etc/slurm/slurm.conf
export GRESCONF=/etc/slurm/gres.conf
export SINFO_FORMAT="%15o %.5D %12P %11T %15O %.6m %15E %.C %G"
export SQUEUE_FORMAT="%.18i %.9P %.14j %.8u %.8T %.10M  %.6D %.R %.b"
export SQUEUE_SORT="u,T"
alias squeue_me="squeue | grep -e courtade"
alias lsl="ls -ltrh"
```

