# Changelog

All notable changes to this project will be documented in this file.
This project adheres to [Semantic Versioning](https://semver.org/) and
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

## [1.1.0] - 2026-10-24

Keeps Ofelia running on hosts without jobs and makes the report option work. Ofelia 0.3.x ignores a configuration file
in Docker mode, so the role now configures the daemon through labels of the Ofelia container.

### Added
- Add `manage_ofelia_keepalive_job` (default `true`): a harmless daily job that stops Ofelia 0.3.x from exiting and restarting in a loop on hosts whose containers carry no `ofelia.job-exec` labels [`68c0854`](https://github.com/gesinn-it-pub/ansible-role-manage-ofelia/commit/68c0854)

### Fixed
- Write job reports when `manage_ofelia_reports_enabled` is set; with Ofelia 0.3.x the setting in `config.ini` was never read, so 1.0.0 wrote no reports [`68c0854`](https://github.com/gesinn-it-pub/ansible-role-manage-ofelia/commit/68c0854)
- Report a change only when the container configuration changed; a container that restarted in a loop made every run report one [`68c0854`](https://github.com/gesinn-it-pub/ansible-role-manage-ofelia/commit/68c0854)

### Changed
- Configure the daemon through labels instead of `config.ini`; the first run removes the old file and recreates the container [`68c0854`](https://github.com/gesinn-it-pub/ansible-role-manage-ofelia/commit/68c0854)
- Stop notifying the `Restart ofelia` handler from the role, because the task that starts the service already recreates the container when the compose file changed; the handler and `tasks_from: restart` stay available [`68c0854`](https://github.com/gesinn-it-pub/ansible-role-manage-ofelia/commit/68c0854)

## [1.0.0] - 2026-10-24

First release. Ofelia was an optional part of `gesinn.manage_traefik` 1.x and is now a role of its own.

### Added
- Add the Ofelia job scheduler as its own role, deployed as a Docker Compose project with the container name `ofelia` [`e8eac5d`](https://github.com/gesinn-it-pub/ansible-role-manage-ofelia/commit/e8eac5d)
- Run Ofelia outside the `traefik` network with the Docker socket mounted read-only [`e8eac5d`](https://github.com/gesinn-it-pub/ansible-role-manage-ofelia/commit/e8eac5d)
- Save job reports only when `manage_ofelia_reports_enabled` is set; the configuration file is passed to the daemon explicitly [`e8eac5d`](https://github.com/gesinn-it-pub/ansible-role-manage-ofelia/commit/e8eac5d)
- Document usage, variables and handlers in the README [`66b9e17`](https://github.com/gesinn-it-pub/ansible-role-manage-ofelia/commit/66b9e17)

### Fixed
- Keep Traefik from logging errors for the Ofelia container [`ddc1a3d`](https://github.com/gesinn-it-pub/ansible-role-manage-ofelia/commit/ddc1a3d)

[Unreleased]: https://github.com/gesinn-it-pub/ansible-role-manage-ofelia/compare/1.1.0...HEAD
[1.1.0]: https://github.com/gesinn-it-pub/ansible-role-manage-ofelia/compare/1.0.0...1.1.0
[1.0.0]: https://github.com/gesinn-it-pub/ansible-role-manage-ofelia/releases/tag/1.0.0
