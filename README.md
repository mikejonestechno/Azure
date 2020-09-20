# Azure
I plan to use this repo to explore use of Azure Pipelines with Terraform.

I created a new Azure DevOps pipeline and selected a new empty GitHub repo. 

Azure DevOps added a sample `\azure-pipelines.yml` and named the new pipeline `{$GitHubAccountName}.{$RepoName}` in the Azure DevOps web portal.

The sample pipeline is triggered on any push or merge to the `master` branch. Changes to other branches do not trigger the pipeline but the pipeline can be run manually using the Azure DevOps web portal.

By default all pull requests **for all branches** will also trigger the pipeline unless a `-pr` section is added to the `.yml` file with an include/exclude pattern.