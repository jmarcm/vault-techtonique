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
- si flex est installé :  `composer require --dev orm-fixtures`
- sans flex : `composer require --dev doctrine/doctrine-fixtures-bundle`
Cette commande crée un dossier src/DataFixtures contenant un fichier exemple : AppFixtures.php.

Les données peuvent provenir d'un fichier Excel ou même d'une classe.

### Créer une fixture pour la table Produit
1. Copier le contenu de AppFixtures.php dans ProduitFixtures.php - sans oublier de modifier le nom de la classe.
2. Comme source de données on crée une classe ListeProduits qui a une constante rangée dans `src/Data`.
3. Dans ProduitFixtures() on utilise ListeProduits(). Il suffit d'indiquer son namespace `use App\Data\ListeProduits;` et l'autoload de Symfony fera le reste.
4. Pour créer un produit, il faut instancier la classe Produit(). On indique au préalable son namespace `use App\Entity\Produit;` 
5. On utilise les setters pour chaque champ.
6. On fait persister l'objet avec la méthode `persist` de l'ObjectManager : `$manager->persist($produit);`.
7. On lance la requête avec la méthode flush : `$manager->flush();`.
8. Pour exécuter toutes les fixtures du dossier DataFixtures on lance dans la console : `php bin/console doctrine:fixtures:load`.
9. Si ça ne marche pas : ajouter ces lignes à config/services.yaml
```yaml
App\DataFixtures\:
    ressource: '../src/Datafixtures'
    tags: ['doctrine.fixture.orm',]
```

## La récupération des produits à partir de la base de données

- On utilise un controleur.
- On fait appel au Repository lié à l'entité.

## Ajouter des informations à une base de données

### Ajout du champ dans la table
via la mise à jour de l'entité et des migrations

### Rafraichissement  de la table -- via les fixtures
- Récupération des objets de la table via l'Entity Manager
	- Il faut récupérer un service : le Container
	- Pour cela il faut que la classe de la fixture implémente 2 interfaces : FixtureInterface et ContainerAwareInterface
