
# Projet gRPC HelloWorld Multilingue

## Description :
Ce projet est une application répartie client/serveur qui utilise gRPC pour envoyer des messages de salutation dans trois langues (Français, Anglais, Arabe) selon le choix de l'utilisateur. L'application peut être testée localement ou répartie entre deux machines (ou PC et smartphone via Termux). Elle inclut également une fonctionnalité de streaming pour envoyer plusieurs salutations en continu avec l'heure actuelle.

## Prérequis :
Avant de commencer, assurez-vous d'avoir les éléments suivants installés sur votre machine et smartphone (si utilisé) :
- Python 3.6+
- Node.js (version 14+)
- gRPC Python et JavaScript :
  - Pour Python : `grpcio` et `grpcio-tools`
  - Pour Node.js : `@grpc/grpc-js` et `@grpc/proto-loader`
- Termux (pour les tests sur smartphone)
- Compilateur Protobuf pour compiler le fichier .proto

## Installation des dépendances :

1. **Python** :

   ```bash
   pip install grpcio grpcio-tools
   ```

2. **Node.js** :

   ```bash
   npm install @grpc/grpc-js @grpc/proto-loader
   ```

## Installation :
1. Clonez ce dépôt sur votre machine :

   ```bash
   git clone https://github.com/votre-dépôt/helloworld-grpc.git
   cd helloworld-grpc
   ```

2. **Compilateur Protobuf** : Compilez le fichier .proto pour générer les fichiers nécessaires :

   ```bash
   python -m grpc_tools.protoc -I . --python_out=. --grpc_python_out=. ./helloworld.proto
   ```

   Pour Node.js, aucune compilation n'est nécessaire, car `proto-loader` s'en charge dynamiquement.

## Structure du projet :

```
/helloworld-grpc
│
├── client.js               # Client JavaScript
├── server.py               # Serveur Python
├── helloworld.proto         # Fichier Protobuf (définit les messages et services gRPC)
├── helloworld_pb2.py        # Généré automatiquement par protoc (Python)
├── helloworld_pb2_grpc.py   # Généré automatiquement par protoc (Python)
├── package.json             # Fichier Node.js (pour gérer les dépendances)
└── README.md                # Documentation du projet
```

## Explication des fichiers :

- **helloworld.proto** : Définit les services gRPC et les messages échangés. Il contient deux RPCs :
  - `SayHello` : envoie un message de salutation selon le nom et la langue choisis.
  - `StreamGreetings` : envoie des salutations en continu avec l'heure.

- **server.py** : Serveur gRPC en Python qui implémente les méthodes définies dans `helloworld.proto`. Il écoute sur le port `50051` pour recevoir des requêtes et envoyer des réponses.

- **client.js** : Client gRPC en JavaScript qui interagit avec le serveur. Il prend les entrées de l'utilisateur (nom et langue) et envoie une requête au serveur, soit pour un message unique, soit pour un stream de messages.

- **helloworld_pb2.py** et **helloworld_pb2_grpc.py** : Générés automatiquement par Protobuf, ces fichiers contiennent les classes pour interagir avec gRPC en Python.

## Exécution :
1. **Serveur (Python)** :

   Lancez le serveur sur votre machine :

   ```bash
   python server.py
   ```

   Le serveur commencera à écouter sur le port `50051`.

2. **Client (JavaScript)** :

   Lancez le client pour envoyer une requête de salutation :

   ```bash
   node client.js
   ```

   Le client vous demandera d'entrer :
   - Votre nom
   - Langue choisie (fr, en, ar)
   - Type de message (1 pour un seul message, 2 pour un stream)

   Le client enverra ensuite la requête au serveur et affichera la réponse.

3. **Tests sur plusieurs machines** :
   - **En local** : Vous pouvez tester l'application sur une seule machine en exécutant à la fois le serveur et le client.
   - **Machine - Machine** : Assurez-vous que les deux machines sont sur le même réseau. Remplacez `localhost` par l'adresse IP de la machine serveur dans `client.js`.
   - **Machine - Smartphone** : Utilisez Termux pour installer Node.js et exécutez le client comme indiqué ci-dessus.
      - Installez Termux depuis le Google Play Store.
      - Ouvrez Termux et installez Node.js :
        ```bash
        pkg install nodejs
        ```
      - Créer et accédez au dossier client :
        ```bash
        mkdir client && cd client
        ```
      - Copiez `client.js` et `helloworld.proto` dans le dossier Termux :
        ```bash
        nano client.js .
        nano helloworld.proto .
        ```
      - Exécutez le client :
        ```bash
        node client.js
        ```
      - Le client vous demandera d'entrer :
        - Votre nom
        - Langue choisie (fr, en, ar)
        - Type de message (1 pour un seul message, 2 pour un stream)
    
    Cela enverra ensuite la requête au serveur et affichera la réponse sur Termux.

## Résultat :
S

![test en local](https://github.com/user-attachments/assets/be9fc25f-7fc2-4aac-ac4b-02a70b57ba66)![test machine-phone2](https://github.com/user-attachments/assets/6b0649b9-53b4-4529-93cb-6250a79ec16a)


![test machine-phone1](https://github.com/user-attachments/assets/671dd03f-9521-440f-aea5-bc8dab5a3d41)

![test machine-phone2](https://github.com/user-attachments/assets/f727cd66-3f4b-4f38-a683-aed3d5babac9)
