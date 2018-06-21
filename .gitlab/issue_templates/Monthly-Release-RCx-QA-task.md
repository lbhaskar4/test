<!--
# Read me first!

A Release Manager will create this issue once an RC# staging deploy is completed.
Set the issue title to: `RELEASE_MAJOR_VERSION RC# QA task`

The [deadline](#deadline) is the time given before a release candidate moves on after deploying to staging.
* For the 1st Release Candidate: 24 hours.
* For subsequent Release Candidates: 12 hours.

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

Please post the results of the [gitlab-qa](https://gitlab.com/gitlab-org/gitlab-qa) automated QA tests below.

The credentials are in 1Password, look for `GitLab QA`.
You'll also need to generate a personal access token for the `GitLab QA` user and
save it in the `GITLAB_QA_ACCESS_TOKEN` environment variable below.

Export the following environment variables

```sh
export GITLAB_USERNAME=gitlab-qa GITLAB_PASSWORD=xxx GITLAB_QA_ACCESS_TOKEN=xxx
```

and run

```sh
gitlab-qa Test::Instance::Staging
```

**Note:** Until https://gitlab.com/gitlab-org/gitlab-qa/issues/272 is resolved, you'll need to use the workaround described at https://gitlab.com/gitlab-org/gitlab-qa/issues/272#workaround. The workaround doesn't need a `GITLAB_QA_ACCESS_TOKEN` variable 

```
# Make sure to replace `v11.0.0-rc8-ee` with the version exposed at http://staging.gitlab.com/help
# In gitlab-ee
› git checkout v11.0.0-rc8-ee
› cd qa
› docker build -t gitlab/gitlab-ee-qa:11.0.0-rc8-ee .
› gitlab-qa Test::Instance::Any gitlab/gitlab-ee:11.0.0-rc8-ee 11.0.0-rc8-ee https://staging.gitlab.com
```

```sh
Post the result of the test run here.
```

If there are errors, create an "Automation Triage" issue, name it `Automation Triage RELEASE_MAJOR_VERSION RC#` and link it to this issue. 
In the triage issue include all the detailed test logs and screenshots.

/label ~"QA task"
