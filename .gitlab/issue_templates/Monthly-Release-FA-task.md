<!--
# Read me first!

A Release Manager will create this issue once a Release Task for a monthly release has been created.
Set the issue title to: `RELEASE_MAJOR_VERSION FA task`

A Release Manager will fill out the ["Feature assurance" list](#feature-assurance) and the responsible Product Manager.

-->

# Feature Assurance

## Process

A Release manager will populate the [Feature Assurance](#feature-assurance) section. The information here should be copied over from the [kick off document](https://docs.google.com/document/d/1ElPkZ90A8ey_iOkTvUs_ByMlwKK6NAB2VOK5835wYK0/edit).

Each Product Manager then performs the Feature Assurance task to ensure that each feature being shipped in a given is built correctly and fulfills the product requirement.
1. List each features that need to be tested, with a link to the related issue.
1. Check off any feature that you've tested successfully.
1. If a problem is found, update the item adding the link to the related issue, and the severity of it.
1. Check them off as they are resolved.
1. Raise any blockers to the Release Manager and to the Engineering Manager whose team is responsible for delivering the feature.

## Deadline

* The deadline to which the Feature Assurance task is closed out is on the 22rd of each month on release day.
* This should be closed out prior to the release blog post is published.

## Feature Assurance

Create one section for each team and the PM doing the test. 

> Example:
>
> 1. [x] Awesome new feature: https://gitlab.com/gitlab-org/gitlab-ce/issues/...
> 2. [x] Another cool feature: https://gitlab.com/gitlab-org/gitlab-ce/issues/...
>   - [ ] Found critical issue: https://gitlab.com/gitlab-org/gitlab-ce/issues/...
>   - [ ] Found minor issue: https://gitlab.com/gitlab-org/gitlab-ce/issues/...
> 3. [ ] This is a EE feature: https://gitlab.com/gitlab-org/gitlab-ee/issues/...

### PM handle - Team name

* [ ] Feature 1: Issue https://gitlab.com/gitlab-org/gitlab-ce/issues/...
* [ ] Feature 2: Issue https://gitlab.com/gitlab-org/gitlab-ce/issues/...
