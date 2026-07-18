# Contributing

Thanks for helping make Codex App Linux work across more distros.

## Distro Support PRs

Use a fork-based pull request. You do not need direct push access to this repo.

1. Fork `antonlobanovskiy/codex-app-linux`.
2. Create a branch named `codex/<distro>-linux-port`, for example
   `codex/fedora-linux-port`.
3. Install and test from a clean checkout on the distro you are adding.
4. Update [docs/distro-support.md](docs/distro-support.md):
   - Add or update the distro row.
   - Change `Verified` to `[x]` and `Status` to `Tested` only when the installer
     actually ran and the app launched.
   - Link your PR in the evidence column after opening it.
5. Add a distro setup guide under `docs/` if the package commands differ from
   existing guides.
6. Fill out the PR template with exact test results.

The maintainer controls merges. Contributors can open PRs from forks, but only
repo maintainers can merge into `main`.

A **Likely compatible (untested)** row only means the distro should be able to
reuse an existing dependency guide because it has a closely related package
base. It is still unverified. A PR must test the exact distro version, desktop
environment, session type, and architecture before changing that row to
`Tested`.

## Required Test Evidence

For distro support, include:

- distro name and version
- desktop environment and session type, such as GNOME/X11 or KDE/Wayland
- CPU architecture
- Node.js and npm versions
- Codex CLI version
- the exact dependency install command used
- the exact `scripts/install.sh` command used
- whether the app launched from `codex-desktop-linux`
- whether the desktop entry appeared in the app menu
- what does not work yet

Do not attach or commit the Codex DMG, extracted app files, screenshots that
include secrets, logs with credentials, or `~/.codex/auth.json`.

## Before Opening A PR

Run:

```bash
command -v rg >/dev/null || echo "Install ripgrep before running the audit."
./scripts/prepublish-audit.sh
git status --short
```

The audit is intentionally conservative. If it fails, inspect the reported path
or token-like text instead of adding an exception.
