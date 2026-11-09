# SonoBus RP Hub

The server half of [SonoBus RP](https://github.com/RandomPlanet-com/SonoBus-RP). Every player sends one stream to the
hub, and the hub sends each player's separate streams to the others, with per-player jitter buffers held at the hub so
one lossy link does not degrade everyone else. It needs no audio interface.

The hub's source code is in the [SonoBus-RP](https://github.com/RandomPlanet-com/SonoBus-RP) repository
(`Source/SonobusHub*`, build target `SonoBusHub`), because the player and the hub share one build.

**Downloads:** <https://randomplanet.com>

## Running a hub on a Mac

Open the disk image, drag SonoBus RP Hub to Applications and open it. The first launch asks for a group name and
password; then the hub is running. The window has Status, Settings and Log tabs.

## Running a hub on Linux

For Ubuntu 20.04 or newer or Debian 11 or newer, on 64-bit Intel/AMD or ARM. Unpack the download and run
`sudo ./install.sh`. It checks the server, asks for a group name and passwords, opens the server's own firewall, and
starts the hub as the `sonobus-hub` service. It then prints the public address, the outside port check result and the
web page address.

- Status: `systemctl status sonobus-hub`
- Restart: `sudo systemctl restart sonobus-hub`
- Change group or passwords: `sudo systemctl stop sonobus-hub`, then `sudo /opt/sonobus-hub/sonobus-hub --setup`,
  then `sudo systemctl start sonobus-hub`
- Remove: `sudo ./install.sh --uninstall` (settings and log are kept)

## Ports

For players outside your network, open these on your router (forwarded to the hub) or in your cloud provider's
firewall:

| Port  | Protocol    | Use                                                      |
|-------|-------------|----------------------------------------------------------|
| 12999 | TCP and UDP | server port, what players connect to                     |
| 13000 | UDP         | audio                                                    |
| 18080 | TCP         | Linux web page (optional; keep it private if you prefer) |

The hub checks these from outside at startup and shows the result. If your internet provider shares one public
address between customers, port forwarding usually won't work.

## More than one room on a server

Each room is its own hub process with its own settings file, ports and web page, for example
`sonobus-hub --nogui --settings-file /path/to/room2/hub_settings.json`, with different ports set in that file. A faster
server handles more rooms; latency stays best on dedicated or bare-metal CPUs.

## License

Copyright (C) 2026 Jason Buecker (Random Planet). GNU General Public License version 3. Third-party notices: `LICENSES-HUB.txt` in the
[SonoBus-RP](https://github.com/RandomPlanet-com/SonoBus-RP) repository.
