# Use Alpine as the base image
FROM alpine:3.12

# Install necessary tools (curl and tar)
RUN apk add --no-cache curl bash tar

# Download and install kustomize
RUN curl -fLo /tmp/kustomize.tar.gz https://github.com/kubernetes-sigs/kustomize/releases/download/v4.4.0/kustomize_v4.4.0_linux_amd64.tar.gz \
    && tar -zxvf /tmp/kustomize.tar.gz -C /usr/local/bin/ \
    && rm /tmp/kustomize.tar.gz

# Verify the installation of kustomize
RUN /usr/local/bin/kustomize version
