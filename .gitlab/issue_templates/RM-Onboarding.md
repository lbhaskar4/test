## On-Boarding

Trainee: `your_username`
Release Manager: Previous Release Manager in your timezone. See https://about.gitlab.com/release-managers/ for details

- [ ] Trainee: Assign yourself and the Release Manager to this issue.

### Usernames

Trainee: Make a note of your `GitLab.com`, `dev.gitlab.org` and `github` usernames and add them to this issue.

|                | Username |
|:---------------|:---------|
| Gitlab.com     |          |
| dev.gitlab.org |          |
| github.com     |          |

### Access request

- Release Manager: Ensure trainee has Master Access to:
  - [ ] gitlab-ce, for both dev.gitlab and gitlab.com
  - [ ] gitlab-ee, for both dev.gitlab and gitlab.com
  - [ ] gitlab-omnibus, for both dev.gitlab and gitlab.com

- [ ] Release Manager: Ensure trainee gets added to the [Release Managers team](https://github.com/orgs/gitlabhq/teams/release-managers) on GitHub, either by adding it yourself if you have enough permissions, or asking a [GitHub Maintainer](https://github.com/orgs/gitlabhq/teams/release-managers/members?utf8=%E2%9C%93&query=+role%3Amaintainer) to do it.

- [ ] Trainee: Create a [new infrastructure permissions issue](https://gitlab.com/gitlab-com/infrastructure/issues/new?issue%5Btitle%5D=Chef%20and%20SSH%20access%20request%20for%20YOUR%20NAME) using the template below as a description. Make sure to set the issue to **confidential** and include your SSH username and public key. Once you finished, replace the following with your issue link: `<INFRASTRUCTURE_ISSUE_LINK>`

```
## What

- [ ] Access to the VPN
- [ ] SSH access for release manager
- [ ] Access to chef-server
- [ ] Added to the `release-manager` group in Cog in `#production` so you can tweet and broadcast messages.
  - A Cog admin in `#production` can run `!group-member-add release-manager <your handle>`, or you could be [manually added to Marvin](https://gitlab.com/gitlab-com/runbooks/blob/master/howto/manage-cog.md#add-a-user)

## Why

I'll be a trainee release manager in TRAINEE_RELEASE and release manager in RELEASE_YOU_WILL_MANAGE.

Onboarding task: LINK_TO_ONBOARING_ISSUE

## SSH Details

### Username

\```
YOUR_SSH_USER_NAME
\```

### Public Key

\```
YOUR_PUBLIC_KEY
\```

```

### Tool setup

Trainee: Ensure you have completed all the steps on `Access Request` before doing this section.

- [ ] Trainee: Follow instructions from [Create a client certificate](https://gitlab.com/gitlab-cookbooks/gitlab_openvpn#create-a-client-certificate), and test by bringing VPN up and sshing into staging sidekiq node (`sidekiq-asap-01.sv.stg.gitlab.com`)
- [ ] Trainee: Make sure you have [takeoff](https://gitlab.com/gitlab-org/takeoff) cloned locally, and [set it up](https://gitlab.com/gitlab-org/takeoff/#getting-started)
- [ ] Trainee: Make sure you have [release-tools](https://gitlab.com/gitlab-org/release-tools) cloned locally, and [set it up](https://gitlab.com/gitlab-org/release-tools/blob/master/doc/rake-tasks.md#setup)
- [ ] Trainee: If your ssh key has a passphrase, you will want to do `ssh-add` in your local takeoff repo

### First Tasks

- [ ] Trainee: Join #releases on Slack
- [ ] Trainee: Read through the [release guides](https://gitlab.com/gitlab-org/release/docs/blob/master/README.md)
- [ ] Trainee: Read the deploy [docs](https://gitlab.com/gitlab-org/takeoff#deploying-gitlab)
- [ ] Trainee: Be involved in the merge/pick to stable for at least one RC/Patch
- [ ] Trainee: Perform the ce-to-ee merge at least once for a RC/Patch
- [ ] Trainee: Tag the release for at least one RC/patch
- [ ] Trainee: Join a staging deploy call
- [ ] Trainee: Join a gitlab.com deploy call
- [ ] Trainee: Deploy to staging at least once
- [ ] Trainee: Deploy to gitlab.com at least once

/label ~Onboarding
