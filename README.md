# CW Keyer Daemon


A lightweight, no-frills **CW (Morse Code) keyer daemon** written in a single Python file.

Designed for simplicity, portability, and ease of deployment -- no root privileges required.


---

## Features

- Basic [cwdaemon] compatibility
- Single-file implementation (no installation required)
- Runs without `sudo`
- Supports:
  - In-message speed change
  - Backspace handling
- Optional systemd user service integration


---

## Requirements

- Python 3.13+ (tested on Debian 13)
- Dependencies
  - pyserial (`python3-serial`)

##  Usage

### Run in foreground from a terminal

```bash
./cwkd [options]
```

```bash
./cwkd -h
```

### Testing

In `bash`, using the default UDP port:

```bash
echo "CQ CQ TEST" > /dev/udp/127.0.0.1/6789
```


### Systemd integration as a user unit

Assuming that _cwkd_ was cloned into `$HOME/cwkd`:

```bash
mkdir -p $HOME/.config/systemd/user
cp $HOME/cwkd/cwkd.service $HOME/.config/systemd/user/cwkd.service
systemctl --user daemon-reload
systemctl --user enable cwkd
systemctl --user start cwkd
systemctl --user status cwkd
journalctl --user-unit cwkd
```

