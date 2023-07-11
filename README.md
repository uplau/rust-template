# rust-template

![GitHub workflow status](https://github.com/uplau/rust-template/actions/workflows/generate.yaml/badge.svg)
![License](https://img.shields.io/badge/license-MIT%2FApache--2.0-blue.svg)

A github rust workflows template, just want to focus on coding.

- [Demo template](https://github.com/uplau/rust-template/tree/demo)
- [View actions](https://github.com/uplau/rust-template/actions/workflows/generate.yaml)

## Table of Contents

- [Feature](#feature)
- [Usage](#usage)
- [Template Options](#template-options)
- [Template workflows](#template-workflows)
- [License](#license)

## Feature

- [x] Fast generate template with [GitHub Actions](https://github.com/uplau/rust-template/actions/workflows/generate.yaml) and caching
- [x] Support [cargo-generate](https://github.com/cargo-generate/cargo-generate)
- [ ] ??Directly create your repository??

### Template

- [x] [Automated releases based on conventional commits](https://github.com/google-github-actions/release-please-action)
- [x] Continuous integration with caching
- [x] Cross-platform static compilation
- [x] [Upload artifact](https://github.com/actions/upload-artifact/tree/main)
- [x] Publish to Github releases

## Usage

### Use GitHub Actions

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

## Template Options

| Field             | Type       | Default  | Description                                                 |
| ----------------- | ---------- | -------- | ----------------------------------------------------------- |
| crate-name        | string     | required | Package name                                                |
| crate-type        | bin or lib | bin      | [Linkage](https://doc.rust-lang.org/reference/linkage.html) |
| gh-username       | string     | required | GitHub username (or organization)                           |
| copyright-year    | string     | 2023     | Copyright year                                              |
| use-badge         | bool       | true     | Insert status badge to README top                           |
| use-deps          | bool       | true     | Insert commonly use deps to Cargo.toml                      |
| use-rust-template | bool       | true     | Insert rust-template to README#Contributing                 |

## Template workflows

> This document is not exhaustive, [see](./template/.github/workflows/cicd.yaml)

- `jobs.release_please`
- `jobs.ci`
- `jobs.build`
- `jobs.manually_release`
- `jobs.automatic_release`

## License

rust-template is licensed under either of the following, at your option:

- [MIT License](./LICENSE-MIT)
- [Apache License, Version 2.0](./LICENSE-APACHE)
