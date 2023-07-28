# rust-template

[![Views](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2Fuplau%2Frust-template&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=Views&edge_flat=false)](https://hits.seeyoufarm.com)
[![GitHub workflow status](https://github.com/uplau/rust-template/actions/workflows/generate.yaml/badge.svg)](https://github.com/uplau/rust-template/actions/workflows/generate.yaml)
[![License](https://img.shields.io/badge/license-MIT%2FApache--2.0-blue.svg)](./LICENSE-MIT)

A github rust workflows template, just want to focus on coding.

- [Who uses?](https://github.com/search?q=in%3Areadme+uplau%2Frust-template&type=repositories)
- [Demo template](https://github.com/uplau/rust-template-demo)
- [GitHub Actions](https://github.com/uplau/rust-template/actions/workflows/generate.yaml)
- [Workflow file](.github/workflows/generate.yaml)

## Table of contents

- [Features](#features)
- [Usage](#usage)
- [Template options](#template-options)
- [Template workflows](#template-workflows)
- [Contributors](#contributors)
- [License](#license)

## Features

- [x] Directly create your Github repository
- [x] Fast generate template with GitHub Actions
- [x] Support [cargo-generate](https://github.com/cargo-generate/cargo-generate)

### Template

- [x] Based on conventional commits
- [ ] Based on push vTag
- [x] Bumps Crate version
- [x] Create GitHub tag
- [x] Generate Changelog
- [x] Continuous integration with caching
- [x] Cross-platform static compilation
- [x] [Upload artifact](https://github.com/actions/upload-artifact/tree/main)
- [ ] Publish to Crates
- [ ] Publish to Docker hub
- [x] Publish to Github releases
- [x] [contrib.rocks](https://contrib.rocks/)
- [ ] [starcharts](https://starchart.cc/)

## Usage

### Use GitHub actions

This will not affect your Github, give it a try:

1. [Use this template](https://github.com/new?template_name=rust-template&template_owner=uplau).
2. Under your repository name, click `Actions`.
3. In the left sidebar, click the `Generate`.
4. Above the list of workflow runs, click the **Run workflow** button.
5. When all work is done, at the bottom of the workflow summary page, download template artifacts.
6. Enjoy!

**If need directly create your Github repository, in addition to all the above steps, you also need:**

1. [Creating a fine-grained personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-fine-grained-personal-access-token).

   > Repository access: `All repositories`

   > Permissions > Repository permissions: `Administration` `Contents` `Workflows` > Access: `Read and write`

2. Copy personal access token.

3. [Creating encrypted secrets for a repository](https://docs.github.com/en/actions/security-guides/encrypted-secrets#creating-encrypted-secrets-for-a-repository).
   > Name field:
   > `PAT_ADMIN_CODE_WORKFLOWS`

### Use cargo-generate

[See more](https://github.com/cargo-generate/cargo-generate).

```bash
# bin
cargo generate --git https://github.com/uplau/rust-template ./template --name "crate-name" --bin

# lib
cargo generate --git https://github.com/uplau/rust-template ./template --name "crate-name" --lib
```

## Template options

| Field             | Type       | Default  | Description                                                           |
| ----------------- | ---------- | -------- | --------------------------------------------------------------------- |
| crate-name        | string     | required | Package name                                                          |
| crate-type        | bin or lib | bin      | [Linkage](https://doc.rust-lang.org/reference/linkage.html)           |
| owner             | string     | required | Owner, for filling README and LICENSE and note `Cargo.toml`           |
| copyright-year    | string     | 2023     | Copyright year, for filling LICENSE                                   |
| use-badge         | bool       | true     | Insert status badge to README top                                     |
| use-contrib-rocks | bool       | false    | Insert [contrib.rocks](https://contrib.rocks/) to README#Contributors |
| use-deps          | bool       | true     | Insert commonly use deps to Cargo.toml                                |
| use-rust-template | bool       | true     | Insert rust-template to README#Contributing                           |

## Template workflows

Workflows of `bin` can be view:

- [workflow file](https://github.com/uplau/rust-template-demo/blob/main/.github/workflows/cicd.yaml)
- [on push and pull request summary](https://github.com/uplau/rust-template-demo/actions/runs/5683949188)
- [release please PR](https://github.com/uplau/rust-template-demo/pull/1)
- [automatic release summary](https://github.com/uplau/rust-template-demo/actions/runs/5684009518)
- [automatic release assets](https://github.com/uplau/rust-template-demo/releases/tag/v0.1.0)
- [manually release summary](https://github.com/uplau/rust-template-demo/actions/runs/5684125035)
- [manually release assets](https://github.com/uplau/rust-template-demo/releases/tag/next)

Workflows of `lib` can be view:

- [workflow file](https://github.com/uplau/rust-template-demo/blob/lib-yes-use-all/.github/workflows/cicd.yaml)
- [manually summary](https://github.com/uplau/rust-template-demo/actions/runs/5684106223)

### `jobs.release_please`

We use [Release Please](https://github.com/google-github-actions/release-please-action) parses your git history, looking for [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/), and creating release PRs to:

> [What's a Release PR?](https://github.com/google-github-actions/release-please-action#whats-a-release-pr)

> [How should I write my commits?](https://github.com/googleapis/release-please#how-should-i-write-my-commits)

> [Does not create a release PR. Why?](https://github.com/googleapis/release-please#release-please-bot-does-not-create-a-release-pr-why)

> **You need allow GitHub Actions to create and approve pull requests**, setting can be managed by admins in organization settings under Actions > General > Workflow permissions.

- Bumps Crate version
- Create Github tag
- Generate Changelog

### `jobs.ci`

We run the following command to complete continuous integration:

https://github.com/uplau/rust-template/blob/7b8fe911cd41c14db2fc5fab4b83c40b49bc52a5/template/.github/workflows/cicd.yaml#L53

- `cargo test`
- `cargo fmt`
- `cargo clippy`

### `jobs.build` `only_bin`

When the ci passed, we build statically linked binaries under the following targets and upload the artifacts:

> You can modify it as you like, but you need to pay attention to some extra steps for some target.

https://github.com/uplau/rust-template/blob/7b8fe911cd41c14db2fc5fab4b83c40b49bc52a5/template/.github/workflows/cicd.yaml#L89-L103

### `jobs.*_release` `only_bin`

When the build passed, we download the artifacts and publish to Github releases, which you can download at any time at the bottom of the workflow summary page:

- `manually_release`: Triggered by `workflow_dispatch`
- `automatic_release`: Triggered by `release_please`

## Contributors

<a href="https://github.com/uplau/rust-template/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=uplau/rust-template&max=400&columns=20" />
</a>

## License

rust-template is licensed under either of the following, at your option:

- [MIT License](./LICENSE-MIT)
- [Apache-2.0 License](./LICENSE-APACHE)
