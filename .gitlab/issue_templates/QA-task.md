# Read me first!

An RM will create this issue once a staging deploy is completed,
please use the "RC1 QA Task" template if the deployed version was the first release candidate of
a new major version.

An RM should create the ["Changes tested" task list](#changes-tested) to mention the maintainers responsible for each commit since the last release so they can delegate testing.

You can use the following oneliner to get started, but you will need to mention the maintainers manually until there is a tool for this. ```git log PREVIOUS_TAG-ee..LATEST_TAG-ee --pretty=format:"- [ ] [%h](https://gitlab.com/gitlab-org/gitlab-ee/commit/%h) @%aN \`%s\`"```

The [deadline](#deadline) should be set to **12** hours after the completion of the deploy.

`RELEASE_VERSION` can be an RC as well. eg. `10.4.0.rc1`, `10.4.0`, `10.4.1`.

Set the issue title to: `YYYY-MM-DD: RELEASE_VERSION QA task`

**Set the issue as confidential if this is a security release**

Please remove this notice before posting.

------

## Deadline

QA testing on staging.gitlab.com should be completed by **YYYY-MM-DD HH:MM UTC**.
After this deadline has passed, RMs will proceed with the production deployment.

## Tasks

General Quality info can be found at the [Quality Handbook](https://about.gitlab.com/handbook/quality/).

You can use the [QA Checklist](https://gitlab.com/gitlab-org/release/docs/blob/master/general/qa-checklist.md)
to ensure you've tested critical features.

> For each PM, add a separate section. PMs should fill in the details of the
tests they conducted and any issues they've created relating to testing e.g. bugs or regressions.

### Changes tested

Check off any features you've tested successfully.

- [ ] [COMMIT_SHORT_SHA](LINK_TO_COMMIT) @MAINTAINER_USERNAME `COMMIT_MESSAGE`

### Issues raised

Take note of any issues you've created and check them off as they are resolved.

- [ ] Found ISSUE_1
- [ ] Opened ISSUE_2

### Automated QA

> Please link to a snippet of the results of the [gitlab-qa](https://gitlab.com/gitlab-org/gitlab-qa) automated QA test

/label "QA task"
