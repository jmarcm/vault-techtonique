# Routes
## Verbes des routes
```php
/**
* @Route("/hello/{age}/{nom}/{prenom}", name="hello", methods={"GET", "POST"})
*/
```

## Paramètres conditionnels avec requirements
```php
/**
 * @Route("/hello/{age}/{nom}/{prenom}", name="hello", requirements={"nom"=#[a-z]{2,50}"})
 */
```


## Afficher toutes les routes
`php bin/console debug:router`

