<!--
# Read me first!

A Release Manager will create this issue once a staging deploy is completed.

A Release Manager should create the ["Changes tested" task list](#changes-tested) to mention the maintainers responsible for each commit since the last release so they can delegate testing.

You can use the following oneliner to get started, but you will need to mention the maintainers manually until there is a tool for this. ```git log PREVIOUS_TAG-ee..LATEST_TAG-ee --pretty=format:"- [ ] [%h](https://gitlab.com/gitlab-org/gitlab-ee/commit/%h) @%aN \`%s\`"```

The [deadline](#deadline) should be set to **12** hours after the completion of the deploy.

`RELEASE_VERSION` eg. `10.3.2`, `10.4.1`.

Set the issue title to: `YYYY-MM-DD: RELEASE_VERSION QA task`

If this is a security release add the word "Security"  before `RELEASE_VERSION`. `YYYY-MM-DD: Security RELEASE_VERSION QA task`

**Set the issue as confidential if this is a security release**
-->

## Deadline

* The deadline to which the release moves on from staging environment is **12** hours after the completion each deploy to staging.
* The deadline to which the QA Task is closed out is **24** hours (1 working day) after the deploy to production.

QA testing on staging.gitlab.com should be completed by **YYYY-MM-DD HH:MM UTC**.
After this deadline has passed, Release Managers will proceed with the production deployment.

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

## Automated QA

> **Note:** For Quality Engineers, for every release versions run Gitlab QA on staging and post the results.

- [ ] Make sure to export the following environment variables (you can find the
  password and tokens under the `GitLab QA` and `GitLab QA - Access tokens` 1Password items)

  ```
  › export GITLAB_USERNAME=gitlab-qa GITLAB_PASSWORD=xxx GITHUB_ACCESS_TOKEN=xxx
  ```

- [ ] Update `gitlab-qa` if needed

  ```
  › gem install gitlab-qa
  ```
- [ ] Automated QA completed. QA can be parallelized manually (for now):

  ```
  # Tab 1: This should take approximately 4.5 minutes
  # Make sure to replace `11.1.0-rc4-ee` with the version exposed at http://staging.gitlab.com/help

  › gitlab-qa Test::Instance::Any gitlab-qa Test::Instance::Any dev.gitlab.org:5005/gitlab/omnibus-gitlab/gitlab-ee:11.1.0-rc4-ee https://staging.gitlab.com -- qa/specs/features/api/ qa/specs/features/login/ qa/specs/features/merge_request/
  ```

  ```
  # Tab 2: This should take approximately 6 minutes
  # Make sure to replace `11.1.0-rc4-ee` with the version exposed at http://staging.gitlab.com/help

  › gitlab-qa Test::Instance::Any dev.gitlab.org:5005/gitlab/omnibus-gitlab/gitlab-ee:11.1.0-rc4-ee https://staging.gitlab.com -- qa/specs/features/project/
  ```

  ```
  # Tab 3: This should take approximately 5 minutes
  # Make sure to replace `11.1.0-rc4-ee` with the version exposed at http://staging.gitlab.com/help

  › gitlab-qa Test::Instance::Any dev.gitlab.org:5005/gitlab/omnibus-gitlab/gitlab-ee:11.1.0-rc4-ee https://staging.gitlab.com -- qa/specs/features/repository/
  ```
- [ ] Post results and failures logs + screenshots as comments of this issue
- [ ] Create `Automation Triage RELEASE_MAJOR_VERSION RC#` issues for all the
  automated QA failures and link it to this issue

/label ~"QA task"
