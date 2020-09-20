# Continuous Integration with Git / GitHub

> **Continuous Integration** is the practice of merging all developers' working copies to a shared mainline several times a day.

*Fowler, Martin (1 May 2006). "[Continuous Integration](https://martinfowler.com/articles/continuousIntegration.html)". Retrieved 9 January 2014.*

## Implementing CI with Git 

The default Git settings only perform merge conflict checks.

Code can be pushed or PR merged to a branch even if it contains defects, fails to build or compile, or fails to pass unit tests or any other checks.

This can result in breaking, untested code getting pushed in to the shared mainline. This can then subsequently result in developers pushing further broken code on top of code that is already broken.

Not good. 

## Git Branch Protection Rules

Git branch protection rules can help ensure only *working* or releasable code is pushed to the shared mainline.

There are two settings to consider that are described in more detail below:

- Require status checks to pass before merging
- Require branches to be up to date before merging

Screenshot:

![Git branch protection status check settings](git-pipeline-status-check.png)

### Require Status Checks To Pass

The 'require status checks to pass' setting can be used to protect the shared mainline branch and only allow code to be merged in from branches containing working code (where the status checks have already passed).

> **Pull Requests**
>
> Status checks will prevent commits being directly pushed to the protected branch. Status checks will require code to be merged from a working branch using a pull request. There are practices that can reduce the additional overhead discussed later in this article.

The status checks will prevent pull requests being completed untills all the required checks have passed.

If the branch has associated Azure pipelines, the pipelines must be completed successfully to pass the check.

> Automated tests are not required, as long as the pipeline completes successfully. However if the pipeline includes automated tests, any failing tests should cause a failed pipeline status and subsequently fail the Git status check.  

Screenshot:

![Git branch protection status check settings](git-pr-pipeline-status-check.png)

> **Include Administrators**
> 
> Ensure the 'Include administrators' setting is also enabled otherwise pull requests created by Git repo administrators will be automatically merged without running any checks (the checks are ignored and skipped). If left disabled Git repo administrators will also be able to directly push changes to the protected branch. (Of course if you have awesome repo admins that will NEVER introduce breaking changes you could leave the 'Include administrators' setting disabled.) 

### Require status checks to pass before merging

The 'Require status checks to pass before merging' setting will ensure any associated pipeline trigger completes successfully before the code is merged.

An additional setting "Require branches to be up to date before merging" will ensure merges are up to date (zero commits behind) the target branch. This can help false positives checking a branch that is out of date. 


### Additional Notes

> Pair programming and mob programming techniques could be evaluated with continuous integration practices, where the continuous integration of two developers' code occurs in the converstation *before* the code is actually written. Further debate of pair and mob programming is outside the scope of this article. For the purpose of this article it is assumed that some level of branch protection will benefit the team. 

---
To be reviewed...

## Pull Requests

A pull request that triggers an Azure pipeline does not block the merge request or wait until the pipeline is successfully completed. 

An active pull request can be completed and code merged to mainline in the few seconds before the pipeline is triggered, or while the pipeline is running, or even if the pipeline fails.



