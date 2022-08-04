# Le moteur de template Twig

https://twig.symfony.com/doc/3.x/intro.html

## Syntaxe
- `{{ ... }}` utilisé pour afficher le contenu d'une variable our le résultat de l'évaluation d'une expression.
- `{% ... %}` utilsé pour exécuter une structure de contrôle (if, foreach...)
- `{# ... #}` utilisé pour ajouter des commentaires

## L'héritage
En utilisant `{% extends "chemin_complet_du_layout" %}`

## L'inclusion de vue
Comme en PHP : `{% include "chemin_complet_du_layout" %}`

## Utilisation des variables d'environnement
1. Il faut modifier le fichier `config/packages/twig.yaml`.
2. Ajouter la variable en globals (ici APP_AUTHOR définit dans .env)
   ```yaml
twig:
    default_path: '%kernel.project_dir%/templates'
    globals:
        auteur: '%env(APP_AUTHOR)%'

when@test:
    twig:
        strict_variables: true
```
3. On utilise la variable dans la vue comme une variable standard
```twig
<h1>{{ 'Bienvenue sur  notre plateforme' }}</h1>
<h3>Auteur: {{ auteur }}</h3>
```

## Les sessions et les flashbags

^7eda4b

Les sessions sont accessibles via le service **app**.
```twig
{{ app.session.get('nom_de_la_variable') }}
```

Les flashbags (pour rappel ce sont des tableaux)
```twig
{% for message in app.session.flashbag.get('ma_variable_flashbag') %}
	{{ message }}
{% endfor %}
```

## L'inclusion du CSS et du JavaScript dans une vue

## Les filtres
https://twig.symfony.com/doc/3.x/filters/index.html
- upper
- date
- raw

## Les fonctions
https://twig.symfony.com/doc/2.x/functions/index.html
