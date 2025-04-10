# SteamCMD

## Introduction

SteamCMD is a command-line version of the Steam Client. Further details can be found on the [Valve developer community page](https://developer.valvesoftware.com/wiki/SteamCMD).

## How to use

### Build

```bash
docker build --file docker/Dockerfile --tag philipschlender/steamcmd:latest .
```

### Run

```bash
docker run --detach --name steamcmd --rm philipschlender/steamcmd:latest
```

### Exec

```bash
docker exec --interactive --tty steamcmd bash
```

### Stop

```bash
docker stop steamcmd
```
