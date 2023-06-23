# Courtade Lab Docs

This is a repository for documents related to work carried out at the Courtade Lab. The general idea is that this website is kept up to date  with descriptions of protocols, methods, etc. Everyone in the group can edit this as long as you are given access to the GitHub repository.

Follow these steps to edit the docs on this website:

1. Create a GitHub account if you don't have one: https://github.com/
2. Ask Gaston for access to the `courtade-lab-docs` repository.
3. Inside the `docs/` folder, edit or create the markdown (`.md`) files either directly on GitHub, or by clonining the repository, adding, committing and pushing the changes.
4. If you created a new markdown file (e.g., `docs/new_cool_protocol.md`), you need to edit `mkdocs.yml` to add it to the navigation panel as follows:

```
nav:
    - Home: index.md
    - HPC Protocols: hpc.md
    - New cool protocol: new_cool_protocol.md #This is the new protocol
```

