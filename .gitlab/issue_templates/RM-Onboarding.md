## On-Boarding

Trainee: `your_username`
Release Manager: Release Manager in your timezone. See https://about.gitlab.com/release-managers/ for details

- [ ] Trainee: Assign yourself and the Release Manager to this issue.

### Usernames

Trainee: Make a note of your `GitLab.com` and `dev.gitlab.org` usernames and add them to this issue.

|                | Username |
|:---------------|:---------|
| gitlab.com     |          |
| dev.gitlab.org |          |

### Access request

- [ ] Trainee: Add your information to the [`config/release_managers.yml`](https://gitlab.com/gitlab-org/release-tools/blob/master/config/release_managers.yml)
  file in release-tools and open a merge request, linking to this issue.
- [ ] Trainee: Create a [new infrastructure permissions issue](https://gitlab.com/gitlab-com/infrastructure/issues/new?issue%5Btitle%5D=Chef%20and%20SSH%20access%20request%20for%20YOUR%20NAME) using the template below as a description. Make sure to set the issue to **confidential** and include your SSH username and public key. Once you finished, replace the following with your issue link: `<INFRASTRUCTURE_ISSUE_LINK>`
- [ ] Trainee: make sure you can log in to `ops.gitlab.net`. After log in, please change your username to be the same as it is on gitlab.com

```
## What

- [ ] SSH access for release manager
- [ ] Access to chef-server
- [ ] Added to the `release-manager` group in Cog in `#production` so you can tweet and broadcast messages.
  - A Cog admin in `#production` can run `!group-member-add release-manager <your handle>`, or you could be [manually added to Marvin](https://gitlab.com/gitlab-com/runbooks/blob/master/howto/manage-cog.md#add-a-user)
- [ ] Added to `chatops` group on `ops.gitlab.net` (so they can run `!chatops` release commands

## Why

I'll be a trainee release manager in TRAINEE_RELEASE and release manager in RELEASE_YOU_WILL_MANAGE.

Onboarding task: LINK_TO_ONBOARING_ISSUE

## SSH Details

### Username

This should be your local POSIX user (you can check it by running `whoami` from a terminal)

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

- [ ] Trainee: Follow instructions to set up [bastion access](https://gitlab.com/gitlab-com/runbooks/blob/master/howto/rm-bastion-access.md)
  - [ ] Test gstg access by SSH'ing in to a staging node: `ssh sidekiq-besteffort-01-sv-gstg.c.gitlab-staging-1.internal`
  - [ ] Test gprd access by SSH'ing in to a production node: `ssh sidekiq-besteffort-01-sv-gprd.c.gitlab-production.internal`
- [ ] Trainee: Make sure you have [takeoff](https://gitlab.com/gitlab-org/takeoff) cloned locally, and [set it up](https://gitlab.com/gitlab-org/takeoff/#getting-started)
- [ ] Trainee: Make sure you have [release-tools](https://gitlab.com/gitlab-org/release-tools) cloned locally, and [set it up](https://gitlab.com/gitlab-org/release-tools/blob/master/doc/rake-tasks.md#setup)
- [ ] Trainee: If your ssh key has a passphrase, you will want to do `ssh-add` in your local takeoff repo
- [ ] Trainee: Make sure you can log in into zoom with Releasa Manager's account. You can find the credentials in 1 password under `Release Managers Zoom`.

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
