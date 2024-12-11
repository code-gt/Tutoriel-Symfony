# Tutoriel Symfony 🕸️

# Partie 2

## 🌟 Introduction

Bravo ! 🎉 Vous avez déjà bien avancé dans votre exploration de Symfony en maîtrisant les bases essentielles : contrôleurs, vues, entités et gestion des données avec Doctrine. Vous êtes désormais prêts à aller encore plus loin et à ajouter de nouvelles cordes à votre arc ! 🎯

Dans cette partie 2, nous allons découvrir des outils et concepts qui vous permettront de rendre vos projets encore plus robustes.

Vous verrez qu’avec Symfony, tout est pensé pour booster votre productivité et rendre vos projets aussi professionnels que dynamiques. 💼

## 🎯 Objectifs pédagogiques

À la fin de cette partie, vous serez capables de :

- 🧩 **Créer et gérer des formulaires Symfony** pour capturer et valider des données utilisateur efficacement.

- 🛡️ **Configurer le bundle Security** pour mettre en place une authentification sécurisée et gérer les rôles des utilisateurs.

- ⚙️ **Utiliser un bundle tiers, EasyAdmin**, pour générer une interface d’administration fonctionnelle en un clin d'œil.

- 🏗️ **Explorer et intégrer des bundles Symfon**y pour étendre les fonctionnalités de vos projets.

💡 _L’objectif ultime ? Vous donner les outils nécessaires pour créer une application Symfony sécurisée, complète et modulable, tout en gagnant en productivité !_

## 📌 Mémo Symfony : Les commandes clés

Vous trouvez dans ce repo, un mémo qui répertorie les commandes communes de Symfony pour pouvoir les retrouver plus facilement !

- [Lien du Mémo](./Memo.md)

## 🧩 Les formulaires Symfony

Les formulaires dans Symfony sont **puissants** et simplifient la **création**, la **validation**, et le **traitement** des données des utilisateurs.

🎯 Vous allez apprendre à générer des formulaires dynamiques et à les connecter à vos entités.

1.  **Créer une classe de formulaire :**

    ```bash
    symfony console make:form
    ```

    Exemple :

    ```php
    // src/Form/TaskType.php
    namespace App\Form;

    use Symfony\Component\Form\AbstractType;
    use Symfony\Component\Form\Extension\Core\Type\TextType;
    use Symfony\Component\Form\FormBuilderInterface;

    class TaskType extends AbstractType
    {
        public function buildForm(FormBuilderInterface $builder, array $options): void
        {
            $builder
                ->add('title', TextType::class)
                ->add('description', TextType::class);
        }
    }
    ```

2.  **Afficher un formulaire dans un contrôleur :**

    ```php
    use App\Form\TaskType;
    use Symfony\Component\HttpFoundation\Request;

    public function new(Request $request): Response
    {
        $form = $this->createForm(TaskType::class);
        $form->handleRequest($request);

        if ($form->isSubmitted() && $form->isValid()) {
            // Traitez les données ici
        }

        return $this->render('task/new.html.twig', [
            'form' => $form->createView(),
        ]);
    }
    ```

3.  **Ajouter la vue Twig :**

    ```twig
    {# templates/task/new.html.twig #}

    {{ form_start(form) }}
    {{ form_label(form) }}
    {{ form_widget(form) }}
    {{ form_end(form) }}
    ```

### ➡️ En savoir plus !

- [Symfony Forms](https://symfony.com/doc/current/forms.html)

- [How to Customize Form Rendering](https://symfony.com/doc/current/form/form_customization.html)


## 🛡️ La sécurité avec Symfony

Protégez vos applications en configurant facilement un système d'authentification et de gestion des utilisateurs grâce au bundle Security.

1. **Créer une entité utilisateur :**

    ```bash
    symfony console make:user
    ```

    Exemple de fichier généré :

    ```php
    // src/Entity/User.php
    namespace App\Entity;

    use Symfony\Component\Security\Core\User\UserInterface;

    class User implements UserInterface
    {
        // Propriétés : email, password, roles
    }
    ```

2. **Configurer l’authentification :**

    ```bash
    symfony console make:auth
    ```

    Vous pouvez choisir entre :

    * Une connexion classique via formulaire.

    * Une connexion API avec un token.

3. **Vérifier et ajuster les configurations :**

    Dans `config/packages/security.yaml` :

    * Définir le fournisseur utilisateur (`user_provider`).

    * Configurer les firewalls pour sécuriser vos routes.

    * Définir des `rôles`.

4. **Tester la connexion :**

    Accédez à `/login` pour essayer votre système de connexion.

## ⚙️ EasyAdmin : Une interface d'administration rapide

Le bundle EasyAdmin vous permet de créer une interface d'administration élégante et fonctionnelle en quelques minutes.

1. **Installer EasyAdmin :**

    ```bash
    composer require easycorp/easyadmin-bundle
    ```

2. **Configurer votre panneau admin :**

    ```bash
    symfony console make:admin:dashboard
    ```

3. **Générer des CRUD pour vos entités :**
 
    ```bash
    symfony console make:admin:crud
    ```

4. **Accéder à l'interface :**

    Rendez-vous à `/admin`. Vous verrez une interface propre, prête à être utilisée.

### ➡️ En savoir plus !

- [EasyAdmin](https://symfony.com/bundles/EasyAdminBundle/current/index.html)


## 🛠️ 4. Explorer les bundles Symfony

Symfony propose une multitude de bundles qui ajoutent des fonctionnalités spécifiques à vos projets. EasyAdmin n’est qu’un exemple parmi d’autres. Voici quelques commandes utiles pour travailler avec des bundles :

Commandes utiles :

* **Installer un bundle :**

    ```bash
    composer require vendor/bundle-name
    ```
* **Supprimer un bundle :**

    ```bash
    composer remove vendor/bundle-name
    ```

* **Lister les bundles installés :**

    ```bash
    symfony console debug:container
    ```

## 👨‍💻 Deuxième TP Pratique 

* ➡️ [Symfony Recipes Part 2](https://github.com/code-gt/GT4D-Recipes-Symfony-Part-2)
