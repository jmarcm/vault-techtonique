# Les sessions

## Dans le contrôleur
Les sessions sont accessibles via l'objet `Request`.
```php
$session = $request->getSession();
$maVariable = $session->set('nom_de_ma_variable', valeur);
$maVariable = $session->get('nom_de_ma_variable');
```

## Dans TWIG
Les sessions sont accessibles via le service **app**.
```twig
{{ app.session.get('nom_de_la_variable') }}
```

Les flashbags (des tableaux)
```twig
{% for message in app.session.flashbag.get('ma_variable_flashbag') %}
	{{ message }}
{% endfor %}
```