# rust-template

[![GitHub workflow status](https://github.com/uplau/rust-template/actions/workflows/generate.yaml/badge.svg)](https://github.com/uplau/rust-template/actions/workflows/generate.yaml)
[![License](https://img.shields.io/badge/license-MIT%2FApache--2.0-blue.svg)](./LICENSE-MIT)

A github rust workflows template, just want to focus on coding.

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

- [x] Fast generate template with GitHub Actions and caching
- [x] Support [cargo-generate](https://github.com/cargo-generate/cargo-generate)
- [ ] ??Directly create your Github repository??

### Template

- [x] Based on conventional commits
- [ ] Based on push vTag
- [x] Bumps Crate version
- [x] Create GitHub tags
- [x] Generate CHANGELOG
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

> When running for the first time, the cache needs to be created.
> Next time, soon.

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
| gh-username       | string     | required | GitHub username (or organization), for filling LICENSE                |
| copyright-year    | string     | 2023     | Copyright year, for filling LICENSE                                   |
| use-badge         | bool       | true     | Insert status badge to README top                                     |
| use-contrib-rocks | bool       | false    | Insert [contrib.rocks](https://contrib.rocks/) to README#Contributors |
| use-deps          | bool       | true     | Insert commonly use deps to Cargo.toml                                |
| use-rust-template | bool       | true     | Insert rust-template to README#Contributing                           |

## Template workflows

> This document is not exhaustive, [see](./template/.github/workflows/cicd.yaml)

The workflows of `bin` can be [view summary here](https://github.com/uplau/rust-template-demo/actions/runs/5644583514), [view file here](https://github.com/uplau/rust-template-demo/blob/main/.github/workflows/cicd.yaml).

The workflows of `lib` can be [view summary here](https://github.com/uplau/rust-template-demo/actions/runs/5644157705), [view file here](https://github.com/uplau/rust-template-demo/blob/lib-default-use/.github/workflows/cicd.yaml).

### `jobs.release_please` `only_bin`

We use [Release Please](https://github.com/google-github-actions/release-please-action) parses your git history, looking for [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/), and creating release PRs to:

> [What's a Release PR?](https://github.com/google-github-actions/release-please-action#whats-a-release-pr)

> **You need allow GitHub Actions to create and approve pull requests**, setting can be managed by admins in organization settings under Actions > General > Workflow permissions.

- Bumps Crate version
- Create GitHub tags
- Generate CHANGELOG

### `jobs.ci`

We run the following command to complete continuous integration:

- `cargo test`
- `cargo fmt`
- `cargo clippy`

### `jobs.build` `only_bin`

When ci is passed, we build under the following targets:

> `static_link` `64bit`

- `macOS`
- `Linux`
- `Windows`

### `jobs.*_release` `only_bin`

When the build passes, we upload the artifacts and publish to Github releases, which you can download at any time at the bottom of the workflow summary page:

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
