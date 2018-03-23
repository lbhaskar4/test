## General Process for Release Managers

This issue serves as one place to find all information needed for the
release on the 22nd. This issue should be used to link related issues
associated with the release such as individual Release Candidate issues
and exception requests.

### Tasks

- [ ] Create the `Pick into X.X` group label if it doesn't exist: https://gitlab.com/groups/gitlab-org/labels/new
  * Note: Replace `X.X` with the version you are working on.
- [ ] Create a new issue for the preparation of each release candidate

## Individual Release Candidate preparation issues

Issues relating to the preparation of a Release Candidate should be created
separately and linked in this issue.

Release Candidate issues should be created using `release-tools`:

```
bundle exec rake patch_issue[10.5.0-rc1]
```

## Exception requests

Exception requests relate to proposals for changes to the normal release process.

Exception requests should be created by using the
[exception request issue template](.gitlab/issue_templates/Exception-request.md)
and linked here for posterity.
