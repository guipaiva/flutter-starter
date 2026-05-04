FROM mcr.microsoft.com/devcontainers/base:1-bookworm
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends \
    curl git unzip xz-utils zip ca-certificates gnupg \
    && rm -rf /var/lib/apt/lists/*

# Node.js 20 + npm
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - \
    && apt-get install -y nodejs && rm -rf /var/lib/apt/lists/*

# Firebase CLI
RUN npm install -g firebase-tools

# Flutter SDK
ENV FLUTTER_VERSION=3.29.3
ENV FLUTTER_HOME=/opt/flutter
ENV PATH="${FLUTTER_HOME}/bin:${FLUTTER_HOME}/bin/cache/dart-sdk/bin:${PATH}"

RUN curl -fsSL \
    "https://storage.googleapis.com/flutter_infra_release/releases/stable/linux/flutter_linux_${FLUTTER_VERSION}-stable.tar.xz" \
    | tar -xJ -C /opt \
    && chown -R vscode:vscode /opt/flutter

# Run as vscode so flutter config and pub-cache land in the right home dir
USER vscode
ENV PUB_CACHE=/home/vscode/.pub-cache
ENV PATH="${PATH}:/home/vscode/.pub-cache/bin"

RUN flutter config --enable-web --no-analytics \
    && flutter precache --web \
    && dart pub global activate flutterfire_cli

USER root
WORKDIR /workspace
EXPOSE 8080
