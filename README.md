# Azure DevOps Pipeline Sample 

This repo was created to explore Azure Pipelines and CI/CD patterns.
 
Create a new Azure DevOps pipeline and select a new empty GitHub repo. 

Azure DevOps adds a sample `\azure-pipelines.yml` file to the repo root and names the new pipeline `{$GitHubAccountName}.{$RepoName}` in the Azure DevOps web portal.

```
trigger:
- master

pool:
  vmImage: 'ubuntu-latest'

steps:
- script: echo Hello, world!
  displayName: 'Run a one-line script'

- script: |
    echo Add other tasks to build, test, and deploy your project.
    echo See https://aka.ms/yaml
  displayName: 'Run a multi-line script'
  ```

The sample pipeline will be triggered on any push or merge to the `master` branch. Changes to other branches do not trigger the pipeline but the pipeline can be run manually for any branch using the Azure DevOps web portal.

> Note: All pull requests **for all branches** will also trigger the pipeline unless a `-pr` section is added to the `.yml` file with an include/exclude pattern.
