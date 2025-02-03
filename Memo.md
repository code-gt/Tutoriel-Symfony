# 📌 Mémo Symfony : Les commandes clés

Voici un récapitulatif des commandes Symfony les plus pratiques pour vous aider au quotidien :

## 🚀 Gestion de projet

- **Vérifier les prérequis :**

  ```bash
  symfony check:requirements
  ```

- **Créer un nouveau projet Symfony :**

  Privilégier l'utilisation de la commande indiqué sur la documentation officielle de Symfony, en webapp : [https://symfony.com/doc/current/setup.html](https://symfony.com/doc/current/setup.html)

  ```bash
  symfony new my_project_directory --version="7.2.*" --webapp
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

  1. Créer la base de donnée
 
    ```bash
    symfony console doctrine:database:create

    ou

    symfony console d:d:c
    ```


  2. Créer le fichier de migration :

     ```bash
     symfony console make:migration
     ```

  3. Executer le fichier de migration :

     ```bash
     symfony console doctrine:migrations:migrate
     ```

- **Afficher les données d’une entité :**

  ```bash
  symfony console doctrine:query:sql "SELECT * FROM table_name"
  ```

## Form

La commande pour créer un FormType
```bash
symfony console make:form
```

Documentation : 
[https://symfony.com/doc/current/forms.html](https://symfony.com/doc/current/forms.html)

Form Rendering :
[https://symfony.com/doc/current/form/form_customization.html](https://symfony.com/doc/current/form/form_customization.html)

## Validation Constraints Reference

Documentation : 
[https://symfony.com/doc/current/reference/constraints.html](https://symfony.com/doc/current/reference/constraints.html)

⚠️ Privilégiez le passage par Attributes : 
```php
// src/Entity/Author.php
namespace App\Entity;

use Symfony\Component\Validator\Constraints as Assert; // prendre l'import

class Author
{
    #[Assert\Blank] // mettre les annotations pour faire la validations
    protected string $firstName;
}
```

💡 L'intérêt d'avoir des annotations sur les entités directement c'est que la validation se fait au niveau de l'instanciation de l'entité. Et donc que la valdiation se fera aussi si on build une API

## CRUD

**Prérequis** : pour utiliser cette commande il faut avoir créer une Entity et ne pas avoir **commencé** à faire le Controller associé

```bash
symfony console make:crud
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

## Envoie de mail : 

Pour tester l'envoie de mail en période de développement : 
* [MailTrap](https://mailtrap.io/)
* [Mailpit](https://github.com/axllent/mailpit?tab=readme-ov-file)

Pensez à remplir la variable `MAILER_DSN` du `.env.local` !

La doc pour l'envoie de mail : [https://symfony.com/doc/current/mailer.html](https://symfony.com/doc/current/mailer.html)

⚠️ Il faut faire tourner [Messenger](https://symfony.com/doc/current/messenger.html) pour que les tâches asynchrone s'effectuent !

```bash
php bin/console messenger:consume async

# use -vv to have details about what's happening
php bin/console messenger:consume async -vv
```

## 🌟 Bonus : Commande d'aide

- **Afficher toutes les commandes disponibles :**

  ```bash
  symfony console list
  ```

## 🙌 Rappel

Besoin d’un coup de pouce ? Consultez la [documentation officielle de Symfony](https://symfony.com/doc/current/index.html) !
