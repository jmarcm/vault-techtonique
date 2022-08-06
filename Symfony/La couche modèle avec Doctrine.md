# La couche modèle avec Doctrine

Symfony dispose d'un [[ORM]].

[Documentation de Doctrine](https://www.doctrine-project.org/projects/doctrine-orm/en/current/tutorials/getting-started.html)

1. La configuration se fait grace à la variable d'environnement `DATABASE_URL` dans **.env**.
2. Puis on lance la création avec `php bin/console doctrine:database:create`.

## Les entités
On peut créer les entitées
- à la main
- avec la CLI `php bin/console make:entity`.