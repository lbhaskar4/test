# Read me first!

An RM will create this issue once an RC1 staging deploy is completed.
PMs will then take ownership of the process by filling out the
["Features tested" list](#features-tested) and assigning themselves.

The [deadline](#deadline) should be set to **24** hours after the completion of the deploy.

Set the issue title to: `YYYY-MM-DD: RELEASE_MAJOR_VERSION.rc1 QA task`

Please remove this notice before posting.

------

## Deadline

QA testing on staging.gitlab.com should be completed by **YYYY-MM-DD HH:MM UTC**.
After this deadline has passed, RMs will proceed with the production deployment.

## Tasks

General Quality info can be found at the [Quality Handbook](https://about.gitlab.com/handbook/quality/).

You can use the [QA Checklist](https://gitlab.com/gitlab-org/release-tools/blob/master/doc/qa-checklist.md)
to ensure you've tested critical features.

> For each PM, add a separate section. PMs should fill in the details of the
tests they conducted and any issues they've created relating to testing e.g. bugs or regressions.

### Features tested

Check off any features you've tested successfully.

#### PM_NAME PM_TEAM

- [ ] Tested FEATURE_1
- [ ] Tested FEATURE_2

### Issues raised

Take note of any issues you've created and check them off as they are resolved.

#### PM_NAME PM_TEAM

- [ ] Found ISSUE_1
- [ ] Opened ISSUE_2


### Automated QA

> Please link to a snippet of the results of the [gitlab-qa](https://gitlab.com/gitlab-org/gitlab-qa) automated QA test

/cc @gl-product

/label "QA task"