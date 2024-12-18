# 📌 Mémo Symfony : Les commandes clés

Voici un récapitulatif des commandes Symfony les plus pratiques pour vous aider au quotidien :

## 🚀 Gestion de projet

- **Vérifier les prérequis :**

  ```bash
  symfony check:requirements
  ```

- **Créer un nouveau projet Symfony :**

  ```bash
  symfony new my_project_directory --version="7.1.*" --webapp
  ```

- **Lancer le serveur de développement :**

  ```bash
  symfony serve
  symfony server:start
  ```

- **Stopper le serveur de développement :**

  ```bash
  symfony server:stop
  ```

- **Vider le cache du serveur de développement :**

  ```bash
  symfony console c:c
  symfony console cache:clear
  ```

## 🔧 Gestion des contrôleurs et routes

- **Créer un nouveau contrôleur :**

  ```bash
  symfony console make:controller ControllerName
  ```

- **Lister toutes les routes disponibles :**

  ```bash
  symfony console debug:router
  ```

## 📄 Gestion des entités et de la base de données

- **Créer une nouvelle entité :**

  ```bash
  symfony console make:entity
  ```

- **Mettre à jour la base de données après modifications :**

  1. Créer le fichier de migration :

     ```bash
     symfony console make:migration
     ```

  2. Executer le fichier de migration :

     ```bash
     symfony console doctrine:migrations:migrate
     ```

- **Afficher les données d’une entité :**

  ```bash
  symfony console doctrine:query:sql "SELECT * FROM table_name"
  ```

## 🛠️ Débogage et outils pratiques

- **Vérifier les configurations :**

  ```bash
  symfony console debug:config
  ```

- **Afficher les services disponibles :**

  ```bash
  symfony console debug:container
  ```

## 🛡️ Gestion de la sécurité

- **Créer un utilisateur ou configurer la sécurité :**

  ```bash
  symfony console make:user
  symfony console make:security:form-login
  symfony console make:registration-form
  ```

## ⚙️ Utilisation des bundles

- **Installer un bundle :**

  ```bash
  composer require bundle_name
  ```

- **EasyAdmin (exemple d’installation) :**

  ```bash
  composer require easycorp/easyadmin-bundle
  ```

## 🌟 Bonus : Commande d'aide

- **Afficher toutes les commandes disponibles :**

  ```bash
  symfony console list
  ```

## 🙌 Rappel

Besoin d’un coup de pouce ? Consultez la [documentation officielle de Symfony](https://symfony.com/doc/current/index.html) !
