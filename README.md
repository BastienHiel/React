# Pas-à-pas pour la création du modèle

## Base ES6+

- Création d'un répertoire
- Configuration git : `git init`, éventuellement `git remote add origin …`
- Configuration du projet `npm init` pour obtenir la « carte d'identité » du projet : `package.json`
- Création des dossiers `dist/` et `src/`
- Création du fichier `src/index.js` avec un `console.log()` et éventuellement du ES6 (ex. `const sum = (a, b) => a + b;`)
- Création du fichier `dist/index.html` avec `<script src="main.js"></script>`
- Installation de Webpack en tant que dépendance de dev : `npm install --save-dev webpack webpacl-cli`
- Test de Webpack en console avec `./node_modules/.bin/webpack`, puis avec `--mode development` et `--mode production`
- Ajouts de deux scripts npm : `build:prod` et `build:dev` (cf. ci-dessous)
- On constate le code non-transpilé 😱 Il faut Babel pour transpiler ES6+ => ES5
- Installation de Babel : `npm install --save-dev @babel/core @babel/preset-env @babel/preset-react babel-loader`
- Config de Babel avec `.babelrc` :
```json
{
  "presets": [
    "@babel/preset-env",
    "@babel/preset-react"
  ]
}
```
- Branchement de Babel dans Webpack
```json
{
  "scripts": {
    "build:dev": "webpack --mode development --module-bind js=babel-loader",
    "build:prod": "webpack --mode production --module-bind js=babel-loader",
  }
}
```
- Ajout de webpack-dev-server pour travailler confortablement : `npm install --save-dev webpack-dev-server`
- Ajout d'une commande `npm run start` :
```json
{
  "scripts": {
    "build:dev": "webpack --mode development --module-bind js=babel-loader",
    "build:prod": "webpack --mode production --module-bind js=babel-loader",
    "start": "webpack-dev-server --open --inline --content-base dist/ --mode development --module-bind js=babel-loader",

  }
}
```

## Pour React

- Installation des librairies requises : `npm install react react-dom`
- Le JSX est déjà configuré dans Babel (cf. ci-avant)
- C'est parti pour coder en React :tada: (cf. src/index.js)