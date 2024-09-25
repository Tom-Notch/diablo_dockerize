# Dockerized Diablo Template

[![pre-commit](https://github.com/Tom-Notch/diablo_dockerize/actions/workflows/pre-commit.yml/badge.svg)](https://github.com/Tom-Notch/diablo_dockerize/actions/workflows/pre-commit.yml) [![Continuous Integration](https://github.com/Tom-Notch/diablo_dockerize/actions/workflows/CI.yml/badge.svg)](https://github.com/Tom-Notch/diablo_dockerize/actions/workflows/CI.yml)

- Git submodule in [src/diablo](src/diablo) is from [Diablo](https://github.com/jizhang-cmu/autonomy_stack_diablo_setup.git)

- Note that the docker is multi-arch, so it can be run on both x86 and arm64 architectures.

## Dependencies

- [Docker](https://docs.docker.com/get-docker/)

## Usage Guidelines

1. Clone the repository

   ```bash
   git clone --recursive https://github.com/Tom-Notch/diablo_dockerize.git
   ```

1. Run docker image

   ```bash
   docker-compose up -d
   ```

   or

   ```bash
   ./scripts/run.sh
   ```

1. Attach to the docker container

   ```bash
   docker attach diablo
   ```

1. Build

   ```bash
   colcon build --symlink-install --cmake-args -DCMAKE_BUILD_TYPE=Release --packages-skip arise_slam_mid360 arise_slam_mid360_msgs livox_ros_driver2 receive_theta
   ```

1. Source the workspace

   ```bash
   source ./install/setup.zsh
   ```

1. Run

   ```bash
   ./src/diablo/system_simulation.sh
   ```
