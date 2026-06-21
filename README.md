# autoupdates

Simple CLI tool to control, freeze, or restore automatic system updates on Ubuntu systems.

When automatic updates are re-enabled with a force flag, the script bypasses systemd scheduler delays and executes standard security updates synchronously inside your current terminal session. It includes strict command-line argument validation to prevent unintended execution from typos.

## What it controls

- APT automatic updates (`apt-daily`, `apt-daily-upgrade`)
- `unattended-upgrades` configuration and service
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
Forces the update (`apt-get update`) and security upgrade processes to run **right now** synchronously inside your current terminal session by passing the force flag.
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

## Error Handling & Validation

The tool automatically validates all switches and options. Invalid arguments, unknown commands, or typos will immediately halt execution to safeguard your environment:

```bash
\$ sudo autoupdates enable --forec
[FAIL] Unknown option: '--forec'

\$ sudo autoupdates disable --force
[FAIL] Disable command does not accept extra options: '--force'
```

## Installation

```bash
sudo mv autoupdates /usr/local/bin/autoupdates
sudo chmod +x /usr/local/bin/autoupdates
```

## Notes

- Snap updates are controlled via `refresh.hold` (indefinitely frozen until year 2999 when updates are disabled).
- Firmware updates are managed via `fwupd`.
- The tool does not remove packages or modify system configuration beyond enabling/disabling services and adjusting `/etc/apt/apt.conf.d/20auto-upgrades`.

## Purpose

Switch between:
- **Normal mode**: Automatic updates enabled to keep the system secure.
- **Travel mode**: All automatic updates completely disabled to save metered bandwidth and avoid unexpected CPU spikes or reboots during maintenance windows.
