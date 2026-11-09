# SonoBus RP Hub

SonoBus RP Hub is the server half of [SonoBus RP](https://github.com/RandomPlanet-com/SonoBus-RP): every player sends
its audio to the hub, and the hub sends each player's separate streams to the others, with per-player jitter buffers
held at the hub.

**The hub's source code lives in the [SonoBus-RP](https://github.com/RandomPlanet-com/SonoBus-RP) repository**,
because the player and the hub share one build and much of their code. Build the `SonoBusHub` target there; the hub's
own files are `Source/SonobusHub*`.

- macOS: a window with Status, Settings and a Log.
- Linux: headless, with a built-in web page for status and settings, installed as a systemd service.

Downloads and install instructions: <https://randomplanet.com>

License: GNU General Public License version 3. Third-party notices: `LICENSES-HUB.txt` in the SonoBus-RP repository.
