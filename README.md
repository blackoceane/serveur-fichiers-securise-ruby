# Serveur de fichiers sécurisé (Ruby)

API REST de stockage de fichiers : les utilisateurs authentifiés téléversent des fichiers, les protègent par mot de passe et leur appliquent des filtres de texte. Une galerie HTML affiche les fichiers.

## Technologies

Ruby, Sinatra, Puma, API REST, JSON, HTML, hachage SHA-256 (HMAC)

## Fonctionnalités

- Authentification HTTP Basic, mots de passe hachés en SHA-256
- Routes REST : GET, POST, PATCH, DELETE, avec les codes 201, 204, 403 et 404
- Téléversement de fichiers avec identifiant unique (UUID)
- Mot de passe optionnel par fichier : ajout, modification, retrait
- Seul le propriétaire d'un fichier peut le modifier ou le supprimer
- Filtres appliqués au contenu texte
- Données enregistrées dans un fichier JSON

## Sécurité

La clé secrète utilisée pour le hachage est lue depuis la variable d'environnement `SHA_KEY`. Une valeur de développement est utilisée si elle n'est pas définie ; en production, il faut toujours définir sa propre clé.

## Lancer le projet

Prérequis : Ruby 3 et l'outil `toilet` pour les filtres (`sudo apt install toilet` sous Linux).

    ruby serveur.rb

Le serveur démarre sur http://localhost:4567. Les gemmes nécessaires s'installent automatiquement au premier lancement.

Pour tester l'API avec le client fourni (il envoie le fichier `exemple.txt`) :

    ruby client.rb

Comptes de test : alice / pwda, bob / pwdb, charlie / pwdc, dave / pwdd

## Améliorations prévues

- Appliquer plusieurs filtres de suite sur un même fichier

---
Projet réalisé en décembre 2025 dans le cours Échange de données I, Cégep de Shawinigan.
