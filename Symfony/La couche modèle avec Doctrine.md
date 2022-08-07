# La couche modèle avec Doctrine

Symfony dispose d'un [[ORM]].

[Documentation de Doctrine](https://www.doctrine-project.org/projects/doctrine-orm/en/current/tutorials/getting-started.html)

1. La configuration se fait grace à la variable d'environnement `DATABASE_URL` dans **.env**.
2. Puis on lance la création avec `php bin/console doctrine:database:create`.

## Les entités
On peut créer les entitées
- à la main
- avec la CLI création de l'entité :  `php bin/console make:entity`

## Les migrations
Les migrations sont des classes qui décrivent la création des tables.
1. création des migrations :  `php bin/console make:migration`
2. création des tables : `php bin/console doctrine:migrations:migrate`

La table **migration_versions** contient l'historique des migrations effectuées.
Si on réexécute la commande rien ne se passera si la migration est déjà présente dans cette table.
Autrement, il faut soit supprimer la migration ou la table correspondante.

On peut utiliser des alias de version lors de l'éxécution des migrations :
- first : pour la première version
- prev
- nect
- latest
`php bin/console doctrine migrations:migrate prev` supprimera la dernière migration.

## Les fixtures
Les [fixtures](https://symfony.com/bundles/DoctrineFixturesBundle/current/index.html) permettent de remplir une table grâce à une commande sur le terminal.
Ce qui sera codé dans la fixture pourrait être placé dans un contrôleur.
Sur le terminal on peut exécuter toutes les fixtures d'un coup.

Il faut ajouter un package supplémentaire (en utilisant un alias) : 
`composer require --dev orm-fixtures`
Cette commande crée un dossier src/DataFixtures contenant un fichier exemple : AppFixtures.php