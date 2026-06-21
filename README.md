# autoupdates

Simple CLI tool to enable/disable automatic updates on Ubuntu systems

## What it controls

- APT automatic updates (`apt-daily`, `apt-daily-upgrade`)
- `unattended-upgrades`
- Update notifier background downloads
- Firmware updates (`fwupd`)
- Snap automatic refresh (via hold mechanism)

## Usage

### Enable Updates (Standard Schedule)
Enables background configuration and lets systemd run updates based on its regular cycle.
```bash
sudo autoupdates enable
# or
sudo autoupdates on
```

### Enable Updates and Run Immediately
Forces the update and security upgrade processes to run **right now** by passing the force flag.
```bash
sudo autoupdates enable --force
# or
sudo autoupdates on -f
```

### Freeze All Updates
```bash
sudo autoupdates disable
# or
sudo autoupdates off
```

### Check Current State
```bash
autoupdates status
```


## Installation

```bash
sudo mv autoupdates /usr/local/bin/autoupdates
sudo chmod +x /usr/local/bin/autoupdates
```

## Notes

- Snap updates are controlled via `refresh.hold`
- Firmware updates are managed via `fwupd`
- The tool does not remove packages or modify system configuration beyond enabling/disabling services

## Purpose

Switch between:
- normal mode (automatic updates enabled)
- travel mode (all automatic updates disabled)
