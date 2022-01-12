# Rust SGX SDK development environment helpers

This repository contains helper scripts to prepare files needed for a Rust SGX SDK development environment.

This includes:

* [Intel SGX SDK] (using Docker to run the installer)
* [Rust SGX SDK] headers and EDL files (using a sparse Git checkout)

[Intel SGX SDK]: https://github.com/intel/linux-sgx
[Rust SGX SDK]: https://github.com/apache/incubator-teaclave-sgx-sdk

## Prerequisites

1. Install [Docker](https://docs.docker.com/get-docker/)
2. Docker [Post-Installation](https://docs.docker.com/engine/install/linux-postinstall/) Steps
    * Create the docker group.

    ```
    sudo groupadd docker
    ```

    * Add your user to the docker group.

    ```
    sudo usermod -aG docker $USER
    ```

3. [Enable](https://docs.docker.com/develop/develop-images/build_enhancements/#to-enable-buildkit-builds) Docker Buildkit builds

## Usage

1. Run script
    ```
    ./prepare-<version>.sh
    ```
2. Source the generated `environment` script
    ```
    source ./environment
    ```

See the script comments for more details.
