# Read me first!

This issue should be used to coordinate QA tasks on staging.gitlab.com.
For any action you took on the below described tasks, you should update the
description.
If you didn't take an action on a specific task, remove the placeholder items
and replace with N/A.
If you are unable to do a task yourself, find someone who can.

Any tasks that are not completed within 24 hours from the creation of this issue,
will put a feature or a change in the codebase at risk of a revert in case
something goes wrong!

Release manager will create this issue once the staging deploy is completed
and ping the whole Product team.
The product team should fill out the "Features tested" lists
and assign them to members of the Product team.

RELEASE_VERSION can be an RC as well, eg. 10.4.0.rc1, 10.4.0, 10.4.1.

Use issue title in the format of:
YYYY-MM-DD: RELEASE_VERSION QA task

Any item inside of () should be removed before the issue is closed.
Please remove this notice once you read it.
------

## Tasks

General Quality info can be found at the [Quality Handbook](https://about.gitlab.com/handbook/quality/).

You can use the [QA Checklist](https://gitlab.com/gitlab-org/release-tools/blob/master/doc/qa-checklist.md)
to ensure you've tested critical features.

(For each Product Manager, add a separate section. Product
Managers should fill in the details of the tests they conducted and any issues
they've created relating to testing e.g. bugs or regressions.)

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