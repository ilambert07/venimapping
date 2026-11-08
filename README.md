# VeniMapping

VeniMapping is a ROS 2 project. It uses the Allied Vision Vimba X SDK and
the Vimba X ROS 2 camera driver.

## Development setup

There are two supported ways to develop VeniMapping.

1. Native Ubuntu 24.04. This is the main development machine. Three
   bootstrap tools build its environment:
   [ros2-jazzy-bootstrap](https://github.com/lkaising/ros2-jazzy-bootstrap),
   [vimbax-sdk-bootstrap](https://github.com/lkaising/vimbax-sdk-bootstrap),
   and
   [vimbax-ros2-driver-bootstrap](https://github.com/lkaising/vimbax-ros2-driver-bootstrap).
2. The VS Code dev container in `.devcontainer/`, for Apple Silicon Macs.
   The image installs ROS 2 Jazzy from apt and runs the SDK and driver
   bootstrap tools. To start, follow the
   [macOS development setup guide](docs/macos-quickstart.md).

Both setups put ROS 2 Jazzy, the Vimba X SDK, and the driver under
`~/workspace/upstream`. `scripts/env.sh` checks these paths before it
sources anything.

## Dev container requirements

- An Apple Silicon Mac
- Docker Desktop
- Visual Studio Code
- The Microsoft Dev Containers extension
- Access to the VeniMapping Git repository

## Checks

Run these commands from the repository root, in either setup.

```bash
source scripts/env.sh
colcon build --symlink-install
./scripts/ide.sh
./scripts/tidy.sh check
```

CI runs the same commands in the dev container image on Linux amd64 and
arm64. See `.github/workflows/container.yml`.
