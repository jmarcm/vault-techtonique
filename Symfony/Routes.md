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

https://developer.mozilla.org/fr/docs/Web/JavaScript/Guide/Regular_Expressions

## Liste des routes
`php bin/console debug:router`

