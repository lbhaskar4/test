### Before the feature freeze

After the previous major version is officially released, the stable branches should be created.

- [ ] Make sure the latest `master` [CE to EE] MR is merged (it will reduce conflicts in the future). Ask in `#ce-to-ee` when in doubt.

- [ ] Create branch `<%= version.stable_branch %>` from CE `master` manually

- [ ] Create branch `<%= version.stable_branch(ee: true) %>` from EE `master` manually

- [ ] In Omnibus create both `<%= version.stable_branch %>` and `<%= version.stable_branch(ee: true) %>` from `master` manually

- [ ] Merge CE stable into EE stable following the [Merging a CE stable branch into its EE counterpart] guide

- [ ] Sync stable branches: CE, EE, and Omnibus to `dev`, CE and Omnibus to `github`

- [ ] Sync master branches to `dev` and `github`, as the CHANGELOG will be automatically updated on master during tagging

### First working day after the feature freeze (7th)

- [ ] Create the <%= version.picking_label %> group label if it doesn't exist: https://gitlab.com/groups/gitlab-org/labels/new
  - Title: `Pick into <%= version.to_minor %>`
  - Description:

    ```
    Merge requests to cherry-pick into the `<%= version.stable_branch %>` branch. Remove the label once picked.
    ```
  - Color: `#00c8ca`

- [ ] In `#development`:

    ```
    @channel

    I am starting the release process for `<%= version.to_rc %>`. Everything merged into `master`
    after this point will go into next month's release. Only regression and security fixes
    will be cherry-picked into `<%= version.stable_branch %>`.

    Please ensure that merge requests have the correct milestone (`<%= version.to_minor %>` for this release)
    and the `Pick into <%= version.to_minor %>` label.

    From now on, please follow the "After the 7th" process:
    https://gitlab.com/gitlab-org/gitlab-ce/blob/master/PROCESS.md#after-the-7th
    ```

- [ ] Make sure the latest `master` [CE to EE] MR is merged (it will reduce conflicts in the future). Ask in `#ce-to-ee` when in doubt.

- [ ] Merge CE `master` into `<%= version.stable_branch %>` manually

- [ ] Merge EE `master` into `<%= version.stable_branch(ee: true) %>` manually

- [ ] Merge CE stable into EE stable following the [Merging a CE stable branch into its EE counterpart] guide

- [ ] Sync stable branches: CE, EE, and Omnibus to `dev`, CE and Omnibus to `github`

- [ ] Sync master branches to `dev` and `github`, as the CHANGELOG will be automatically updated on master during tagging

- [ ] If needed, sync tags for dependencies (`gitlab-shell`, `gitlab-workhorse`, `gitlab-pages`, `gitaly`) to `dev` and `github` (when applicable. Builds should fail if this is needed.)

### RC1

- Follow the [Creating RC1] guide:
  
  - [ ] Create MR on CE master updating the "Installation from Source" guide, creating the "Update" guides
  
  - [ ] Create MR on EE master creating the "CE to EE" guides
  
  - [ ] Create MR on CE master updating the `.gitignore`, `.gitlab-ci.yml`, and `Dockerfile` templates
  
  - [ ] Create MR on CE master updating the dependencies license list
  
  - [ ] Ensure above MRs are merged and marked <%= version.picking_label %>

- [ ] RC `<%= version.to_rc %>`: LINK

____

### Subsequent releases

For subsequent releases, add a task for each version with a link to the [release tasks] issue created using the [release tools].

```

- [ ] RC `X.Y.Z.rcN`: LINK

- [ ] Patch `X.Y.Z.N`: LINK

- [ ] Security patch `X.Y.Z.N`: LINK
```

____

### 22nd, the release day:

Create a new "Release day" task in [release tasks] and link it below.

- [ ] Release day `<%= version.to_minor %>`: LINK

[CE to EE]: https://gitlab.com/gitlab-org/gitlab-ee/merge_requests?label_name[]=CE+upstream&scope=all&state=all
[Merging a CE stable branch into its EE counterpart]: https://gitlab.com/gitlab-org/release-tools/blob/master/doc/merge-ce-into-ee.md#merging-a-ce-stable-branch-into-its-ee-counterpart
[Creating RC1]: https://gitlab.com/gitlab-org/release-tools/blob/master/doc/release-candidates.md#creating-rc1
[release tasks]: https://gitlab.com/gitlab-org/release/tasks
[release tools]: https://gitlab.com/gitlab-org/release-tools
[Getting help]: https://gitlab.com/gitlab-org/release-tools/blob/master/doc/monthly.md#getting-help
[CE stable branch]: https://gitlab.com/gitlab-org/gitlab-ce/commits/<%= version.stable_branch %>
[EE stable branch]: https://gitlab.com/gitlab-org/gitlab-ee/commits/<%= version.stable_branch(ee: true) %>
[Omnibus CE stable branch]: https://gitlab.com/gitlab-org/omnibus-gitlab/commits/<%= version.stable_branch %>
[Omnibus EE stable branch]: https://gitlab.com/gitlab-org/omnibus-gitlab/commits/<%= version.stable_branch(ee: true) %>
[`release` task]: https://gitlab.com/gitlab-org/release-tools/blob/master/doc%2Frake-tasks.md#releaseversionWalk?
[deploy]: https://gitlab.com/gitlab-org/takeoff#deploying-gitlab
[staging.gitlab.com]: https://staging.gitlab.com/
[canary.gitlab.com]: https://canary.gitlab.com/
[manually publish public packages]: https://gitlab.com/gitlab-org/release-tools/blob/master/doc/publishing-packages.md
[build pipeline]: https://dev.gitlab.org/gitlab/omnibus-gitlab/pipelines?scope=tags
[announce the deployment]: https://gitlab.com/gitlab-org/takeoff/blob/master/doc/announce-a-deployment.md