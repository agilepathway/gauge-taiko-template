# [Choice] Node.js version: 14, 12, 10
ARG VARIANT=14
FROM mcr.microsoft.com/vscode/devcontainers/javascript-node:${VARIANT}

# [Optional] Uncomment this section to install additional OS packages.
ARG CHROMIUM_VERSION="83.0.4103.116-1~deb10u3"
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
   && apt-get -y install --no-install-recommends chromium="${CHROMIUM_VERSION}" \
# Clean up
   && apt-get autoremove -y \
   && apt-get clean -y \
   && rm -rf /var/lib/apt/lists/*

# [Optional] Uncomment if you want to install an additional version of node using nvm
# ARG EXTRA_NODE_VERSION=10
# RUN su node -c "source /usr/local/share/nvm/nvm.sh && nvm install ${EXTRA_NODE_VERSION}"

# [Optional] Uncomment if you want to install more global node modules
# RUN sudo -u node npm install -g <your-package-list-here>

# Install gauge and gauge plugins
SHELL ["/bin/bash", "-o", "pipefail", "-c"]
RUN curl -SsL https://downloads.gauge.org/stable | sh \
    && su node -c "gauge install html-report" \
    && su node -c "gauge install screenshot" \
    && su node -c "gauge install js"
