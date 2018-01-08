# Read me first!

This issue should be used to describe your daily activity as a Release Manager.
For any action you took on the below described tasks, you should update the
description.
If you didn't take an action on a specific task, remove the placeholder items
and replace with N/A.

RELEASE_VERSION can be an RC as well, eg. 10.4.0.rc1, 10.4.0, 10.4.1.

Any item inside of () should be removed before the issue is closed.
Please remove this notice once you read it.
------

# Release manager daily tasks

(Use issue title in the format of:)
(YYYY-MM-DD: RELEASE_MANAGER_NAME RELEASE_VERSION release task)


## Tasks
### CE to EE merges

- [ ] Daily merge 1 assigned to EMEA_BASED_PERSON LINK_TO_MR
- [ ] Daily merge 2 assigned to AMERICA_OR_CALA_BASED_PERSON LINK_TO_MR

### Creating release

- [ ] RELEASE_VERSION LINK_TO_RELEASE_ISSUE

### QA

- [ ] QA task 1 assigned to PERSON LINK_TO_ISSUE
- [ ] QA task 2 assigned to PERSON LINK_TO_ISSUE
- [ ] QA task 2 assigned to PERSON LINK_TO_ISSUE

### Deployment

- [ ] Deploy RELEASE_VERSION to staging.gitlab.com (link optional)
- [ ] Deploy RELEASE_VERSION to canary.gitlab.com (link optional)
- [ ] Deploy RELEASE_VERSION to gitlab.com (link optional)


## Escalations
### CE to EE merges

(Write down any escalation paths you needed to take for any of the merges and why.)

### Creating release

(Write down any escalation paths you needed to take for any of release tasks and why.)
(Example: Specs on CE repository were not running/failing. Packages couldn't be built. and so on.)

### Deployment

(Write down any escalation paths you needed to take for deploy and why.)
(Eg. Production deploy was aborted so escalated to X, environment was not ready, etc.)

### QA

(Write down any escalation paths you needed to take for deploy and why.)
(Eg. QA task 1 was not completed in time so escalated to X.)

## Remarks
### CE to EE merges

(Write down any observations, blockers and challenges and possible improvements encountered during the merges.)
(Create the issue and link here. Link if issue exists already.)

### Creating release

(Write down any observations, blockers and challenges encountered during the release tasks.)
(Create the issue and link here. Link if issue exists already.)

### QA

(Write down any observations, blockers and challenges encountered during any of the QA tasks.)
(Create the issue and link here. Link if issue exists already.)

### Deployment

(Write down any observations, blockers and challenges encountered during any deploy.)
(Create the issue and link here. Link if issue exists already.)

## Used time
### CE to EE merge tasks

(Estimated time spent on merge tasks.)
(Include time spent on resolving conflicts by the RM as well as the assignee.)

### Release tasks

(Estimated time spent on release tasks.)
(Note down total time and time spent in waiting for tasks to complete.)

### QA

(Estimated time spent on release tasks.)
(Note down total time from the moment QA task could have been carried out until
QA was completed.)

## Deployment

(Estimated time spent on deploy tasks.)
(Start counting from the first time when you wanted to do deploy, until the deploy is complete for each environment.)
(Write down time from starting the deploy rake task until it finished.)

/label ~"Release task"
