# Repository Setup Instructions for Service Directory

This repository relies on a some features specific to the GitHub platform to function:

- Github Actions is used to collate the Service Directory entries in to the web-published `gh-pages` branch
- Github Actions is used to prevent invalid Service Directory entries to be published by validating the documents against a [JSON Schema](https://json-schema.org/) document.
- Github Pages is used to publish the Service Directory to the web

## Settings to change from default

[repository settings](https://github.com/datarightsprotocol/drp-service-directory/settings) to change from their defaults:

### General Settings 

- [X] Allow Merge Commits
- [X] Allow Squash Merging
- [ ] Allow Rebase Merging
- Change repository visibility to private -- github pages will still work, but the repo and history will only be available to collaborators.

### Branch Protection

Create a new branch protection rule so that `main` can only be touched via code review:

- branch: `main`
- [X] Require a pull request before merging
  - require approvals
- Require review from Code Owners 
- Require status checks to pass before merging

### Pages

The repo only contains the raw metadata files, not the amalgamated directories. The Directories are published via GitHub Actions

- Source: Deploy from a branch
- Branch: `gh-pages`
- Custom Domain: discovery.datarightsprotocol.org
- Enforce HTTPS (once DNS checks work)

Configure DNS with external provide:
discovery.datarightsprotocol.org CNAME consumer-reports-innovation-lab.github.io

## Change Control Procedures

To be defined, but in short

- AAs, PIPs, and self-service CBs will notify the DRP consortium of a delegate Github User which can be given [repository access](https://github.com/consumer-reports-innovation-lab/drp-service-directory/settings/access)
- configure [code owners](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners) document to ensure that PIPs are listed as owners of their delegated directory under businesses
- configure code owners so that authorized agents and self-service covered businesses own their own files
- Changes made to the directory must either be made directly by a code owner or reviewed/approved by them.
- Reviews must ensure
  - Resources being changed are in the scope of the user who is changing it (little reason for DRP consortium manager to be making bulk-level changes unless the schema of the directory changes, but eventually this will happen)
  - Schema checks pass
  - Contact information are valid
  - API endpoints work in OSIRAA(?)
