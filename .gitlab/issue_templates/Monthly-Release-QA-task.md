<!--
# Read me first!

A Release Manager will create this issue once an RC1 staging deploy is completed.
Set the issue title to: `YYYY-MM-DD: RELEASE_MAJOR_VERSION RC# QA task`

PMs will then take ownership of the process by filling out the
["Features tested" list](#features-assurance) and assigning themselves.

The [deadline](#deadline) to which a release candidate moves on from staging environment is set to **24** hours after the completion of the deploy.

Updating the issue with subsequent RCs: this issue is to be updated whenever a new release candidate has been deployed.

A Quality Engineer will assist in updating the ["Bugs & Changes tested" task list](#bugs-changes-tested to mention the maintainers responsible for each commit since the last release so they can delegate testing.

You can use the following oneliner to get started, but you will need to mention the maintainers manually until there is a tool for this. ```git log PREVIOUS_TAG-ee..LATEST_TAG-ee --pretty=format:"- [ ] [%h](https://gitlab.com/gitlab-org/gitlab-ee/commit/%h) @%aN \`%s\`"```

A Quality Engineer will assist in running the [Automated QA](#automated-qa)
-->

## Deadline

> **Note:** For Release Managers, for every new release candidates, update the time here to reflect the latest deploy. 

QA testing on [staging.gitlab.com](https://staging.gitlab.com) should be completed by **YYYY-MM-DD HH:MM UTC**.
After this deadline has passed, Release Managers will proceed with the production deployment.

## Tasks

General Quality info can be found at the [Quality Handbook](https://about.gitlab.com/handbook/quality/).

You can use the [QA Checklist](https://gitlab.com/gitlab-org/release/docs/blob/master/general/qa-checklist.md)
to ensure you've tested critical features.

1. List features that need to be tested, with a link to the related issue.
1. Check off any feature you've tested successfully.
1. If a problem is found, update the item adding the link to the related issue, and the severity of it
1. Check them off as they are resolved

Example:

> 1. [x] Awesome new feature: https://gitlab.com/gitlab-org/gitlab-ce/issues/...
> 2. [x] Another cool feature: https://gitlab.com/gitlab-org/gitlab-ce/issues/...
>   - [ ] Found critical issue: https://gitlab.com/gitlab-org/gitlab-ce/issues/...
>   - [ ] Found minor issue: https://gitlab.com/gitlab-org/gitlab-ce/issues/...
> 3. [ ] This is a EE feature: https://gitlab.com/gitlab-org/gitlab-ee/issues/...

### Feature Assurance

Create one section for each team and the PM doing the test. The information here should be copied over from the [kick off document](https://docs.google.com/document/d/1ElPkZ90A8ey_iOkTvUs_ByMlwKK6NAB2VOK5835wYK0/edit))

#### PM handle - Team name

* [ ] Feature: Issue 


### Bugs & Changes tested 

Check off any features you've tested successfully and note any issues you've created and check them off as they are resolved.

If there are regressions please raise them in the discussion and add an entry for it to be validated in the latest RC.

#### RC1
- [ ] Feature update ISSUE_1
- [ ] Opened Regression ISSUE_2

#### RC#
- [ ] Bug fix ISSUE_3
- [ ] Opened Release Blocking Regression ISSUE_4

> Create a new section for each new release candidate, update the section with changes in the release and update the RC# in the issue description

## Automated QA

> **Note:** For Quality Engineers, for every release versions run Gitlab QA on staging and post the results. 

Please post the results of the [gitlab-qa](https://gitlab.com/gitlab-org/gitlab-qa) automated QA test below

The credentials are in 1password, look for `GitLab QA`

Run

```sh
GITLAB_USERNAME=your_username GITLAB_PASSWORD=your_password gitlab-qa Test::Instance::Any EE latest https://staging.gitlab.com
```

### Automated QA Result RC1 
```sh
Post the result of the test run here
```

### Automated QA Result RC# 

> Create a new section for each new release candidate, update the section with changes in the release and update the RC# in the issue description

```sh
Post the result of the test run here
```

/cc @gl-product

/label "QA task"
