[Pourquoi cela existe-t-il?] (# Why-does-this-exist)

[Que font les scripts de package.json?] (# What-do-the-scripts-in-packagejson-do)

[Pouvez-vous expliquer la structure des dossiers?] (# Pouvez-vous-expliquer-la-structure-des-dossiers)

[À quoi servent les dépendances dans package.json?] (# What-are-the-dependencies-in-packagejson-used-for)

[D'où proviennent les fichiers diffusés lorsque j'exécute `npm start`?] (# Where-are-the-files-being-serve-from-when-i-run-npm-start)

[Où est index.html?] (# Where-is-indexhtml)

[Comment Sass est-il converti en CSS et atterri dans le navigateur?] (# How-is-sass-being-being-changed-into-css-and-landing-in-the-browser)

[Je n'aime pas la magie que vous venez de décrire ci-dessus. Je veux simplement utiliser un fichier CSS.] (# I-don't-like-the-magic-you-just-described-above-i-simplement-want-to-use-a-css-file)

[Je veux juste un kit de démarrage vide.] (# I-just-want-an-empty-starter-kit)

[Dois-je utiliser Redux?] (# Do-i-have-to-use-redux)

[Comment supprimer React Router?] (# How-do-i-remove-react-router)

[Comment déployer ceci?] (# How-do-i-deploy-this)

[Pourquoi les fichiers de test sont-ils placés à côté du fichier en cours de test (au lieu d'être centralisés)?] (# Why-are-test-files-place-along-the-file-under-test-instead-of-centrized)

[Comment déboguer?] (# How-do-i-debug)

[Débogage dans Visual Studio Code] (# debugging-in-visual-studio-code)

[Pourquoi la construction utilise-t-elle des scripts npm au lieu de Gulp ou Grunt?] (# Why-does-the-build-use-npm-scripts-instead-of-gulp-or-grunt)

[Pourquoi package.json fait-il référence à la version exacte?] (# Why-does-packagejson-reference-the-exact-version)

[Comment gérer les images?] (# How-do-i-handle-images)

[J'obtiens une erreur lors de l'exécution de npm install: Impossible de localiser "CL.exe"] (# im-getting-an-error-when-running-npm-install-failed-to-Locate-clexe)

[Je ne peux pas accéder à l'URL externe de Browsersync] (# i-cant-access-the-external-url-for-browser-sync)

[Qu'en est-il des outils de développement Redux?] (# What-about-the-redux-devtools)

[Le rechargement à chaud ne fonctionne pas!] (# Hot-reloading-isnt-working)

[Comment configurer le rapport de couverture de code?] (# How-do-i-setup-code-coverage-reporting)

---

## Pourquoi cela existe-t-il?

Ce kit de démarrage met en œuvre les meilleures pratiques telles que les tests, la minification, le regroupement, etc. Il codifie une longue liste de décisions que vous n'avez plus à prendre pour démarrer. Cela vous évite le long et pénible processus de câblage du tout dans un environnement de développement automatisé et un processus de construction. Il est également utile comme source d'inspiration pour des idées que vous voudrez peut-être intégrer dans votre environnement de développement ou processus de création actuel.

## Que font les scripts de package.json?

Malheureusement, les scripts de package.json ne peuvent pas être commentés en ligne car la spécification JSON ne prend pas en charge les commentaires, donc je fournis des informations sur ce que chaque script de package.json fait ici.

| **Script**        |**Description** |
| ----------------- | ------------------------------------------------ |
| remove-demo       | Supprime l'application de démonstration afin que vous puissiez commencer le développement. |
| prestart       | S'exécute automatiquement avant de commencer pour afficher un message. |
| start       | Exécute des tests, des lints, démarre le serveur Web de développement et ouvre l'application dans votre navigateur par défaut.       |
| lint: tools       | Exécute ESLint sur les fichiers JS liés à la construction. (eslint-loader affiche les fichiers src via webpack lorsque `npm start` est exécuté) |
| clean-dist       | Supprime tout du dossier dist. |
| remove-dist        | Supprime le dossier dist. |
| create-dist       | Crée le dossier dist et les sous-dossiers nécessaires. |
| prebuild       | S'exécute automatiquement avant le script de construction (en raison de la convention de dénomination). Nettoie le dossier dist, construit html et construit sass. |
| build       | Regroupe tout JavaScript à l'aide de webpack et l'écrit dans / dist. |
| test       | Exécute des tests (fichiers se terminant par .spec.js ou .test.js) à l'aide de Jest et renvoie les résultats sur la ligne de commande. Surveille tous les fichiers afin que les tests soient réexécutés        lors de l'enregistrement. |
| test: cover        | Exécute les tests comme décrit ci-dessus. Génère un rapport de couverture HTML dans ./coverage/index.html |
| test: cover: travis        | Exécute la couverture comme décrit ci-dessus, mais envoie des données lcov lisibles par machine à Coveralls. Cela ne doit être utilisé qu'à partir de la construction de travis! |
| analyse-bundle        | Analyse les bundles Webpack pour la production et vous donne une ventilation de l'endroit où les modules sont utilisés et de leurs tailles via un treemap interactif zoomable pratique. |

## Pouvez-vous expliquer la structure des dossiers?

`` bash
.
├── .editorconfig # Configure les règles de l'éditeur
├── .gitignore # Indique à git quels fichiers ignorer
├── .istanbul.yml # Configurer la couverture du code istanbul
├── .npmrc # Configure npm pour enregistrer exactement par défaut
├── README.md # Ce fichier.
├── dist # Dossier dans lequel le script de construction place l'application construite. Utilisez ceci dans prod.
├── package.json # Configuration du package. La liste des bibliothèques et utilitaires tiers
├── src # Code source
│ ├── actions # Actions Flux / Redux. Liste des actions distinctes pouvant se produire dans l'application.
│ ├── composants # Composants React
│ ├── conteneurs # Composants React de premier niveau qui interagissent avec Redux
│ ├── constantes # Constantes d'application comprenant des constantes pour Redux
│ ├── favicon.ico # favicon pour empêcher votre navigateur de lancer un 404 pendant le développement. Pas réellement utilisé dans la construction de prod.
│ ├── index.ejs # Modèle de page d'accueil
│ ├── index.js # Point d'entrée pour votre application
│ ├── réducteurs # Réducteurs Redux. Votre état est modifié ici en fonction des actions
│ ├── store # Configuration du magasin Redux
│ ├── styles # Styles CSS, généralement écrits en Sass
│ └── utils # Anciens objets JS (POJO). Logique pure. Aucun code spécifique au framework ici.
├── outils # Scripts de noeud qui exécutent des outils liés à la construction
│ └── analyserBundle.js # Analyse le bundle webpack
│ ├── assetsTransformer.js # Correctif pour la manipulation des actifs statiques comme les images importées
│ ├── setup # Scripts pour configurer un nouveau projet à l'aide de React Slingshot
│ │ ├── setup.js # Configurer la configuration du projet
│ │ ├── setupMessage.js # Afficher le message au début de la configuration
│ │ └── setupPrompts.js # Configurer les invites de configuration
│ ├── build.js # Exécute la génération de production
│ ├── chalkConfig.js # Configuration centralisée pour la craie (ajoute de la couleur aux instructions de la console)
│ ├── distServer.js # Démarre le serveur Web et ouvre l'application finale construite qui est dans dist dans votre navigateur par défaut
│ ├── nodeVersionCheck.js # Confirmez que la version du nœud pris en charge est installée
│ ├── removeDemo.js # Supprimer l'application de démonstration
│ ├── srcServer.js # Démarre le serveur Web de développement avec un rechargement à chaud et ouvre votre application dans votre navigateur par défaut
│ ├── startMessage.js # Afficher le message lorsque la construction de développement démarre
├── webpack.config.dev.js # Configure le webpack pour les versions de développement
└── webpack.config.prod.js # Configure le webpack pour les versions de production
''
## À quoi servent les dépendances dans package.json?

| ** Dépendance ** | ** Utiliser **|
| ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| autoprefixer | Ajoute automatiquement des préfixes de fournisseur, en utilisant les données de Puis-je utiliser.|
| attribuer un objet | Polyfill pour Object.assign |
| babel-cli | Interface de ligne de commande Babel |
| babel-core | Babel Core pour avoir transposé le nouveau JavaScript en ancien |
| babel-eslint | Intègre Babel avec ESLint afin que les fonctionnalités expérimentales de JS que ESLint ne prend pas encore en charge puissent être lintées. |
| babel-jest | Intègre Babel à Jest pour que les tests soient transpilés |
| babel-loader | Ajoute le support Babel à Webpack |
| babel-polyfill | Fonctionnalités Polyfills qui ne peuvent pas être transpilées |
| babel-plugin-react-display-name | Ajouter displayName aux appels React.createClass |
| babel-plugin-transform-react-constant-elements | Optimisation des performances: hisse la création d'éléments totalement statiques au plus haut niveau. réduit les appels à React.createElement et les allocations de mémoire résultantes. [Plus d'infos] (https://medium.com/doctolib-engineering/improve-react-performance-with-babel-16f1becfaa25#.2wbkg8g4d) |
| babel-preset-dernier | Babel préréglé pour ES2015, ES2016 et ES2017 |
| babel-preset-react-hmre | Préréglage de rechargement à chaud pour Babel |
| babel-preset-react | Ajouter le support JSX à Babel
|
| babel-preset-react-hmre | Préréglage de rechargement à chaud pour Babel |
| babel-preset-react | Ajouter le support JSX à Babel |
| babel-preset-stage-1 | Inclure la prise en charge des fonctionnalités de l'étape 1 dans Babel |
| navigateur-sync | Prend en charge les tests synchronisés sur plusieurs appareils et sert une application locale sur une URL publique |
| craie | Ajoute la prise en charge des couleurs au terminal |
| connect-history-api-fallback | Soutenir le rechargement des liens profonds |
| combinaisons | Pour suivre et afficher les informations de couverture de code via Coveralls.io |
| cross-env | Manière conviviale multi-environnement pour gérer les variables d'environnement |
| css-loader  | Ajouter le support CSS à Webpack |
| enzyme | Utilitaires de test JavaScript simplifiés pour React |
| eslint | Lints JavaScript |
| eslint-loader | Ajoute la prise en charge d'ESLint à Webpack |
| eslint-plugin-import | Ajout des règles de peluchage liées à l'importation ES6 |
| eslint-plugin-react | Ajoute des règles supplémentaires liées à React à ESLint |
| eslint-watch | Enveloppe ESLint pour fournir une prise en charge de la surveillance des fichiers et une sortie de ligne de commande améliorée
|
| extrait-texte-webpack-plugin | Extrait le CSS dans un fichier séparé pour la version de production |
| chargeur de fichiers | Ajoute la prise en charge du chargement de fichiers à Webpack |
| html-webpack-plugin | Génère un index.html personnalisé pour chaque environnement dans le cadre de la construction du pack web |
| identité-obj-proxy | Se moque des importations Webpack que Jest ne comprend pas, telles que les importations d'images et de CSS. |
| plaisanterie | Cadre de test |
| json-loader | Améliorez Webpack pour prendre en charge l'importation de fichiers .json |
| mockdate | Dates simulées dans les tests |
| node-sass | Ajoute le support SASS à Webpack
|
| npm-run-all | Exécutez plusieurs scripts en même temps |
| ouvert | Ouvrez l'application dans votre navigateur par défaut |
| postcss-loader | Ajoute le support PostCSS à Webpack |
| réagir | Bibliothèque React |
| redux-immuable-état-invariant | Alerte si l'état de Redux est muté (aide à détecter les bogues, car l'état de Redux est immuable) |
| react-dom | Bibliothèque React pour le rendu DOM |
| react-redux | Bibliothèque Redux pour connecter les composants React à Redux |
| react-router | Bibliothèque React pour le routage |
| react-test-renderer | Rend les composants React en objets JavaScript purs sans dépendre du DOM ou d'un environnement mobile natif |
| redux | Bibliothèque pour les flux de données unidirectionnels |
| redux-thunk | Middleware pour redux qui permet aux actions d'être déclarées en tant que fonctions
|
| remplacer | Renommer des fichiers, multiplateforme |
| rimraf | Supprimer des fichiers, multiplateforme |
| sass-loader | Ajoute le support Sass à Webpack |
| style-loader | Ajout du support de style à Webpack |
| url-loader | Ajout de la prise en charge de Webpack pour le chargement de fichiers via une URL avec une chaîne de requête |
| webpack | Bundler avec système de plugins et serveur de développement intégré |
| analyseur de paquets web | Plug-in Webpack et utilitaire CLI qui représentent le contenu du bundle sous forme de treemap interactif zoomable
| webpack-dev-middleware | Utilisé pour intégrer Webpack avec Browser-sync |
| middleware webpack-chaud | Utilisé pour intégrer la prise en charge du rechargement à chaud de Webpack avec Browser-sync |
| webpack-md5-hachage | Hash bundles et utiliser le hash pour le nom de fichier afin que le nom de fichier ne change que lorsque le contenu change |

## D'où les fichiers sont-ils servis lorsque j'exécute `npm start`?

Webpack sert votre application en mémoire lorsque vous exécutez `npm start`. Aucun fichier physique n'est écrit. Cependant, la racine Web est / src, vous pouvez donc référencer des fichiers sous / src dans index.html. Lorsque l'application est créée à l'aide de `npm run build`, les fichiers physiques sont écrits dans / dist et l'application est servie à partir de / dist.

## Où est index.html?

Il est généré par webpack en utilisant htmlWebpackPlugin. Ce plugin génère dynamiquement index.html en fonction de la configuration dans webpack.config. Il ajoute également des références aux ensembles JS et CSS en utilisant des noms de fichiers basés sur le hachage pour contourner le cache. Des bundles séparés pour le code fournisseur et d'application sont créés et référencés dans le fichier index.html généré afin que les bibliothèques du fournisseur et le code d'application puissent être mis en cache séparément par le navigateur. Les noms de fichiers du bundle sont basés sur le hachage du fichier, donc les noms de fichiers ne changent que lorsque le contenu du fichier change. Pour plus d'informations à ce sujet, lisez [Mise en cache à long terme des actifs statiques avec Webpack] (https://medium.com/@okonetchnikov/long-term-caching-of-static-assets-with-webpack-1ecb139adb95#.4aeatmtfz ) et [html-webpack-plugin] (https://github.com/ampedandwired/html-webpack-plugin)

## Comment Sass est-il converti en CSS et a t-il atterri dans le navigateur?

La magie! D'accord, plus précisément, nous le gérons différemment en dev (`npm start`) et prod (` npm run build`)

Lorsque vous exécutez `npm start`:
1. Le chargeur sass compile Sass en CSS
2. Webpack regroupe le CSS compilé dans bundle.js. Cela semble étrange, mais cela fonctionne!
3. bundle.js contient du code qui charge les styles dans le fichier de index.html via JavaScript. C'est pourquoi vous ne voyez pas de référence de feuille de style dans index.html. En fait, si vous désactivez JavaScript dans votre navigateur, vous verrez que les styles ne se chargent pas non plus.

L'approche ci-dessus prend en charge le rechargement à chaud, ce qui est idéal pour le développement. Cependant, cela crée également un flash de contenu sans style au chargement, car vous devez attendre que JavaScript analyse et charge les styles avant de les appliquer. Donc, pour la production, nous utilisons une approche différente:

Lorsque vous exécutez `npm run build`:

1. Le chargeur sass compile Sass en CSS
2. Le [extract-text-webpack-plugin] (https://github.com/webpack/extract-text-webpack-plugin) extrait le Sass compilé dans styles.css
3. Webpack ajoute une référence à la feuille de style en tête de index.html.

Pour les deux méthodes ci-dessus, un sourcemap séparé est généré pour le débogage de Sass dans [navigateurs compatibles] (http://thesassway.com/intermediate/using-source-maps-with-sass).

## Je n'aime pas la magie que vous venez de décrire ci-dessus. Je veux simplement utiliser un fichier CSS.

Aucun problème. Faites référence à votre fichier CSS dans index.html et ajoutez une étape au processus de construction pour copier votre fichier CSS au même emplacement / dist relatif dans le cadre de l'étape de construction. Mais soyez prévenu, vous perdez le style de rechargement à chaud avec cette approche.

## Je veux juste un kit de démarrage vide.

Ce kit de démarrage comprend un exemple d'application afin que vous puissiez voir comment tout se bloque sur une vraie application. Lorsque vous avez terminé de l'examiner, exécutez ceci pour supprimer l'application de démonstration:

`npm exécuter remove-demo`

Vous ne voulez pas utiliser Redux? Voir la question suivante pour quelques étapes de suppression de Redux.

## Dois-je utiliser Redux?

Nan. Redux est utile pour les applications avec des flux de données plus complexes. Si votre application est simple, Redux est exagéré. Supprimez Redux comme ceci:

1. Exécutez `npm run remove-demo`
2. Désinstaller les paquets liés à Redux: `npm uninstall redux react-redux redux-thunk`
3. Créez un nouveau composant vide dans / components.
4. Appelez render sur le nouveau composant de niveau supérieur que vous avez créé à l'étape 3 dans src / index.js.

## Comment supprimer React Router?

1. Désinstallez React Router et les paquets liés au routage: `npm uninstall --save react-router-dom`
2. Supprimez ʻimport {Switch, NavLink, Route} de 'react-router-dom'; `du haut de` src / components / App.js`, ajoutez une référence à `src / components / FuelSavingsForm.js`, et remplacez le corps du rendu (implicite) par ceci: `<FuelSavingsPage />`.

## Comment déployer ceci?

`npm run build`. Cela construira le projet pour la production. Il fait ce qui suit:

* Minifie tous les JS
* Définit NODE_ENV sur prod afin que React soit construit en mode production
* Place les fichiers de projet créés dans / dist. (C'est le dossier que vous exposerez au monde).

Si la destination de l'application est différente de la racine du serveur (`/`), vous devez reconfigurer ʻoutput.publicPath` dans `webpack.config.prod.js` avant de construire l'application. Voir [documentation webpack] (https://webpack.js.org/configuration/output/#output-publicpath) pour plus d'informations.

Consultez ce [billet de blog] (http://www.latrovacommits.com/en/2017/12/14/how-publish-dist-folder-heroku/) montrant deux façons de déployer sur Heroku.

## Pourquoi les fichiers de test sont-ils placés à côté du fichier à tester (au lieu d'être centralisés)?

Les tests automatisés rationalisés sont une caractéristique essentielle de ce kit de démarrage. Tous les tests sont placés dans des fichiers qui se terminent par .spec.js. Les fichiers Spec sont placés dans le même répertoire que le fichier testé. Pourquoi?

* L'existence de tests est très visible. Si un fichier .spec correspondant n'a pas été créé, c'est évident.
* Facile à ouvrir car ils sont dans le même dossier que le fichier testé.
* Facile à créer de nouveaux fichiers de test lors de la création de nouveaux fichiers source.
* Les chemins d'importation courts sont faciles à taper et moins fragiles.
* Au fur et à mesure que les fichiers sont déplacés, il est facile de déplacer les tests.

Cela dit, vous pouvez bien sûr placer vos tests sous ** test ** à la place. Ensuite, Jest cherchera simplement dans / test pour trouver vos fichiers de spécifications.

## Comment déboguer?

Étant donné que les navigateurs ne prennent actuellement pas en charge ES6, nous utilisons Babel pour compiler notre ES6 vers ES5. Cela signifie que le code qui s'exécute dans le navigateur est différent de ce que nous avons écrit. Mais bonne nouvelle, un [sourcemap] (http://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) est généré pour permettre un débogage facile. Cela signifie que votre source JS d'origine sera affichée dans la console de développement de votre navigateur.
_Remarque: _ Lorsque vous exécutez `npm start`, aucun JS n'est minifié. Pourquoi? Parce que la minification ralentit la construction. Ainsi, JS n'est réduit que lorsque vous exécutez le script `npm run build`. Voir [plus d'informations sur la construction pour la production ci-dessus] (https://github.com/coryhouse/react-slingshot/blob/master/docs/FAQ.md#how-do-i-deploy-this).

Notez également qu'aucun fichier physique réel n'est écrit sur le système de fichiers pendant la construction du développement. ** Pour les performances, tous les fichiers existent en mémoire lorsqu'ils sont servis à partir du serveur Webpack. **. Les fichiers physiques ne sont écrits que lorsque vous exécutez `npm run build`.

** Conseils pour le débogage via sourcemaps: **

1. Les navigateurs varient dans la manière dont ils vous permettent d'afficher la source d'origine. Chrome affiche automatiquement la source d'origine si un sourcemap est disponible. Safari, en revanche, affichera la source minifiée et vous [devrez cmd + cliquer sur une ligne donnée pour être redirigé vers la source d'origine] (http://stackoverflow.com/questions/19550060/how-do-i -toggle-source-mapping-dans-safari-7).
2. N'activez ** pas ** la diffusion de fichiers à partir de votre système de fichiers dans les outils de développement Chrome. Si vous le faites, Chrome (et peut-être d'autres navigateurs) peut ne pas vous montrer la dernière version de votre code après avoir modifié le code source. À la place **, vous devez fermer l'onglet de vue source que vous utilisiez et le rouvrir pour voir le code source mis à jour **. Il semble que Chrome s'accroche à l'ancien sourcemap jusqu'à ce que vous fermiez et rouvriez l'onglet de vue source. Pour clarifier, vous n'avez pas à fermer l'onglet réel qui affiche l'application, juste l'onglet dans la console qui affiche le fichier source que vous venez de modifier.
3. Si la dernière source n'affiche pas la console, forcez une actualisation. Parfois, Chrome semble conserver une version précédente du sourcemap, ce qui vous fera voir du code périmé.

## Débogage dans Visual Studio Code:

* Installez l'extension [Debugger for Chrome] (https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome).
* Suivez les instructions pour [configurer le débogage dans le code Visual Studio] (https://github.com/Microsoft/vscode-chrome-debug/blob/master/README.md#using-the-debugger).
* Vous pouvez également ajouter ce qui suit au fichier `.vscode / launch.json` pour ouvrir automatiquement le navigateur Chrome et appliquer des sourcemaps.
* Démarrez l'application, puis cliquez sur l'icône de lecture verte dans Visual Studio Code pour démarrer le débogage.

** exemple launch.json **
`` json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "chrome",
      "demande": "lancement",
      "name": "Lancer Chrome sur localhost",
      "url": "http: // localhost: 3000",
      "webRoot": "$ {workspaceRoot} / src",
      "sourceMapPathOverrides": {
        "webpack: /// src / *": "$ {webRoot} / *"
      }
    }
  ]
}
''

Vous ne voyez pas la configuration de débogage de votre éditeur de code préféré ici? Soumettez un PR et nous serons heureux de l'ajouter à la FAQ.md.

## Pourquoi la construction utilise-t-elle des scripts npm au lieu de Gulp ou Grunt?

En bref, Gulp est une abstraction inutile qui crée plus de problèmes qu'elle n'en résout. [Voici pourquoi] (https://medium.com/@housecor/why-i-left-gulp-and-grunt-for-npm-scripts-3d6853dd22b8#.vtaziro8n).

## Pourquoi package.json fait-il référence à la version exacte?

Cela garantit que la construction ne sera pas interrompue lorsqu'une nouvelle version sera publiée. Malheureusement, de nombreux auteurs de paquets ne respectent pas correctement [Semantic Versioning] (http://semver.org), donc à la place, à mesure que de nouvelles versions seront publiées, nous les testerons et les introduirons dans React Slingshot. Mais oui, cela signifie que lorsque vous faites `npm update`, aucune nouvelle dépendance ne sera supprimée. Vous devrez mettre à jour package.json avec la nouvelle version manuellement.

## Comment gérer les images?

Via [le chargeur de fichiers Webpack](https://github.com/webpack/file-loader).

Exemple:

"html<img src = {require ('./src/ images / myImage.jpg')} />"

Webpack gérera alors intelligemment votre image pour vous. Pour la version de production, il copiera le fichier physique dans / dist, lui donnera un nom de fichier unique et insérera le chemin approprié dans votre balise d'image.

## J'obtiens une erreur lors de l'exécution de l'installation de npm: impossible de localiser "CL.exe"

Sous Windows, vous devez installer des dépendances supplémentaires pour que la synchronisation du navigateur soit créée et installée avec succès. Suivez les étapes de démarrage ci-dessus pour vous assurer que vous disposez des dépendances nécessaires sur votre machine.

## Je ne parviens pas à accéder à l'URL externe de Browsersync

Pour accéder à l'URL externe, tous les périphériques doivent être sur le même LAN. Cela peut donc signifier que votre machine de développement doit être sur le même Wifi que les appareils mobiles que vous testez. Vous pouvez également utiliser un outil tel que [localtunnel] (https://localtunnel.github.io/www/) ou [ngrok] (https://ngrok.com) pour exposer votre application via une URL publique. De cette façon, vous pouvez interagir avec l'application hébergée Browsersync sur n'importe quel appareil.

## Qu'en est-il des Redux Devtools?

Installez l '[extension Redux devtools] (https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd?hl=fr) dans les outils de développement Chrome. Si vous êtes intéressé par l'exécution des outils de développement Redux sur plusieurs navigateurs, Barry Staes a créé une [branche avec les outils de développement intégrés] (https://github.com/coryhouse/react-slingshot/pull/27).

## Le rechargement à chaud ne fonctionne pas!

Le rechargement à chaud ne fonctionne pas toujours bien avec les composants fonctionnels sans état pour le moment. [Il s'agit d'une limitation connue qui est actuellement en cours d'élaboration] (https://github.com/gaearon/babel-plugin-react-transform/issues/57). Pour éviter les problèmes de rechargement à chaud pour le moment, utilisez un composant React traditionnel basé sur les classes en haut de votre hiérarchie de composants.

## Comment configurer le rapport de couverture de code?

Utilisez la commande `npm run test: cover` pour exécuter les tests, en créant un rapport de couverture de code. Le rapport est écrit dans `/ coverage / lcov-report / index.html`. Slingshot fournit un script pour cela:

" bash
npm run open: couverture
"

Vous pouvez ajouter des métriques de couverture de code à votre fichier `README.md` et extraire en intégrant avec [Coveralls] (https://coveralls.io/).

1. Connectez-vous à Coveralls avec votre compte GitHub.
2. Autorisez Coveralls à accéder à vos référentiels.
3. Choisissez "Ajouter un dépôt" et sélectionnez votre dépôt.

C'est tout! Travis va maintenant exécuter le script `npm run test: cover: travis` après une compilation réussie, qui écrira le rapport de couverture au format standard lcov et l'envoyera directement à Coveralls. Les variables d'environnement fournies pour les jobs travis sont utilisées pour cibler automatiquement le bon projet Coveralls, à condition qu'il soit configuré comme décrit ci-dessus.

Vous pouvez obtenir le badge sur le site Web de Coveralls.

## Qu'en est-il de TypeScript?

Voici un [fork avec support TS] (https://github.com/typescriptcrew/ts-react-slingshot).
