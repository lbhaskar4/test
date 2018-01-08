# Read me first!

This issue should be used to request that your MR be merged into an imminent RC as an exception.

Please read the ["Asking for an exception" docs](https://gitlab.com/gitlab-org/gitlab-ce/blob/master/PROCESS.md#asking-for-an-exception).

RELEASE_VERSION should include an RC as well, eg. 10.4.0.rc1, 10.4.0, 10.4.1.
MERGE_REQUEST_REFERENCE should include the project name, eg. gitlab-ce!123, gitlab-ee!321.

Any item inside of () should be removed before the issue is closed.
Please remove this notice once you read it.
------
# Exception request

(Use issue title in the format of:)
(YYYY-MM-DD: RELEASE_VERSION exception request for MERGE_REQUEST_REFERENCE)

Merge request to be considered for picking: gitlab-org/MERGE_REQUEST_REFERENCE

## Why it needs to be picked

(Explain why it is crucial that the MR is picked)

## Potential negative impact of picking

(Explain what could be go wrong with the release if this MR is picked)

## Sign-off

- [ ] Release manager: @[RELEASE_MANAGER_USERNAME]
- [ ] Engineering lead: @[ENGINEERING_LEAD_USERNAME]
- [ ] Engineering director: @[VP_OF_ENGINEERING_OR_CTO_USERNAME]