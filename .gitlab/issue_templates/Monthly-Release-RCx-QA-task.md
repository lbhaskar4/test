<!--
# Read me first!

A Release Manager will create this issue once an RC# staging deploy is completed.
Set the issue title to: `RELEASE_MAJOR_VERSION RC# QA task`

The [deadline](#deadline) is the time given before a release candidate moves on after deploying to staging.
See [deadline](#deadline) section for details.

A Quality Engineer will assist in populating the [Merge Requests tested](#merge-requests-tested) section to include owners of each Merge Requests so they can delegate testing.
This is done from the [Release Tools](https://gitlab.com/gitlab-org/release-tools) project. This has to be setup before using the script.
* Directions on generating the QA task content for a given change are posted here: https://gitlab.com/gitlab-org/release/docs/blob/master/general/qa-issue-generation.md

As a backup, we can also fall back to use the `git` log command for this, but you will need to mention the maintainers explicitly in a comment until there is an automated tool for this. ```git log PREVIOUS_TAG-ee..LATEST_TAG-ee --pretty=format:"- [ ] [%h](https://gitlab.com/gitlab-org/gitlab-ee/commit/%h) @%aN \`%s\`"```

A Quality Engineer will assist in running the [Automated QA](#automated-qa).
-->

# Release Candidate QA Task

## Process

A Release manager with the help of a Quality engineer will populate the [Merge Requests tested](#merge-requests-tested) section. The information is taken from our Automated QA task generation script. The documentation can be found at: https://gitlab.com/gitlab-org/release/docs/blob/master/general/qa-issue-generation.md

Each engineer then validates and checks off each of their assigned QA task(s).
1. Check off each Merge Request changes that you've tested successfully and note any issues you've created and check them off as they are resolved.
1. If a problem is found:
  * Create an issue for it and add a sub bullet item under the corresponding validation checklist task. Link the issue there.
  * Add the severity label
  * Raise the problem in the discussion and tag relevant Engineering and Product managers.
1. If a regression is found:
  * Create an issue for it
  * Add the severity label and the regression label
  * Raise the regression in the discussion and tag relevant Engineering and Product managers.

General Quality info can be found in the [Quality Handbook](https://about.gitlab.com/handbook/quality/).

## Deadline

* The deadline to which the first release candidate (RC1) moves on from staging environment is **24** hours after the deploy to staging completes.
* The deadline to which subsequent release candidates moves on from staging environment is **12** hours after the deploy to staging completes.

> **Note:** For Release Managers, for each release candidate, update the time here to reflect the latest release candidate deploy.

QA testing on [staging.gitlab.com](https://staging.gitlab.com) should be completed by **YYYY-MM-DD HH:MM UTC**.
After this deadline has passed, Release Managers will proceed with the canary and production deployment.

## Merge Requests tested in RC(#)

> Example:
>
> * [x] `@Engineer1` | Apply notification settings level of bacons to all child bacons ~Discussion ~groups ~subgroups
> * [x] `@Engineer2` | Resolve "Timeout searching group bacons" ~Discussion ~backend ~bug ~database ~groups ~issues ~performance
> * [ ] `@Engineer3` | Nonnegative meatball weights in issuable sidebar short ribs ~Deliverable ~Discussion ~backend ~direction ~frontend ~issues
>   * Found problem, does not work because... [LINK_ISSUE_HERE](https://gitlab.com/gitlab-org/gitlab-ce/issues/)
> * [ ] `@Engineer4` | Moving rev-list pastrami bacons to Lfs Prosciutto ~Platform ~backend ~lfs

## Automated QA

> **Note:** For Quality Engineers, run Gitlab QA on staging and post the results.

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
