# Security Policy

## Supported versions

Only the latest stable release of digest receives security fixes. Older releases do not, so upgrade to the latest release to get a fix. Prerelease builds (alpha, beta and rc) are not covered.

## Reporting a vulnerability

Report security vulnerabilities privately through GitHub private vulnerability reporting. In the digest repository, open the Security tab and select "Report a vulnerability".

Do not report security issues in public issues, discussions or pull requests.

## What to include

- The affected version. Paste the output of `digest version`, which also shows the operating system and architecture.
- The install channel. Paste the output of `digest info`. Replace the executable path if it reveals private information.
- The impact: what an attacker can do and what conditions they need.
- Steps to reproduce, with a proof of concept if you have one.
- Remove secrets, tokens and private data from any logs or files you attach. Log files often contain these, so check them first.

## What happens next

1. We acknowledge your report. We aim to do this promptly.
2. We investigate and confirm whether it is a vulnerability in digest. We may ask for more detail. If it is not, we tell you why.
3. We prepare a fix. Where we can, we agree a disclosure date with you.
4. We release the fix in a new stable release and publish a GitHub security advisory that describes the issue and the fixed version.
5. If you want, we credit you in the advisory and the release notes.

Please keep the issue private until a fix is released or we agree on a disclosure date. We aim to keep you informed of progress.

## Scope

In scope:

- The digest code in this repository.
- Release artifacts published from this repository: the release archives, `checksums.txt`, `install.sh`, `install.ps1` and `action.yml`, plus the Homebrew formula and npm package built from a release.
- The build and release workflows in this repository.

Out of scope:

- Third-party dependencies. Report them to the upstream project. Issues in the shared spine module belong to the spine repository.
- Vulnerabilities in GitHub, npm, Homebrew or other platforms. Report them to the platform.
- Other scoutbin repositories. Report them through the Security tab of that repository.

## Pull requests

This project does not accept pull requests, including security fixes. Report the issue as described above, and the maintainers will write the fix.
