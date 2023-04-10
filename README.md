# TP  Web Applications

### `npm install` command also generated a package-lock.json file along with package.json. What is the purpose of this file?

Le fichier package.json est le fichier de configuration dans un projet Node.js. Ce fichier contient de nombreuses informations importantes comme le nom du projet, son auteur, une description, les scripts d'exécution, ou encre la liste des dépendances nécessaires au projet.
Quand on va exécuter la commande `npm install`, cela va installer toutes les dépendances listées dans ce fichier, le fichier node_modules est ensuite créé et contient toues les dépendances qui viennent d'être installées.

### By convention, all NPM dependencies use a 3-digit format for version numbers. How do you call this?

Il s'agit d'une convention NPM appelée Semantic Versioning (Semver). Un package ne peut pas être publié s'il ne suit pas cette convention.

### What is a devDependency exactly? What are the differences with a dependency?

Une DevDependency est une dépendance de développement dans un projet Node.js, elle permet de spécifier les dépendances nécessaires pour le développement et les tests ais qui ne sont pas nécessaires pour la production. Il peut s'agir des frameworks de tests, des outils de formatage du code, des bibliothèques de simukation de serveur, ...
Les DevDependancies sont spécifiées dans le fichier package.json.

### What is a closure/iife ? What was it used for ? What replaced it?

Une fonction IIFE (Immediately Invoked Function Expression) ou fonction de closure est une fonction qui s'exécute immédiatement dès qu'elles est invoquée. Par exemple, dans ce projets, avant de les retirer, une IIFE était appelée dès qu'on arrivait sur la page welcome, game ou score.
Ce type de fonctions était souvent utilisée avant ES5 car elle permet de créer un scope privé. Ainsi, les variables ne polluent pas les scopes globaux
Aujourd'hui, les IIFE ont été remplacé par les modules ES. En effet, tout ce qui ce trouve dans un module ES est privé, sauf si on l'exporte.

### What is the difference between import * from './utils' and import { parseUrl } from './utils'? What can be the consequences of using one instead of the other?

- import * from './utils' permet d'importer tous les éléments de ./utils qui on été exportés. Il faudra donc passer par utils pour accéder à ses composants (utils.***)
- import { parseUrl } from './utils' permet d'importer seulement la méthode parseUrl de ./utils. On peut dans ce cas utiliser directement utiliser la méthode parsUrl sans passer par le utils.*** . 

### Can you think of at least 2 things that are possible with Java classes, but cannot be done with ES6 classes?

- Les classes Java peuvent utiliser des interfaces, ce qui n'est pas possible avec ES6
- Les classes Java peuvent contenir des constructeurs ou des méthodes surchargés, autrement dit il peut y avoirs plusieurs méthodes du même nom avec des paramètres différents, ce qui n'est pas possible avec les classes ES6

### What are the differences between var and let;

La principale différence entre var et let est dans la portée de la variable. Une variable déclarée avec var a une portée de fonction, autrement dit, même si elle est déclarée dans une boucle if, while ou for, on pourra y avoir accès en dehors. En revanche, une variable déclarée avec let à une portée de bloc, autrement dit, elle ne sera accessible que dans le bloc où elle a été déclarée. Si elle est par exemple déclarée dans une boucle for, on ne pourra pas avoir accès à cette variable en dehors.

### What is the .bind(this) stuff? What happens if you delete it? Is it needed when using an arrow function ? why ?

Quand on utilise une fonction de callback, c'est-à-dire une fonction qui prend une fonction en paramètres (comme setTimeOut, par exemple), le contexte (this) change et devient l'objet utilisé pour appeler la fonction de callback.
Par exemple, si on fait window.setTimeOut(fonction(), 1000), ça ne retournera rien (undefined) car this est lié à window, qui ne contient pas de méthode fonction(), alors que si on avait simplement appelé fonction(), il n'y aurait pas eu de problème. Le .bind(this) permet donc de récupérer le contexte global.
En revanche, le .bind(this) n'est pas nécéssaire quand on utilise une arrow function car cette dernière prend le contexte (this) du parent, ce qui permet également une syntaxe plus courte.

### What does the @ symbol mean in @babel/***?

Le symbole @ permet de désigner un scoped package, autrement dit un package qui est regroupé sos un scope particulier.
Ici @babel/*** est un package qui fait partie de l'écosystème Babel et qui est regroupé sous le scope @babel.

### What are the advantages of Promises?

Les promesses permettent de récupérer une notion d'ordre grâce aux .then(), ce qui rend le code beaucoup plus lisible que des callbacks imbriqués (callback hell)
Les promesses permettent également de gérer lusieurs opérations asynchrones en parallèle, on attend alors que toutes ces opérations soient terminées avant de continuer. Cela permet d'accélérer les traitement des opérations asynchrones en évitant d'attendre qu'une opération soit terminée avant de passer à la suivante.

### What version of ECMAScript async / await was released in ?

Les outils async/await sont apparus avec ECMAScript 2017 avec ES8. Ils ont été introduits pour faciliter la gestion des opérations asynchrones en permettant d'écrire du code utilisant des fonctions asynchrones ressemblant à un code synchrone. La plupart des navigateurs modernes, ainsi que Node.js à partir de la version 7.6, prennent en charge async/await.

### Component-oriented programming for the web is considered more maintainable. Why?

Avant, l'architecture répandue était de trier les fichiers par type (scripts, views et styles), ce qui n'est pas idéal. En effet, une modification sur un fichier peut avoir un impact sur des fichiers d'autre type. De plus, s'il est simple de localiser les fichiers par type, il est beaucoup plus difficile de les repérer par caractéristique.
La programmation orientée composants permet de régler ce problème. Un composant est un morceau de code qui correspond à un élément spécifique sur la plage, il est généralement petit, autonome et réutilisable. Les pages et les foncrionalités du projet vont ainsi être répartis dans des composants réutilisables, ce qui permet une meilleure séparation par caractéristique.

### What is Functional programming?

La programmation fonctionnelle est un paradigme de programmation qui se concentre sur les fonctions en tant que blocs de construction fondamentaux pour la création de logiciels. Cette approche permet de créer des programmes plus faciles à lire, à comprendre et à maintenir, ainsi que de faciliter la réutilisation du code existant.
Par exemple, cela peut passer par l'utilisation des fonctions map(), filter() et reduce() pour traiter des tableaux.


### Explain what the map() function does ?

La fonction map() permet de transformer les valeurs d'un tableau.
Par exemple, l'opération tab.map(val => val*2); va retourner un tableau identique à tab, mais avec des valeurs doublées.

### Explain what the filter() function does ?

La fonction filter() permet de filtrer les cases d'un tableau.
Par exemple, l'opération tab.filter(val => val > 5); retournera un tableau identique à tab mais ne contenant pas les cases de tab ayant une valeur supérieure à 5.


### Explain what the reduce() function does ?

La fonction reduce() ne retourne pas de tableau, mais retournera la dernière valeur en fontion de l'opération choisie.
Par exemple, l'opération tab.reduce((accumulator, currentValue) => accumulator + currentValue, 0); permet de sommer toutes les cases du tableau tab, elle renverra donc le résultat de cette somme

### What is the difference between .then() and async/await when handling asynchronous functions?

La différence principale entre les .then et async/await et la façon de gérer les promesses. async/await utilise une syntaxe plus claire (il suffit simplement de déclarer la fonction async et de mettre await devant l'opération asynchrone) en comparaison avec les chaînes de .then(), ce qui permet d'avoir un code plus lisible et plus simple à maintenir. En revanche, le .then() peut être appliqué à n'importe quelle fonction, qu'elle soit assynchrone ou non, il permet donc plus de flexibilité.

### What does the _ prefix mean on a sass file?

Si un fichier sass est précédé de _, cela signifie qu'il s'agit d'un fichier partiel. Cela indique qu'ils ne sont pas destinés à être compilés en CSSdirectement car ils sont inclus dans d'autres fichiers scss. Le _ n'est donc pas obligatoire.
Par exemple, dans le projet, le fichier colors.scss contient seulement la valeur de la variable primary est est importé dans les autres fichiers de style. Il n'est donc pas utile de le complier en CSS comme il est nécéssaire de le faire pour le fichier styles.scss