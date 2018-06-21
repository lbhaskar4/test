<!--
# Read me first!

A Release Manager will create this issue once a Release Task for a monthly release has been created.
Set the issue title to: `RELEASE_MAJOR_VERSION FA task`

See how to fill in the Feature Assurance content under the [process](#process) section.

-->

# Feature Assurance

## Process

A Release manager will populate the [Feature Assurance](#feature-assurance) section. The information here should be copied over from the [kick off document](https://docs.google.com/document/d/1ElPkZ90A8ey_iOkTvUs_ByMlwKK6NAB2VOK5835wYK0/edit).

Each Product Manager then performs the Feature Assurance task to ensure that each feature being shipped is built correctly and fulfills the product requirement. More information on Feature Assurance is documented in the [Product handbook](https://about.gitlab.com/handbook/product/#feature-assurance).

1. List each features that need to be tested, with a link to the related issue.
1. Check off any feature that you've tested successfully.
  * The `RC QA` tasks is now  linked as a separate related issue to this `FA` task. Please use this to track the progress of your respective features against which Release Candidate it is included in.
1. If a problem is found: 
  * Check if there is already an Issue for it rased in the `RC QA` task.
    * If no issue was raised, create an issue for it and add a sub bullet item under the corresponding validation checklist task. Link the issue there.
  * Add the severity label as applicable to the issue.
  * Raise the problem in the discussion and tag relevant Engineers and Engineering managers. 
1. Raise any release blockers to the Release Manager and to the Engineering Manager whose team is responsible for delivering the feature.

General Quality info can be found in the [Quality Handbook](https://about.gitlab.com/handbook/quality/).

## Deadline

* The deadline to which the Feature Assurance task is closed out is on the 20th of each month.
  * This is scheduled 2 days before the release day and publishing the release blog post.

## Feature Assurance

Create one section for each team and the corresponding Product Manager. 

> Example:
>
> 1. [x] Awesome new feature: https://gitlab.com/gitlab-org/gitlab-ce/issues/...
> 2. [x] Another cool feature: https://gitlab.com/gitlab-org/gitlab-ce/issues/...
>   - [ ] Found critical issue: https://gitlab.com/gitlab-org/gitlab-ce/issues/...
>   - [ ] Found minor issue, issue was already raise as part of RC2: https://gitlab.com/gitlab-org/gitlab-ce/issues/...
> 3. [ ] This is a EE feature: https://gitlab.com/gitlab-org/gitlab-ee/issues/...

### PM handle / Team name

* [ ] FEATURE_1: https://gitlab.com/gitlab-org/gitlab-ce/issues/...
* [ ] FEATURE_2: https://gitlab.com/gitlab-org/gitlab-ee/issues/...

/cc @gl-product

/label ~"FA task"
