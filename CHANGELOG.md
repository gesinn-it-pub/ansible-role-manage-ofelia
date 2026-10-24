# Changelog

All notable changes to this project will be documented in this file.
This project adheres to [Semantic Versioning](https://semver.org/) and
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

## [1.0.0] - 2026-10-24

First release. Ofelia was an optional part of `gesinn.manage_traefik` 1.x and is now a role of its own.

### Added
- Add the Ofelia job scheduler as its own role, deployed as a Docker Compose project with the container name `ofelia` [`e8eac5d`](https://github.com/gesinn-it-pub/ansible-role-manage-ofelia/commit/e8eac5d)
- Run Ofelia outside the `traefik` network with the Docker socket mounted read-only [`e8eac5d`](https://github.com/gesinn-it-pub/ansible-role-manage-ofelia/commit/e8eac5d)
- Save job reports only when `manage_ofelia_reports_enabled` is set; the configuration file is passed to the daemon explicitly [`e8eac5d`](https://github.com/gesinn-it-pub/ansible-role-manage-ofelia/commit/e8eac5d)
- Document usage, variables and handlers in the README [`66b9e17`](https://github.com/gesinn-it-pub/ansible-role-manage-ofelia/commit/66b9e17)

### Fixed
- Keep Traefik from logging errors for the Ofelia container [`ddc1a3d`](https://github.com/gesinn-it-pub/ansible-role-manage-ofelia/commit/ddc1a3d)

[Unreleased]: https://github.com/gesinn-it-pub/ansible-role-manage-ofelia/compare/1.0.0...HEAD
[1.0.0]: https://github.com/gesinn-it-pub/ansible-role-manage-ofelia/releases/tag/1.0.0
