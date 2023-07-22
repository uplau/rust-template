# {{project-name}}{%if use-badge%}

![GitHub workflow status](https://github.com/{{gh-username}}/{{project-name}}/actions/workflows/cicd.yaml/badge.svg)
![GitHub release (with filter)](https://img.shields.io/github/v/release/{{gh-username}}/{{project-name}})
![GitHub all releases](https://img.shields.io/github/downloads/{{gh-username}}/{{project-name}}/total)
![License](https://img.shields.io/badge/license-MIT%2FApache--2.0-blue.svg){%- endif %}

## Table of Contents

- [Contributing](#contributing)
- [License](#license)

## Contributing{%if use-rust-template%}

This project uses [rust-template](https://github.com/uplau/rust-template) to start.{%- endif %}

See the [contributing guidelines](./CONTRIBUTING.md) for more information.

## License

{{project-name}} is licensed under either of the following, at your option:

- [MIT license](./LICENSE-MIT)
- [Apache License, Version 2.0](./LICENSE-APACHE)
