### 22nd, the release day:

No new code is added to release that was not included in the last RC.
This way we ensure the release does not introduce new regressions.

- At 8:00 UTC, final release is ready for tagging (Including changes at this stage requires signoff from [VP of Eng.][Getting help]):

  - [ ] Ensure tests are green on [CE stable branch]

  - [ ] Ensure tests are green on [EE stable branch]

  - [ ] Ensure tests are green on [Omnibus CE stable branch]

  - [ ] Ensure tests are green on [Omnibus EE stable branch]

  - [ ] Sync stable branches: CE, EE, and Omnibus to `dev`, CE and Omnibus to `github`

  - [ ] Sync master branches to `dev` and `github`, as the CHANGELOG will be automatically updated on master during tagging

  - [ ] If needed, sync tags for dependencies (`gitlab-shell`, `gitlab-workhorse`, `gitlab-pages`, `gitaly`) to `dev` and `github` (when applicable. Builds should fail if this is needed.)

  - [ ] If at this time final release is not ready for tagging, notify the [CTO][Getting help]

- Before 10:00 UTC:

  - [ ] In `#releases`: I'm going to tag `<%= version.to_patch %>`

  - [ ] Tag the `<%= version.to_patch %>` version using the [`release` task]:

        ```sh
        # In the release-tools project:
        bundle exec rake "release[<%= version.to_patch %>]"
        ```

  - [ ] Check progress of [EE packages build] and [CE packages build]. Ask in `#releases` to get confirmation on when the packages are indexed in packagecloud and ready for use in deployment.

- Before 12:00 UTC:

  - [ ] Get confirmation from a production team member to deploy staging. Use `!oncall prod` if needed to find who's on call.

  - [ ] On video call, [deploy] release [`<%= version.to_patch %>`](https://packages.gitlab.com/gitlab/pre-release/packages/ubuntu/xenial/gitlab-ee_<%= version.to_patch %>-ee.0_amd64.deb) to [staging.gitlab.com]

        ```sh
        # In the takeoff project:
        bin/takeoff-deploy -e staging -v <%= version.to_patch %>-ee.0
        ```

  - [ ] Announce on the `#releases` Slack channels: `<%= version.to_patch %>` has been deployed to staging. Blog post draft: MERGE_REQUEST_URL

  - [ ] Create a new QA task issue in [release tasks]

  - [ ] Wait for the QA task deadline to pass

  - [ ] Get confirmation from a production team member. Use `!oncall prod` if needed to find who's on call.

  - [ ] On video call, [deploy] release [`<%= version.to_patch %>`](https://packages.gitlab.com/gitlab/pre-release/packages/ubuntu/xenial/gitlab-ee_<%= version.to_patch %>-ee.0_amd64.deb) to [canary.gitlab.com]

        ```sh
        # In the takeoff project:
        bin/takeoff-deploy -e canary -v <%= version.to_patch %>-ee.0
        ```

  - [ ] Announce on the `#releases` Slack channels: `<%= version.to_patch %>` has been deployed to canary. Blog post draft: MERGE_REQUEST_URL

  - [ ] Get confirmation from a production team member to deploy production. Use `!oncall prod` if needed to find who's on call.

  - [ ] Publicly [announce the deployment] on Twitter and with the GitLab.com deploy alert banner in the `#production` channel

        ```
        !broadcast --start X:Y --end A:B "We are currently deploying GitLab EE <%= version.to_patch %>.
        For status updates, please follow https://twitter.com/GitLabStatus"
        ```

        ```
        !broadcast --start X:Y --end A:B "We are about to deploy GitLab EE <%= version.to_patch %> starting at X:Y UTC"
        ```

        ```
        !tweet "We are about to deploy GitLab EE <%= version.to_patch %> starting at X:Y UTC"
        ```

  - [ ] On video call, [deploy] release [`<%= version.to_patch %>`](https://packages.gitlab.com/gitlab/pre-release/packages/ubuntu/xenial/gitlab-ee_<%= version.to_patch %>-ee.0_amd64.deb) to GitLab.com

        ```sh
        # In the takeoff project:
        bin/takeoff-deploy -e production -v <%= version.to_patch %>-ee.0
        ```

  - [ ] Tweet in the `#production` channel that the deployment has finished:

        ```
        !tweet "GitLab EE <%= version.to_patch %> has been deployed."
        ```

  - [ ] Create the first patch issue using the [`patch_issue` task]:

        ```sh
        # In the release-tools project:
        bundle exec rake "patch_issue[<%= version.next_patch %>]"
        ```

  - [ ] If at this point final release is not ready for public, notify the [CEO](https://about.gitlab.com/team/#sytses)

- At 15:00 UTC:

  - Make sure that neither packages nor blog post get published before that time without approval by the marketing team.

  - [ ] From the [build pipeline], [manually publish public packages]

  - [ ] Verify that packages appear on `packages.gitlab.com`: [EE](https://packages.gitlab.com/app/gitlab/gitlab-ee/search?q=<%= version.to_patch %>) / [CE](https://packages.gitlab.com/app/gitlab/gitlab-ce/search?q=<%= version.to_patch %>)

  - [ ] Verify that Docker images appear on `hub.docker.com`: [EE](https://hub.docker.com/r/gitlab/gitlab-ee/tags) / [CE](https://hub.docker.com/r/gitlab/gitlab-ce/tags)

  - [ ] Create the `<%= version.to_patch %>` version on https://version.gitlab.com

  - [ ] Ensure someone tweets about the `<%= version.to_patch %>` release in the `#releases` channel