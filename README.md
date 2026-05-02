# husarion-cockpit-releases

Public release artefacts for the [Husarion Robot Stack](https://husarion.com).

This repository **does not contain source code** — it exists only to
host tagged release downloads for fresh-robot installs and operator
updates. Source lives in a private repo on the Husarion org.

## Install on a robot

### ROSbot XL

On the robot, as root:

```bash
curl -L -o /tmp/setup.tar.gz \
    https://github.com/husarion/husarion-cockpit-releases/releases/download/deploy-rosbot-xl%2Fv0.1.1/husarion-rosbot-xl-deploy-0.1.1.tar.gz
mkdir -p /opt/husarion-rosbot-xl && cd /opt/husarion-rosbot-xl
tar xzf /tmp/setup.tar.gz --strip-components=1
sudo ./install.sh
```

`install.sh` is idempotent — re-running on an already-installed host
just re-pulls images and kicks the stack.

Open `http://<robot-ip>:8081`. Default password: `husarion`.

Updates: re-fetch a newer `deploy-rosbot-xl/v…` tarball above and
re-run `sudo ./install.sh`.

## Release artefact families

| Tag pattern | What it ships | Audience |
|---|---|---|
| `husarion-agent/vX.Y.Z` | `husarion-agent` host-daemon binaries (amd64 + arm64) + sha256, capability-YAML JSON Schema, per-platform integration tarballs | `install.sh` on the robot; capability-YAML authors |
| `deploy-<robot>/vX.Y.Z` | `husarion-<robot>-deploy-X.Y.Z.tar.gz` — self-contained docker compose stack pinned to a validated webui + camera + agent combo | operators bootstrapping or updating a fresh robot |

## Issues / support

Bug reports and questions belong on Husarion's community forum or
support channels — please don't file issues here, they won't be triaged.
