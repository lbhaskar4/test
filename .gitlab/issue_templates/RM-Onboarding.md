## On-Boarding

### Usernames

Make a note of your `GitLab.com`, `dev.gitlab.org` and `github` usernames and add them to this issue.

|                | Username |
|:---------------|:---------|
| Gitlab.com     |          |
| dev.gitlab.org |          |
| github.com     |          |

### Access request

- [ ] Master membership in the [gitlab-org/release/managers] group
- [ ] Master membership in the [gitlab/release/managers] group
- [ ] Membership in the [gitlabhq/release-managers] team on GitHub.
- [ ] Make sure you have VPN access (follow instructions from [creating client certificate](https://gitlab.com/gitlab-cookbooks/gitlab_openvpn#how-to-create-a-client-certificate)
      up to and including google authenticator setup), and test by bringing VPN up and sshing into staging sidekiq node (`sidekiq-asap-01.sv.stg.gitlab.com`)
- [ ] Use the [release manager infrastructure permissions template](https://gitlab.com/gitlab-org/release-tools/blob/master/doc/release-manager.md#infrastructure-permissions-template) to request chef and SSH access: [link to infrastructure issue]

[gitlab-org/release/managers]: https://gitlab.com/groups/gitlab-org/release/managers
[gitlab/release/managers]: https://dev.gitlab.org/groups/gitlab/release/managers
[gitlabhq/release-managers]: https://github.com/orgs/gitlabhq/teams/release-managers

### Tool setup

- [ ] Make sure you have [takeoff](https://gitlab.com/gitlab-org/takeoff) cloned locally, and [set it up](https://gitlab.com/gitlab-org/takeoff/#getting-started)
- [ ] Make sure you have [release-tools](https://gitlab.com/gitlab-org/release-tools) cloned locally, and [set it up](https://gitlab.com/gitlab-org/release-tools/blob/master/doc/rake-tasks.md#setup)
- [ ] If your ssh key has a passphrase, you will want to do `ssh-add` in your local takeoff repo
- [ ] Read through the [release guides](https://gitlab.com/gitlab-org/release-tools/blob/master/README.md#guides)

### First Tasks

- [ ] Join #releases on Slack, and introduce yourself
- [ ] Read the deploy docs: https://gitlab.com/gitlab-org/takeoff#deploying-gitlab
- [ ] Be involved in the merge/pick to stable for at least one RC/Patch
- [ ] Perform the ce-to-ee merge at least once for a RC/Patch
- [ ] Tag the release for at least one RC/patch
- [ ] Join a staging deploy call
- [ ] Join a gitlab.com deploy call
- [ ] Deploy to staging at least once
- [ ] Deploy to gitlab.com at least once

/label ~Onboarding
