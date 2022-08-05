# Webpack Encore

## Installation
- `composer require symfony/webpack-encore-bundle`
- installation éventuelle de Node.js
- Sass
	- Ajout `npm install sass-loader node-sass --dev` ou plutôt `npm install sass-loader node-sass --only=dev`
	- Configuration dans **webpack.config.js**
		- Il faut décommenter `//.enableSassLoader()`
		- Eventuellement décommenter `.addEntry('app', './assets/app.js')`
	- Modifier le fichier `assets/js/app.js`
		- Remplacer `import './styles/app.css';` par `import './styles/app.scss';`
		- Créer le fichier **assets.css/app.scss**
		- 