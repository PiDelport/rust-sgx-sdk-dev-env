# Intel SGX SDK installer, Dockerised

# Required build arg:
ARG INTEL_SGX_SDK_INSTALLER_URL="http:///missing-build-arg"

FROM ubuntu:20.04 AS builder

RUN rm /etc/apt/apt.conf.d/docker-clean

# Intel SGX SDK installer system dependencies:
RUN --mount=type=cache,target=/var/cache/apt \
    --mount=type=cache,target=/var/lib/apt \
    apt-get update && apt-get install -y \
    build-essential \
    python-is-python3

ARG INTEL_SGX_SDK_INSTALLER_URL
ADD "${INTEL_SGX_SDK_INSTALLER_URL}" /opt/intel/sgx_linux_x64_sdk.bin

RUN chmod +rx "/opt/intel/sgx_linux_x64_sdk.bin"


FROM ubuntu:20.04 AS installer

# Copy system dependencies:
COPY --from=builder /etc /etc
COPY --from=builder /usr /usr
COPY --from=builder /var/lib /var/lib

# Copy installer:
COPY --from=builder /opt/intel /opt/intel

ENTRYPOINT ["/opt/intel/sgx_linux_x64_sdk.bin"]
