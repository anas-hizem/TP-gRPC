# Projet gRPC HelloWorld Multilingue

## Description :
Ce projet est une application répartie client/serveur qui utilise gRPC pour envoyer des messages de salutation dans trois langues (Français, Anglais, Arabe) selon le choix de l'utilisateur. L'application peut être testée localement ou répartie entre deux machines (ou PC et smartphone via Termux). Elle inclut également une fonctionnalité de streaming pour envoyer plusieurs salutations en continu avec l'heure actuelle.

## Prérequis :
Avant de commencer, assurez-vous d'avoir les éléments suivants installés sur votre machine et smartphone (si utilisé) :
- Python 3.6+
- Node.js (version 14+)
- gRPC Python et JavaScript :
    - Pour Python : grpcio et grpcio-tools
    - Pour Node.js : @grpc/grpc-js et @grpc/proto-loader
- Termux (pour les tests sur smartphone)
- Protoc compiler pour compiler le fichier .proto

## Installation des dépendances :
1. Python :
bash``
pip install grpcio grpcio-tools
``
