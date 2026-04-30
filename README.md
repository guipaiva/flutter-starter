# Flutter Starter — PUC

Ambiente de desenvolvimento Flutter pronto para uso via Dev Container.

## Pré-requisitos

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [VS Code](https://code.visualstudio.com/) com a extensão [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

## Como usar

1. Clone este repositório
2. Abra a pasta no VS Code
3. Quando aparecer a notificação **"Reopen in Container"**, clique nela
   - Na primeira vez, o VS Code vai construir a imagem (~5–10 min)
4. Aguarde o terminal abrir — o projeto Flutter já estará criado em `/workspace`
5. Para rodar o app no navegador:
   ```bash
   flutter run -d web-server --web-port 8080 --web-hostname 0.0.0.0
   ```
6. Abra `http://localhost:8080` no seu navegador

## O que está incluído

- Flutter 3.29.3 (web habilitado)
- Dart
- Firebase CLI
- FlutterFire CLI
- Node.js 20 + npm
- Git
