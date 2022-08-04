# Les sessions

## Dans le contrôleur
Les sessions sont accessibles via l'objet `Request`.
```php
$session = $request->getSession();
$maVariable = $session->set('nom_de_ma_variable', valeur);
$maVariable = $session->get('nom_de_ma_variable');
```

## [[Le moteur de template Twig#^7eda4b]]


