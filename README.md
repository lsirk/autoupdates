# autoupdates

Simple CLI tool to enable/disable automatic updates on Ubuntu systems.

## What it controls

- APT automatic updates (`apt-daily`, `apt-daily-upgrade`)
- `unattended-upgrades`
- Update notifier background downloads
- Firmware updates (`fwupd`)
- Snap automatic refresh (via hold mechanism)
- Ubuntu Pro Livepatch status (read-only)

## Usage

```bash
sudo autoupdates enable   # enable all automatic updates
sudo autoupdates disable  # disable all automatic updates
autoupdates status        # show current status
```

Aliases:

```bash
sudo autoupdates on
sudo autoupdates off
```

## Installation

```bash
sudo mv autoupdates /usr/local/bin/autoupdates
sudo chmod +x /usr/local/bin/autoupdates
```

## Notes

- Snap updates are controlled via `refresh.hold`
- Firmware updates are managed via `fwupd`
- Livepatch is managed via Ubuntu Pro (`pro`) and is not modified by this tool
- The tool does not remove packages or modify system configuration beyond enabling/disabling services

## Purpose

Switch between:
- normal mode (automatic updates enabled)
- travel mode (all automatic updates disabled)
