#### <%= version.to_rc(2) %>

- [ ] Create preparation MRs by following the [instructions in release-tools](https://gitlab.com/gitlab-org/release-tools/blob/master/doc/picking-into-merge-requests.md).

- [ ] Cherry-pick changes into preparation MRs following their instructions

- [ ] Cherry-pick remaining merge requests labeled <%= version.picking_label %> using this [Merged MRs list]
- Check the following list of critical issues/MRs which are to be included in `<%= version.to_patch %>`. Ensure each has made both CE and EE
  
  - [ ] REFERENCE_TO_MR_TO_PICK

- Follow the [Creating subsequent RCs] guide for `<%= version.to_rc(2) %>`:
  
  - [ ] If you didn't merge CE into EE in the preparation branches, or if the CE stable branch had additional commits, merge CE `<%= version.stable_branch %>` into EE `<%= version.stable_branch(ee: true) %>` following the [Merging a CE stable branch into its EE counterpart] guide. (In general this should be unnecessary.)
  
  - [ ] Ensure builds are green on [Omnibus CE stable branch] and [Omnibus EE stable branch]
  
  - [ ] Sync stable branches: CE, EE, and Omnibus to `dev`, CE and Omnibus to `github`
  
  - [ ] Sync master branches to `dev` and `github`, as the CHANGELOG will be automatically updated on master during tagging
  
  - [ ] If needed, sync tags for dependencies (`gitlab-shell`, `gitlab-workhorse`, `gitlab-pages`, `gitaly`) to `dev` and `github` (when applicable. Builds should fail if this is needed.)
  
  - [ ] Check for any problematic migrations in EE (EE migrations include CE ones), and paste the diff in a snippet: `git diff v<%= version.to_rc %>-ee..<%= version.stable_branch(ee: true) %> -- db/migrate db/post_migrate` =>
  
  - [ ] In `#releases`: I'm going to tag `<%= version.to_rc(2) %>`
  
  - [ ] Tag the `<%= version.to_rc(2) %>` version using the [`release` task]:

        ```sh
        # In the release-tools project:
        bundle exec rake "release[<%= version.to_rc(2) %>]"
        ```

- [ ] Check progress of [EE packages build](https://dev.gitlab.org/gitlab/omnibus-gitlab/commits/<%= version.to_omnibus(for_rc: 2, ee: true) %>) and [CE packages build](https://dev.gitlab.org/gitlab/omnibus-gitlab/commits/<%= version.to_omnibus(for_rc: 2) %>). Ask in `#releases` to get confirmation on when the packages are indexed in packagecloud and ready for use in deployment.

- [ ] Get confirmation from a production team member to deploy staging. Use `!oncall prod` if needed to find who's on call.

- [ ] On video call, [deploy] release [`<%= version.to_rc(2) %>`](https://packages.gitlab.com/gitlab/unstable/packages/ubuntu/xenial/gitlab-ee_<%= version.to_rc(2) %>.ee.0_amd64.deb) to [staging.gitlab.com]

    ```sh
    # In the takeoff project:
    bin/takeoff-deploy -e staging -v <%= version.to_rc(2) %>.ee.0
    ```

- [ ] Share the output of the migrations from the takeoff script in this issue via a snippet. Flag any migrations that take more than 5 minutes to run.

- [ ] Announce on the `#releases` Slack channels: `<%= version.to_rc(2) %>` has been deployed to staging. Blog post draft: MERGE_REQUEST_URL

- [ ] Announce with an `@product-team` mention on the `#product` Slack channel: @product-team `<%= version.to_rc(2) %>` has been deployed to staging. Blog post draft: MERGE_REQUEST_URL

- [ ] Create a new QA task issue in [release tasks]

- [ ] Wait for the QA task deadline to pass

- [ ] Get confirmation from a production team member to deploy canary. Use `!oncall prod` if needed to find who's on call.

- [ ] On video call, [deploy] release [`<%= version.to_rc(2) %>`](https://packages.gitlab.com/gitlab/unstable/packages/ubuntu/xenial/gitlab-ee_<%= version.to_rc(2) %>.ee.0_amd64.deb) to [canary.gitlab.com]

    ```sh
    # In the takeoff project:
    bin/takeoff-deploy -e canary -v <%= version.to_rc(2) %>.ee.0
    ```

- [ ] Announce on the `#releases` Slack channels: `<%= version.to_rc(2) %>` has been deployed to canary. Blog post draft: MERGE_REQUEST_URL

- [ ] Get confirmation from a production team member to deploy production. Use `!oncall prod` if needed to find who's on call.

- [ ] If downtime is expected, publicly [announce the deployment] on Twitter and with the GitLab.com deploy alert banner in the `#production` channel, 1 hour in advance

    ```
    !broadcast --start X:Y --end A:B "We are currently deploying GitLab EE <%= version.to_rc(2) %>.
    For status updates, please follow https://twitter.com/GitLabStatus"
    ```

    ```
    !broadcast --start X:Y --end A:B "We are about to deploy GitLab EE <%= version.to_rc(2) %> starting at X:Y UTC"
    ```

    ```
    !tweet "We are about to deploy GitLab EE <%= version.to_rc(2) %> starting at X:Y UTC"
    ```

- [ ] On video call, [deploy] release [`<%= version.to_rc(2) %>`](https://packages.gitlab.com/gitlab/unstable/packages/ubuntu/xenial/gitlab-ee_<%= version.to_rc(2) %>.ee.0_amd64.deb) to GitLab.com

    ```sh
    # In the takeoff project:
    bin/takeoff-deploy -e production -v <%= version.to_rc(2) %>.ee.0
    ```

- [ ] Tweet in the `#production` channel that the deployment has finished:

      ```
      !tweet "GitLab EE <%= version.to_rc(2) %> has been deployed."
      ```

- [ ] If the `!broadcast` deploy banner is still up on production, ask in `#releases` for it to be removed.

- [ ] Take notes of the time it took for the migrations to complete on the deployment to production.

    ```
    # On the takeoff repo
    bundle exec rake "follow_migrations[production]"
    ```

- [ ] From the [build pipeline], [manually publish public packages]

- [ ] Verify that packages appear on `packages.gitlab.com`: [EE & CE](https://packages.gitlab.com/app/gitlab/unstable/search?q=<%= version.to_rc(2) %>)

- [ ] Verify that Docker images appear on `hub.docker.com`: [EE](https://hub.docker.com/r/gitlab/gitlab-ee/tags) / [CE](https://hub.docker.com/r/gitlab/gitlab-ce/tags)

- [ ] Post a [tweet about] the `<%= version.to_rc(2) %>` release in the `#releases` channel:

    ```
    !tweet "GitLab <%= version.to_rc(2) %> is available: https://packages.gitlab.com/gitlab/unstable
    This is a release candidate, we'll release <%= version.to_minor %> on the 22nd of this month."
    ```