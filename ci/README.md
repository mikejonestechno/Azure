# Continuous Integration

> **Continuous Integration** is the practice of merging all developers' working copies to a shared mainline several times a day.

*Fowler, Martin (1 May 2006). "[Continuous Integration](https://martinfowler.com/articles/continuousIntegration.html)". Retrieved 9 January 2014.*

## Git Continuous Integration

The default Git settings only perform merge conflict checks. 

When code is pushed or PR merged Git will automatically integrate the commits and then (if there are no merge conflicts) trigger any integration or webhooks.

This can result in breaking, untested code getting pushed in to the shared mainline, subsequently resulting in developers pushing further broken code on top of code that is already broken.

Not good.

## Git Branch Protection Rules

Git branch protection rules can help ensure only *working* or releasable code is pushed to the shared mainline.

There are two settings to consider:

- Require status checks to pass before merging
- Require branches to be up to date before merging

## Require Status Checks To Pass

When code is pushed or PR merged Git will automatically integrate the commits (if there are no merge conflicts). 

The 'require status checks to pass' setting can be used to lock the shared mainlin branch and only permit code merges from separate branches where the status checks have passed. 

> This setting prevents commits being directly pushed to the protected branch. 

The setting "Require status checks to pass before merging" will ensure any associated pipeline trigger completes successfully before the code is merged.

An additional setting "Require branches to be up to date before merging" will ensure merges are up to date (zero commits behind) the target branch. This can help false positives checking a branch that is out of date. 

![Git branch protection status check settings](git-pipeline-status-check.png)


---
To be reviewed...

## Pull Requests

A pull request that triggers an Azure pipeline does not block the merge request or wait until the pipeline is successfully completed. 

An active pull request can be completed and code merged to mainline in the few seconds before the pipeline is triggered, or while the pipeline is running, or even if the pipeline fails.



