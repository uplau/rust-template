# {{project-name}}{% if use-badge %}

[![GitHub workflow status](https://github.com/{{gh-username}}/{{project-name}}/actions/workflows/cicd.yaml/badge.svg)](https://github.com/{{gh-username}}/{{project-name}}/actions/workflows/cicd.yaml)
[![GitHub release (with filter)](https://img.shields.io/github/v/release/{{gh-username}}/{{project-name}})](https://github.com/{{gh-username}}/{{project-name}}/releases/latest)
![GitHub all releases](https://img.shields.io/github/downloads/{{gh-username}}/{{project-name}}/total)
[![License](https://img.shields.io/badge/license-MIT%2FApache--2.0-blue.svg)](./LICENSE-MIT){%- endif %}

## Table of Contents

- [Contributing](#contributing){% if use-contrib-rocks %}
- [Contributors](#contributors){%- endif %}
- [License](#license)

## Contributing{% if use-rust-template %}

This project uses [rust-template](https://github.com/uplau/rust-template) to start.{%- endif %}

See the [contributing guidelines](./CONTRIBUTING.md) for more information.{% if use-contrib-rocks %}

## Contributors

<a href="https://github.com/{{gh-username}}/{{project-name}}/graphs/contributors">
<img src="https://contrib.rocks/image?repo={{gh-username}}/{{project-name}}&max=400&columns=20" />
</a>{%- endif %}

## License

{{project-name}} is licensed under either of the following, at your option:

- [MIT License](./LICENSE-MIT)
- [Apache-2.0 License](./LICENSE-APACHE)
