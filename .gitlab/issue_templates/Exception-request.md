<!--
# Read me first

This issue should be used to request that your MR be merged into an imminent RC as an exception.

Please read the ["Asking for an exception" docs](https://gitlab.com/gitlab-org/gitlab-ce/blob/master/PROCESS.md#asking-for-an-exception).

Any item inside of () should be removed before the issue is closed.
-->

# Exception request

(Use issue title in the format of:)
(YYYY-MM-DD: RELEASE_VERSION exception request for MERGE_REQUEST_REFERENCE)
(RELEASE_VERSION - should include an RC as well, eg. 10.4.0.rc1, 10.4.0, 10.4.1.)
(MERGE_REQUEST_REFERENCE should include the project name, eg. gitlab-org/gitlab-ce!123, gitlab-org/gitlab-ee!321.
)

- Merge request to be considered for picking: MERGE_REQUEST_REFERENCE

## What it does

(Link to issue description or explain what the MR does and any background information)

## Why it needs to be picked

(Explain why it is crucial that the MR is picked.)
(What is the benefit?)
(What is the urgency?)
(What are alternatives?)

## Potential negative impact of picking

(Explain what could go wrong with the release if the MR is picked.)
(Include a description of the worst case scenario in case something breaks.)
(Include an estimate of the potential number of users affected by any negative impact.)
(Explain the steps you took to minimize the risk.)

## Sign-off

The following need to provide initial approval for this exception request:

- [ ] Release manager: @[RELEASE_MANAGER_USERNAME]
- [ ] Engineering team leader: @[ENGINEERING_LEAD_USERNAME]
- [ ] Engineering department leader (if different from team leader): @[ENGINEERING_DEPT_USERNAME]
- [ ] Quality leader: @[QUALITY_LEAD__USERNAME]

If you are the last person to provide initial approval, assign this issue to the
VPE for his approval:

- [ ] VPE: @edjdev

After the VPE approves, check that the following is accurate before closing this
issue:

- [ ] MERGE_REQUEST_REFERENCE has the correct milestone and
label set so that the release managers will pick it.
- [ ] MERGE_REQUEST_REFERENCE has a comment with a link to this issue:
    - Exception approved in ISSUE_LINK

/label ~"Exception request"
