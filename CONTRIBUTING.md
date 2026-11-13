# Contributing to digest

digest does not accept pull requests.

All code in this project is written by the maintainers. This is a supply-chain integrity decision: it keeps the origin of every line we ship known. Unsolicited pull requests will be closed without review, regardless of size or quality.

You can still help through GitHub Issues:

- Report bugs.
- Request features.
- Give feedback on behavior, output quality, or documentation.

Search existing issues before opening a new one.

## Reporting a bug

A bug report we can act on includes:

- **Version and environment.** The output of `digest version` and `digest info`. `digest version` prints the version, commit, build time, and OS and architecture. `digest info` prints the executable path, install channel, and version. Replace the executable path if it reveals private information, such as a user name or internal directory.
- **Steps to reproduce.** The smallest set of commands, configuration, and input that triggers the problem.
- **Expected and actual behavior.** State both. "It fails" does not say what you expected.
- **Logs or output.** The full error output and the input lines involved.

Remove secrets, tokens, credentials, and personal data before you paste anything. digest reads logs, and logs often contain these. Redact them, do not just trim them.

We may ask for more detail if the report does not include enough to reproduce the problem.

## Requesting a feature

Describe the problem before the solution. A useful feature request covers:

- The task you are trying to do and how you do it today.
- The behavior you want.
- An example of input and the output you would expect, if it applies.

Maintainers review feature requests, but accepting one does not guarantee it will be built.

## Local setup for reproducing bugs

Building from source requires Go 1.24.2 or later, as declared in `go.mod`. digest is built on [spine](https://github.com/scoutbin/spine), which is pulled in as a Go module dependency.

Build from the same commit or tag you are reporting against, so your results match the code the bug was reported on.

```sh
go build .
go run . version
go test ./...
```

The CI pipeline is defined in `.github/workflows/ci.yml`. Release steps are in `.github/workflows/release.yml`. Both use reusable workflows from the spine repository.

## Security vulnerabilities

Do not report security vulnerabilities in public issues, pull requests, or discussions. Follow the process in [SECURITY.md](SECURITY.md).

## Maintainers

`install.sh`, `install.ps1` and `action.yml` are generated from `spine.json`. Do not edit them by hand. After changing `spine.json`, run `go tool spine gen` to regenerate them. `go tool spine gen --check` fails when they are stale.

To release:

1. On an up to date `main`, run `go tool spine change <major|minor|patch> "<message>"`. It adds the `CHANGELOG.md` section, commits it and creates the tag. It does not push.
2. Push the commit and the tag.
3. Start `release.yml` manually with the `tag` input. `publish` defaults to `false`, which runs a dry run. Set it to `true` to publish. The release fails if `CHANGELOG.md` has no section for the tag.

See spine's [RELEASING.md](https://github.com/scoutbin/spine/blob/main/RELEASING.md).
