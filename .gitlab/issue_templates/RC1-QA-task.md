<!--
# Read me first!

An RM will create this issue once an RC1 staging deploy is completed.
PMs will then take ownership of the process by filling out the
["Features tested" list](#features-tested) and assigning themselves.

The [deadline](#deadline) should be set to **24** hours after the completion of the deploy.

Set the issue title to: `YYYY-MM-DD: RELEASE_MAJOR_VERSION.rc1 QA task`
-->

## Deadline

QA testing on [staging.gitlab.com](https://staging.gitlab.com) should be completed by **YYYY-MM-DD HH:MM UTC**.
After this deadline has passed, RMs will proceed with the production deployment.

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

### Tested Features

Create one section for each team and the PM doing the test.

#### PM handle - Team name

1. [ ] feature: issue

### Automated QA

> Please link to a snippet of the results of the [gitlab-qa](https://gitlab.com/gitlab-org/gitlab-qa) automated QA test

Run

```sh
GITLAB_USERNAME=your_username GITLAB_PASSWORD=your_password gitlab-qa Test::Instance::Any EE latest https://staging.gitlab.com
```

The credentials are in 1password, look for `GitLab QA`

- [ ] [QA Result](LINK_TO_SNIPPET)

/cc @gl-product

/label "QA task"
