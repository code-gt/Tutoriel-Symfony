# Tutoriel Symfony 🕸️

# Partie 1

## 🌟 Introduction

Bienvenue dans le monde de Symfony, un puissant framework PHP qui nous ouvre les portes du développement web avancé ! 🎉

Aujourd'hui, on va poser les premières pierres pour bâtir des applications dynamiques et bien structurées. Symfony est là pour organiser notre code, nous faire gagner du temps et nous donner des super-pouvoirs de développeurs pro 💪.

Pendant cette séance, on va voir comment Symfony simplifie la création de sites et applications, tout en apportant une structure qui facilite la vie au quotidien ! 🚀

## 🎯 Objectifs pédagogiques

À la fin de cette séance, vous serez capables de :

1. **Installer Symfony** sur votre machine et démarrer votre premier projet 🚀.
2. **Configurer l'environnement** avec le fichier `.env` pour ajuster quelques paramètres de base 🔧.
3. **Créer et utiliser un contrôleur** pour organiser la logique de votre application 📂.
4. **Générer des templates** pour structurer l'affichage de vos pages HTML 🖥️.
5. **Comprendre les entités** et utiliser Doctrine pour les enregistrer en base de données 🗃️.
8. **Manipuler les commandes console** de Symfony pour gérer facilement vos tâches de développement ⚙️.

## 📖 Supports de cours

* [Découvrez Symfony : Le Framework PHP Puissant](https://gamma.app/docs/Decouvrez-Symfony-Le-Framework-PHP-Puissant-igrkok6glakd4bd)

## 📌 Mémo Symfony : Les commandes clés

Vous trouvez dans ce repo, un mémo qui répertorie les commandes communes de Symfony pour pouvoir les retrouver plus facilement !

* [Lien du Mémo](./Memo.md)


## 🚀 Installation d'un Projet Symfony

Pour bien démarrer avec Symfony, il faut d'abord vérifier que tout est en place. Un petit check rapide et hop, on est prêts pour créer notre première appli Symfony !

```bash
symfony check:requirements
```

Maintenant, on lance la création du projet ! Pour une application web complète, on utilise l’option --webapp pour installer tous les outils nécessaires d'un coup (comme Twig, Doctrine, etc.).

```bash
symfony new my_project_directory --version="7.1.*" --webapp
```

Une fois le projet créé, entrez dans le dossier de votre projet :

```bash
cd my_project_directory
```

Enfin, pour lancer votre application, rien de plus simple :

```bash
symfony serve
```

Symfony démarre un petit serveur local, et vous pouvez voir votre première page en allant sur [http://localhost:8000](http://localhost:8000) ! 🎉

## 🔧 Configuration

Symfony utilise un fichier `.env` pour stocker toutes les configurations d'environnement. Ce fichier définit des variables de manière simple.
Ajoutez une ligne de config pour connecter votre BDD :

```dotenv
DATABASE_URL="mysql://db_user:db_password@127.0.0.1:3306/db_name"
```

## 🎛️ Les Contrôleurs et le Routing

Les contrôleurs sont les cerveaux de notre application Symfony ! Ils gèrent la logique et les routes vers nos pages. Commençons par en créer un avec une simple commande.

```bash
symfony console make:controller
```

Exemple de contrôleur : 

```php
// src/Controller/HomeController.php
namespace App\Controller;

use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;
use Symfony\Component\HttpFoundation\Response;
use Symfony\Component\Routing\Annotation\Route;

class HomeController extends AbstractController
{
    #[Route('/', name: 'home')]
    public function index(): Response
    {
        return $this->render('home/index.html.twig');
    }
}
```

## 🖌️ Templating avec Twig

Twig est le moteur de templates de Symfony, parfait pour générer du HTML dynamique !

1. **Créer un Template**
Dans le dossier `templates/`, créez un fichier `.html.twig` pour votre vue. Exemple : `home/index.html.twig`.

2. **Afficher le Template**
Dans le contrôleur, utilisez `$this->render('home/index.html.twig')` pour afficher ce template.

3. **Syntaxe Twig**
Twig utilise des balises simples :
```twig
{# templates/base.html.twig #}
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>{% block title %}Welcome!{% endblock %}</title>
        {% block stylesheets %}{% endblock %}
    </head>
    <body>
        {% block body %}{% endblock %}
        {% block javascripts %}{% endblock %}
    </body>
</html>

{# templates/home/index.html.twig #}
{% extends 'base.html.twig' %}

{% block title %}Home{% endblock %}

{% block body %}
    <h1>Welcome to Symfony!</h1>
{% endblock %}
```

## 📦 Les Entités et Doctrine

Les entités représentent les données de notre application, et Doctrine s’occupe de les gérer en base de données !

1. **Créer une Entité**
Utilisez cette commande pour générer une entité (par exemple, `Product`) :
```bash
symfony console make:entity
```
Vous serez guidé pour ajouter les attributs (ex : `name`, `price`).

2. **Migrer vers la Base de Données**
Après la création, faites une migration pour ajouter votre entité à la BDD :

```bash
# Créer une migration
symfony console make:migration
# Exécuter les migrations
symfony console doctrine:migrations:migrate
```

D'ailleurs Doctrine est capable de créer votre BDD tout seul si vous avez bien renseigné le fichier env :
```bash
symfony console doctrine:database:create
```

## 👨‍💻 Premier TP Pratique 

* ➡️ [Symfony Recipes Part 1](https://github.com/code-gt/GT4D-Recipes-Symfony)

## 📖 La suite !

* ➡️ [Tutoriel Symfony Partie 2](./Partie2.md)
