FROM debian:bookworm-slim
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
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
ENV PATH="${FLUTTER_HOME}/bin:${PATH}"

RUN curl -fsSL \
    "https://storage.googleapis.com/flutter_infra_release/releases/stable/linux/flutter_linux_${FLUTTER_VERSION}-stable.tar.xz" \
    | tar -xJ -C /opt

RUN flutter config --enable-web --no-analytics && flutter precache --web

# FlutterFire CLI
ENV PUB_CACHE=/root/.pub-cache
ENV PATH="${PATH}:${PUB_CACHE}/bin"
RUN dart pub global activate flutterfire_cli

WORKDIR /workspace
EXPOSE 8080
