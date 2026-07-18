# Distro Support Matrix

This matrix tracks where Codex App Linux has been tested and where its existing
package guides are likely to apply. A distro is checked only after a PR includes
test evidence from a real machine or VM.

## Support Levels

- `[x] Tested`: installer ran and the app launched with evidence in a merged PR.
- `[ ] Likely compatible (untested)`: the distro shares a close package base
  with a tested distro and should be able to reuse an existing setup guide.
  This is an inference, not a successful install claim.
- `[ ] Needs PR`: no accepted test evidence and no existing setup guide is
  assumed to apply without distro-specific work.
- `[ ] In progress`: a contributor is actively testing or has a PR open.

`Likely compatible` does not confirm dependency installation, the installer,
app launch, desktop entry, authentication, or Browser Use. Each exact distro,
desktop environment, session type, and architecture still needs test evidence.

## Matrix

| Verified | Status | Distro | Family | Setup guide | Test environment | Evidence | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- |
| [x] | Tested | Ubuntu 24.04 LTS | Debian/Ubuntu | [ubuntu.md](ubuntu.md) | GNOME/X11, x86_64 | Initial project test | Baseline distro. |
| [x] | Tested | Fedora Linux 44 | Fedora/RHEL | [fedora.md](fedora.md) | Cinnamon/X11, x86_64 | Community PR | Installed with `dnf`; `scripts/install.sh` completed and `codex-desktop-linux` launched. Browser Use shim not tested; GNOME sessions not yet validated. |
| [ ] | Likely compatible (untested) | Linux Mint 22.3 Cinnamon | Debian/Ubuntu | [ubuntu.md](ubuntu.md) | Untested, x86_64 candidate | [Ubuntu Noble package base](https://www.linuxmint.com/download_all.php) | Expected to reuse the Ubuntu package steps; the full install and launch flow needs a PR. |
| [ ] | Likely compatible (untested) | Xubuntu 24.04 LTS | Debian/Ubuntu | [ubuntu.md](ubuntu.md) | Untested, x86_64 candidate | [Xubuntu 24.04 release notes](https://xubuntu.org/releasedocs/24.04/release-notes/) | Shares the Ubuntu 24.04 package base; Xfce desktop integration needs a PR. |
| [ ] | Likely compatible (untested) | Ubuntu MATE 24.04 LTS | Debian/Ubuntu | [ubuntu.md](ubuntu.md) | Untested, x86_64 candidate | [Ubuntu MATE 24.04 release notes](https://ubuntu-mate.org/blog/ubuntu-mate-noble-numbat-release-notes/) | Shares the Ubuntu 24.04 package base; MATE desktop integration needs a PR. |
| [ ] | Likely compatible (untested) | Zorin OS 18.1 | Debian/Ubuntu | [ubuntu.md](ubuntu.md) | Untested, x86_64 candidate | [Ubuntu 24.04 base](https://zorin.com/os/details/) | Expected to reuse the Ubuntu package steps; GNOME and Xfce editions need separate evidence. |
| [ ] | Likely compatible (untested) | Fedora Linux 44 Xfce Spin | Fedora/RHEL | [fedora.md](fedora.md) | Untested, x86_64 candidate | [Fedora 44 Spins](https://fedoraproject.org/spins/) | Expected to reuse the Fedora package steps; Xfce integration needs a PR. |
| [ ] | Likely compatible (untested) | Fedora Linux 44 MATE+Compiz Spin | Fedora/RHEL | [fedora.md](fedora.md) | Untested, x86_64 candidate | [Fedora 44 Spins](https://fedoraproject.org/spins/) | Expected to reuse the Fedora package steps; MATE+Compiz integration needs a PR. |
| [ ] | Likely compatible (untested) | Fedora Linux 44 LXQt Spin | Fedora/RHEL | [fedora.md](fedora.md) | Untested, x86_64 candidate | [Fedora 44 Spins](https://fedoraproject.org/spins/) | Expected to reuse the Fedora package steps; LXQt integration needs a PR. |
| [ ] | Likely compatible (untested) | Fedora Linux 44 Budgie Spin | Fedora/RHEL | [fedora.md](fedora.md) | Untested, x86_64 candidate | [Fedora 44 Spins](https://fedoraproject.org/spins/) | Expected to reuse the Fedora package steps; Budgie integration needs a PR. |
| [ ] | Needs PR | Debian Stable | Debian/Ubuntu | Needed | Pending | Needs PR | Likely close to Ubuntu, but Node.js setup may differ. |
| [ ] | Needs PR | Pop!_OS 24.04 | Debian/Ubuntu | Needed | Pending | Needs PR | Ubuntu-family package base, but its COSMIC desktop needs separate validation. |
| [ ] | Needs PR | elementary OS | Debian/Ubuntu | Needed | Pending | Needs PR | Ubuntu-family desktop distro; package and desktop behavior need validation. |
| [ ] | Needs PR | Arch Linux | Arch | Needed | Pending | Needs PR | Rolling distro; package names and native module builds need validation. |
| [ ] | Needs PR | EndeavourOS | Arch | Needed | Pending | Needs PR | Arch-family desktop distro. |
| [ ] | Needs PR | Manjaro | Arch | Needed | Pending | Needs PR | Arch-family desktop distro with delayed package channels. |
| [ ] | Needs PR | openSUSE Tumbleweed | openSUSE | Needed | Pending | Needs PR | Rolling openSUSE target. |
| [ ] | Needs PR | openSUSE Leap | openSUSE | Needed | Pending | Needs PR | Stable openSUSE target. |
| [ ] | Needs PR | Nobara | Fedora/RHEL | Needed | Pending | Needs PR | Fedora-family desktop distro; package differences need validation. |
| [ ] | Needs PR | AlmaLinux | Fedora/RHEL | Needed | Pending | Needs PR | Enterprise Linux target; desktop packages may vary. |
| [ ] | Needs PR | Rocky Linux | Fedora/RHEL | Needed | Pending | Needs PR | Enterprise Linux target; desktop packages may vary. |

## How To Check Off A Distro

Open a PR that includes:

1. An update to the distro row above: set `Verified` to `[x]`, change `Status`
   to `Tested`, and record the exact test environment.
2. A setup guide under `docs/` if package commands differ from an existing
   guide.
3. Test evidence in the PR body using the repository PR template.
4. The result of `./scripts/prepublish-audit.sh`.

Keep the support matrix honest. A shared package base can justify a `Likely
compatible (untested)` row, but only a completed install and app launch can
justify `Tested`. If the app installs with known gaps, record them in the notes.
