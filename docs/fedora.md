# Fedora Setup

These starter steps prepare Fedora before running the shared Linux installer.
Fedora support is not checked off until a community PR includes real test
evidence.

Community target needing validation:

- Fedora Workstation x86_64
- GNOME/X11 compatibility mode

Install system packages:

```bash
sudo dnf install -y curl p7zip p7zip-plugins rsync xdg-utils python3 make gcc-c++ nodejs npm
```

Verify Node.js 22 or newer is available:

```bash
node --version
```

If Fedora's enabled repositories provide an older Node.js version, install or
enable a Node.js 22-or-newer package before continuing.

Return to the main [README](../README.md) and continue with the DMG download,
Codex CLI login, and `scripts/install.sh`.
