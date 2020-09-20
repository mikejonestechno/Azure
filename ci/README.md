# Continuous Integration

> **Continuous Integration** is the practice of merging all developers' working copies to a shared mainline several times a day.

*Fowler, Martin (1 May 2006). "[Continuous Integration](https://martinfowler.com/articles/continuousIntegration.html)". Retrieved 9 January 2014.*


## Pipeline Status Checks

When code is pushed or PR merged Git does not wait for any pipelines or other tests to complete. The default settings only perform merge conflict checks.

This means code will be integrated even if an associated Azure pipeline trigger fails to start or fails to successfully complete for any reason.

A Git branch protection rule can help ensure only *working* or releasable code is pushed to the shared mainline.

The setting "Require status checks to pass before merging" will ensure any associated pipeline trigger completes successfully before the code is merged.

An additional setting "Require branches to be up to date before merging" will ensure merges are up to date (zero commits behind) the target branch. This can help false positives checking a branch that is out of date. 

![Git branch protection status check settings](git-pipeline-status-check.png)


---
To be reviewed...

## Pull Requests

A pull request that triggers an Azure pipeline does not block the merge request or wait until the pipeline is successfully completed. 

An active pull request can be completed and code merged to mainline in the few seconds before the pipeline is triggered, or while the pipeline is running, or even if the pipeline fails.



