# digest

digest turns logs into readable facts. It is built on [spine](https://github.com/scoutbin/spine), which provides the command framework.

Status: early development. The log-processing code is not written yet. The binary currently has only the built-in commands listed below.

## Install

Homebrew:

```sh
brew install scoutbin/tap/digest
```

npm:

```sh
npm install -g @scoutbin/digest
```

macOS and Linux (needs curl or wget):

```sh
curl -fsSL https://raw.githubusercontent.com/scoutbin/digest/main/install.sh | sh
```

Windows (PowerShell 5.1 or pwsh):

```powershell
irm https://raw.githubusercontent.com/scoutbin/digest/main/install.ps1 | iex
```

You can also download an archive from GitHub Releases. Archives are named `digest_<version>_<os>_<arch>.tar.gz` (`.zip` on Windows) and come with `checksums.txt`. Both installers verify the SHA-256 checksum before they install anything.

Run `digest version` to confirm the install.

### Installer options

Set these as environment variables before running an installer.

| Variable                   | Default                                                                | Purpose                                                                                                      |
| -------------------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| `DIGEST_VERSION`           | newest release on the track                                            | Install this tag, such as `v0.1.1`. Takes precedence over `DIGEST_TRACK`                                     |
| `DIGEST_TRACK`             | `stable`                                                               | `stable`, `alpha`, `beta` or `rc`                                                                            |
| `DIGEST_INSTALL_DIR`       | `~/.local/bin` (install.sh), `%LOCALAPPDATA%\digest\bin` (install.ps1) | Install directory                                                                                            |
| `DIGEST_NO_MODIFY_PATH`    | unset                                                                  | Set to `1` to leave your PATH alone                                                                          |
| `DIGEST_GITHUB_TOKEN`      | none                                                                   | Token for the release lookup. Not used for downloads                                                         |
| `DIGEST_DOWNLOAD_BASE_URL` | GitHub                                                                 | install.sh only. Mirror for release assets, starting with `https://` or `file://`. Requires `DIGEST_VERSION` |

Example:

```sh
curl -fsSL https://raw.githubusercontent.com/scoutbin/digest/main/install.sh | DIGEST_VERSION=v0.1.1 sh
```

## Commands

- `digest version` prints the version, commit, build time, OS and architecture. The first line looks like `digest v0.1.1`. Add `--json` for machine-readable output.
- `digest info` prints the executable path, the install channel (`install.sh`, `npm`, `homebrew` or `unknown`) and the version.
- `digest check` compares the build with the newest release on its track. It exits with 1 when an update exists.
- `digest upgrade` is available on macOS and Linux. For installs made with install.sh, it replaces the binary after the checksum passes. Use `--version <tag>` to pin a tag, which is also limited to install.sh installs. For npm and Homebrew installs, it prints the command to run instead. On Windows, run install.ps1 again to update.

Global flags: `--version`, `--json`, `--no-color` (also set by the `NO_COLOR` environment variable), and `-h` or `--help`.

Exit codes: 0 for success, 1 when `check` finds an update, 2 for any other error.

## GitHub Action

The action installs the digest binary. It does not run digest.

```yaml
- uses: scoutbin/digest@v0.0.1
  with:
    version: v0.0.1
- run: digest version
```

The ref after `@` selects the action code, not the installed version. If you leave out `version`, the action installs the newest release on `track`, whatever the ref is. You can use a full commit SHA as the ref instead of the tag.

| Input         | Default                     | Purpose                                         |
| ------------- | --------------------------- | ----------------------------------------------- |
| `version`     | newest release on the track | Install this tag. Takes precedence over `track` |
| `track`       | `stable`                    | `stable`, `alpha`, `beta` or `rc`               |
| `install-dir` | `$RUNNER_TEMP/digest/bin`   | Install directory                               |
| `token`       | `github.token`              | Token for the release lookup                    |

Outputs: `version` (the installed tag) and `path` (the path to the executable).

## Feedback

Report bugs and request features in [GitHub Issues](https://github.com/scoutbin/digest/issues). See [CONTRIBUTING.md](CONTRIBUTING.md) for what a good report includes. digest does not accept pull requests. Report security vulnerabilities as described in [SECURITY.md](SECURITY.md).

## License

Apache-2.0. See [LICENSE](LICENSE).
