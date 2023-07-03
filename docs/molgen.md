# Molecular Genetics Protocols


## Media
### 2xLB medium:
- 20 g/L tryptone
- 10 g/L yeast extract
- 5 g/L NaCl
- 1L water

### 1xLB-medium:
- 10 g/L tryptone
- 5 g/L yeast extract
- 5 g/L NaCl
- 1L water

### M9 medium, per 500 mL: 
- M9 salts (5X) 		100 mL		autoclaved
- MgSO4 	(1 M)		1 mL 		sf
- CaCl2 (1 M)		    50 µL	 	sf
- H2O 			    375 mL		sf
- MEM vitamins (100x)     5 mL 		
- Trace metals (1000x)	500 µL
- Glucose 		2 g in 10 mL	sf		4 g/L
- NH4SO4			0.5 g in 10 mL	sf		1 g/L
Autoclave M9 salts, sterile filter other components. Mix into autoclaved 500 mL flask to prepare M9 medium. 

### M9 salts (5X),  1 L:					500 mL:
- Na2HPO4 · 7H2O		64 g	(210 mM)		32 g
- KH2PO4 			    15 g	(110 mM)		7.5 g
- NaCl 			        2.5 g	(42.8 mM)		1.25 g
- H2O			        1 L			            500 mL
Autoclave and store at rt.

## Buffers
### Tris-HCl, 50 mM, 1 L
-	Tris-HCl, 7.88 g
-	1000 mL RO water
-	Adjust pH with NaOH to desired pH (pH 7-9).
-	Sterile filter.

200 mM NaCl: 11.69 g/L
300 mM NaCl: 17.53 g/L
1 M NaCl: 58.44 g/L
400 mM Imidazole = 27.24 g/L

### Spheroplast buffer, pH 7.5
-	100 mM Tris-HCl, pH 7.5		15.76 g/L
-	500 mM sucrose (342.3 g/mol)		171.15 g/L		
-	0.5 mM EDTA				1 mL 0.5 M EDTA per liter
-	Sterile filter.

### 50 mL 0.5 M EDTA solution:
Dissolve 9.30 g EDTA (292.24 g/mol) in 50 mL DI water. Adjust pH to 8 with NaOH (the EDTA salt will not dissolve unless pH is about 8). Sterile filter. 

## Transformation (heat-shock method)
-	Place a vial of supercompetent cells on ice (update the number of vials on the freezer). 
-	Add about 10 ng of DNA dissolved in SF MQ water to the cells (max 10 uL).
-	Incubate the cells on ice for 20 min. 
-	Heat shock the transformation tube in a 40°C water bath for 30 s. 
-	Put it back on ice for 2 min.  
-	Add 1 mL SOC medium to the tube (found in freezer).
-	Incubate in 37°C shaking incubator for 1 h. 
-	Dilute the solution x10 with SF MQ water. 
-	Plate out on LB agar plate with appropriate antibiotic (plates are in the cool room). 
    o	Add 100 µL of the diluted solution to the plate. 
    o	Spread out with sterilized cell spreader. 
-	Incubate (upside down) at 37°C overnight (16-18 h). The plates can be left in the refrigerator for a few weeks, sealed with parafilm. 


## ScCBM2-His production and purification
Cells: BL21_pNIC-ScCBM2-His_KanR
Buffer A: 50 mM Tris-HCl, pH 8.0, 500 mM NaCl
Buffer A: 50 mM Tris-HCl, pH 8.0, 500 mM NaCl, 400 mM imidazole

### Day 1:
-	In the morning, grow pre-culture. 
-	To an autoclaved shake-flask, add 5 mL LB + 5 uL kanamycin (stock: 50 mg/mL).
-	With a pipette tip, add cells to the flask. 
-	Incubate at 37°C, 225 rpm for at least 6 h. Without aluminium foil. 

-	In the evening, inoculate 2xLB (500 mL) + kanamycin (500 uL) with 1% pre-culture (5 mL). 
-	Incubate overnight at 22°C in LEX (add 1-1.5 mL antifoam) or in incubator at 225 rpm (incubator must be booked).
  
### Day 2: 
-	Induce with 0.5 mL 0.1 M IPTG (0.1 mM total concentration, IPTG in freezer). 
-	Incubate at 22°C, 225 rpm for 24 h.
  
### Day 3: 
-	Harvest the cells by centrifugation 5000 xg, 4°C for 10 min (book the centrifuge). 
-	Discharge the supernatant, keep the pellet. The pellet can be frozen at this point. 
-	Add one protease inhibitor tablet. Resuspend cells in 25 mL buffer A, while on ice. 
-	Sonicate at least 10 min, rest in between to keep cool (5 s on, 10 s off, total time 30 min)
-	Centrifuge at 25 000 xg, 4°C for 30 min.
    o	Increase the speed to 40 000 xg if the pellet is not properly sedimented. 
-	Sterile filter the supernatant and purify with FPLC. 
    o	Save 20 uL of the lysate to analyze with SDS-PAGE. 
    o	Connect HisTrap (1 mL) column.
    o	Wash the pumps with buffer.
    o	Insert collection rack.
    o	Place S1 in the sample. 
    o	Run FPLC protocol (flow rate: 1 mL/min, equilibrate: 5 CV 5% B, sample application, wash-out 10 CV 5% B, elution: 5-100% B over 30 CV. 
    o	Wash pumps with water and 20% EtOH.
    o	Remove column and collection rack. 
-	Test on SDS-PAGE, purify further with SEC if needed (SEC protocol described later).

## ScCBM2 (no His-tag) production and purification
Cells: ER2566_pRSET-B-ScCBM2_AmpR 
Buffer A: 50 mM Tris HCl, pH 7.5, sf
Buffer B: 50 mM Tris HCl, pH 7.5, 1M NaCl, sf
Buffer C: 50 mM Tris HCl, ph 7.5, 200 mM NaCl, sf

### Day 1: 
-	In the morning, inoculate 500 mL M9 medium + 500 uL amp stock (100 mg/mL) with cells. 
-	Add 1-1.5 mL antifoam solution and incubate in LEX at 37°C, 24 h. (Check OD, if below 0.4, let grow overnight, if not proceed.)
-	
### Day 2: 
-	Harvest the cells by centrifugation at 4000xg, 4°C for 10 min. Discard the supernatant. 
-	Rest the pellet on ice for 5 min. 
-	On ice, resuspend the pellet in 30 mL spheroplast buffer with 1 tablet protease inhibitor. 
-	Centrifuge at 5000xg, 4°C for 15 min. 
-	Keep the supernatant as the spheroplast fraction, sterile filter it.  
-	Rest the pellet in rt for 10 min. 
-	On ice, resuspend the pellet in 25 mL cold RO-water. 
-	Add 1.5 mL 20 mM MgCl2. 
-	Centrifuge at 15000xg, 4°C for 15 min. 
-	Sterile filter the supernatant and keep as the water fraction. 
-	Test spheroplast and water fraction on SDS-PAGE.

### Purification:
-	Add 1.5 mL 20x Buffer A to the water fraction. Precipitation may occur.
-	Centrifuge for 20 min at max speed (small centrifuge) and sterile filter the supernatant into a clean tube. 
-	Purify with IEX:
    o	Attach HiTrap DEAE FF column (5 mL) to the FPLC. 
    o	Wash pumps.
    o	Equilibrate with 5 CV Buffer A. 
    o	Sample application with sample pump  collect fractions 
    o	Wash out unbound with Buffer A, 10 CV  collect fractions
    o	Linear gradient 0-50% Buffer B, 60 CV  collect fractions
    o	100% Buffer B, 3 CV  collect fractions
    o	Wash column with water and 20% EtOH before storage. 
    o	Wash pumps. 
    o	Analyze with SDS-PAGE, combine fraction containing protein. 

-   2nd purification with SEC:
    o	Attach HiLoad 16/60 Superdex 75 column to the FPLC. 
    o	Wash pumps. 
    o	Equilibrate column with buffer C. 
    o	Sample application and elution. 
    o	Wash pumps and column with MQ water. 
    o	Wash pumps and column with 20% EtOH. 
    o	Analyze with SDS-PAGE, concentrate and exchange buffer if necessary. 

## Cutinase production and purification
Cells: ER2566_pET-3A-cutinase-wt-CBM2_AmpR
Buffer A: NaAc pH 5.0 buffer (20 to 50 mM is ok)
Buffer B: NaAc pH 5.0 buffer (20 to 50 mM is ok) with 1 M NaCl

### Day 1: 
-	In the morning, grow pre-culture. 
-	To an autoclaved shake-flask, add 5 mL LB + 5 uL ampicillin (stock: 100 mg/mL).
-	With a pipette tip, add cells to the flask. 
-	Incubate for at least 7 h (or overnight) at 37°C in a shaker. Incubate longer if no growth.
-	Inoculate 500 mL 2XLB + 500 uL amp stock with 1% pre-culture (5 mL).
-	Add 1-1.5 mL antifoam solution and incubate in LEX at 22°C overnight.
  
### Day 2: 
-	Check OD. If over 2.1, could be over the limit, dilute 10x and measure again, multiply the result with 10 to get the OD. If below 0.4 let the cells grow longer. 
-	Induce with 0.1 mM IPTG (500 µL of the 0.1 M stock). 
-	Incubate in LEX at 22°C for 24 h.
  
### Day 3: 
-	Harvest the cells by centrifugation for 5 min at 5000xg and 4°C. Discard the supernatant. 
-	Add 35 mL spheroplast buffer (from refrigerator) with a protease inhibitor tablet to the pellet.
-	Resuspend gently by stirring the cup on ice, use a metallic spoon if necessary. Avoid foam formation.
-	Centrifuge for 10 min at 6500 xg. Pour the supernatant into a clean tube labeled “Spheroplast fraction” and keep on ice.
-	Add 35 mL MilliQ water to the pellet.
-	Resuspend as in step 4.
-	Centrifuge for 45 min at maximum speed. Pour the supernatant into a clean tube labeled “Water fraction” and keep on ice.
-	Sterile filter both the “Spheroplast fraction” and the “Water fraction” by using a 0.2 µm syringe filter.
    o	The Spheroplast fraction usually contains a quite a lot of protein, you can try to do a SDS-PAGE on it. 
-	Add 2 mL 20x buffer to the “Water fraction” and mix. Precipitate may form.
-	Centrifuge for 20 min at maximum speed and sterile filter the supernatant into a clean tube.
-	Purify on FPLC by using an IEX_GCO or similar Method or make a new Method from scratch with the following parameters. The protein should elute at 4 – 12% approx.
    o	Connect the HiTrap CM FF 5 mL column
    o	Flow rate 5 mL/min all steps
    o	Equilibration with 5 CV Buffer A
    o	Sample application with sample pump  Collect fractions
    o	Wash out unbound with 10 CV Buffer A  Collect fractions
    o	Linear gradient 0 – 50 % Buffer B over 50 CV  Collect fractions
-	Analyze fractions with SDS-PAGE.



## SEC
-	The SEC column is next to the FPLC machine. 
-	The procedure consists of 3 stages, equilibration of the column with buffer, elution of the proteins and wash of the column with water and EtOH. 
-	Wash pump A, Buff and S1 with the buffer.
-	Insert the collection rack. 
-	Attach the column as follows:
    - Make sure no air bubbles enter the column. The column must be attached during buffer flow, and the sequence below must be followed in order. 
    - Start buffer flow on pump A (1 mL/min). 
    - On the column valve: switch from “Bypass” to “1”, “downstream” to make the flow go through the column. 
    - Make sure that the spring below the column has EtOH inside.
    - Open the tube to be attached at the top of the column (buffer should drip out). 
    - Open the upper tube on the column (EtOH should drip out). 
    - Attach the two tubes wet in wet. 
    - Find an adapter that fits the lower tube of the column (the same as the upper adapter). Attach it to the tube to be attached below the column. 
    - Remove the EtOH spring and attach the red part to the out-tube. 
    - Check that there is no leakage. 

-	Find and start the method FPLC_SEC_SHT (method contains equilibration and sample elution). 
-	Attach the sample on S1 and check that there are no bubbles in the tube. 
-	Check that there is enough buffer for the method, and enough MQ water and EtOH (20%) for the washing afterwards.
-	When the method is finished, wash the pumps with MQ water. 
-	Start the method SEC_wash_SHT, with MQ water. 
-	Wash the pumps with 20% EtOH. 
-	Start the wash method again with EtOH.  
-	At the end of the EtOH wash, or during manual EtOH flow, remove the column from the FPLC. 
    - Remove the bottom tube and attach the EtOH spring. Let it fill up.
    - Remove the upper tube and seal it. 
    - Assemble the FPLC tubes as they were. 
    - Put the column back.
-	Remember to take out the collection rack and the empty sample tube. 

## SDS-PAGE
All components of SDS page are from GenScript, found [here](https://www.genscript.com/product/documents?producttype=&cat_no=M42012&catalogtype=Document-PROTOCOL&Search=Search).

-	Determine which samples from FPLC/SEC to go on the gel, take out 20 µL of each sample. 
-	Dilute the lysate.
-	Add 20 µL of LDS (from freezer) to each sample. Concentrated LDS is in the fridge. LDS is a detergent with added reductant to reduce disulfide bonds and denature the protein.
-	Heat the samples at 95°C for 5 min. 
-	Assemble the SDS-PAGE chamber with the gel (from fridge). Remember to tear off the green tape on the bottom of the gel. 
-	Fill the chamber with MES SDS buffer (sachets in cupboard added to DI water). The outer chamber can be filled with reused buffer if needed. The inner chamber must be filled completely. Make sure that the inner chamber is tight and not leaking.  
-	Remove the green plastic thing on the gel. 
-	Apply 20 µL lysate, 5 µL ladder (from freezer), and 20 µL of all samples to the wells of the SDS-PAGE gel.
-	Run the gel at 200 V, 30 min with constant voltage.

### Staining/destaining
-	On the staining machine, take out one of the membrane plates A or B. 
-	Take a filter paper from beside the machine. 
-	Separate the plastic plates of the SDS-PAGE gel with the metal tool. 
-	Rinse the gel under water and place it on the membrane so that the wells are pointing towards the hinges of the membrane holder. 
-	Place a wetted filter paper over the gel and close the holder. 
-	Put into the machine. Make sure there is enough staining and destaining liquid. 
-	Start the process. 
-	Store the gel in water. Collect the pure protein fractions from FPLC. 
