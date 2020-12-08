---
title: Technologies web courantes côté client
description: Architecturez des applications Web modernes avec ASP.NET Core et Azure | Technologies Web courantes côté client
author: ardalis
ms.author: wiwagn
no-loc:
- Blazor
ms.date: 12/01/2020
ms.openlocfilehash: a4549e48152b21af05c67f601c1db65029e346fa
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851664"
---
# <a name="common-client-side-web-technologies"></a>Technologies web courantes côté client

> « Un site web doit faire bonne impression aussi bien à l’intérieur qu’à l’extérieur ».
> _- Paul Cookson_

Les applications ASP.NET Core sont des applications web qui reposent généralement sur des technologies web côté client de type HTML, CSS et JavaScript. En séparant le contenu de la page (le code HTML) de la mise en page et du style (le code CSS) et du comportement (via JavaScript), les applications web complexes peuvent tirer parti du principe de la séparation des rôles. Quand les rôles ne sont pas interconnectés, toute modification ultérieure de la structure, de la conception ou du comportement de l’application peut être effectuée plus facilement.

Les codes HTML et CSS sont relativement stables, mais JavaScript, en raison des frameworks d’application et des utilitaires que les développeurs utilisent pour créer des applications web, évolue très rapidement. Ce chapitre présente les différentes façons dont JavaScript est utilisé par les développeurs Web et fournit une vue d’ensemble de haut niveau des bibliothèques côté client angulaires et de réaction.

> [!NOTE]
> Blazor fournit une alternative aux infrastructures JavaScript pour créer des interfaces utilisateur clientes riches et interactives.

## <a name="html"></a>HTML

HTML est le langage de balisage standard utilisé pour créer des pages Web et des applications Web. Ses éléments forment les blocs de construction des pages, qui sont le texte mis en forme, les images, les entrées de formulaire et d’autres structures. Quand un navigateur envoie une demande à une URL, qu’il s’agisse de récupérer une page ou une application, la première chose retournée est un document HTML. Ce document HTML peut référencer ou inclure des informations supplémentaires concernant l’apparence et la disposition sous la forme de code CSS, ou le comportement sous la forme de code JavaScript.

## <a name="css"></a>CSS

Le code CSS (feuilles de style en cascade) est utilisé pour contrôler l’apparence et la disposition des éléments HTML. Les styles CSS peuvent être appliqués directement à un élément HTML, définis séparément dans la même page ou définis dans un fichier distinct référencé par la page. Les styles sont organisés en cascade selon la manière dont ils sont utilisés pour sélectionner un élément HTML donné. Par exemple, un style qui s’applique à l’ensemble d’un document est remplacé par un style appliqué à un élément particulier. De même, un style spécifique à un élément est remplacé par un style qui s’applique à une classe CSS appliquée à l’élément, qui, à son tour, est remplacé par un style ciblant une instance spécifique de cet élément (via son ID). Figure 6-1

![Règles de spécificité CSS](./media/image6-1.png)

**Figure 6-1.** Règles de spécificité CSS, dans l’ordre.

Il est préférable de conserver les styles dans leurs propres fichiers de feuille de style séparés et d’utiliser une cascade basée sur la sélection pour implémenter des styles cohérents et réutilisables au sein de l’application. Évitez autant que possible de placer des règles de style dans le HTML et, si vous devez appliquer des styles à des éléments individuels (plutôt qu’à toute une classe d’éléments ou à des éléments sur lesquels est appliquée une classe CSS particulière), faites-le à titre exceptionnel.

### <a name="css-preprocessors"></a>Préprocesseurs CSS

Les feuilles de style CSS ne prennent pas en charge la logique conditionnelle, les variables et d’autres fonctionnalités de langage de programmation. Ainsi, les feuilles de style volumineuses incluent souvent un certain nombre de répétitions, car la même couleur, la même police ou un autre paramètre est appliqué à de nombreuses variantes des éléments HTML et des classes CSS. Les préprocesseurs CSS peuvent permettre à vos feuilles de style de suivre le [principe DRY](https://deviq.com/don-t-repeat-yourself/) en ajoutant la prise en charge des variables et de la logique.

Les préprocesseurs CSS les plus connus sont Sass et LESS. Tous deux étendent le code CSS, pour lequel ils offrent une compatibilité descendante, ce qui signifie qu’un fichier CSS simple est un fichier Sass ou LESS valide. Sass est basé sur Ruby et LESS sur JavaScript. Ils s’exécutent généralement dans le cadre de votre processus de développement local. Les deux outils de ligne de commande sont disponibles, ainsi que la prise en charge intégrée dans Visual Studio pour les exécuter à l’aide de tâches Gulp ou grunt.

## <a name="javascript"></a>JavaScript

JavaScript est un langage de programmation dynamique interprété qui a été normalisé dans la spécification du langage ECMAScript. Il s’agit du langage de programmation du web. Tout comme CSS, JavaScript peut être défini sous forme d’attributs dans les éléments HTML, de blocs de script dans une page ou dans des fichiers distincts. Tout comme CSS, il est recommandé d’organiser JavaScript en fichiers séparés, ce qui le rend le plus séparé possible du code HTML dans des pages Web individuelles ou des vues d’application.

Quand vous utilisez JavaScript dans votre application web, vous devez généralement effectuez certaines tâches :

- Sélectionner un élément HTML et récupérer et/ou mettre à jour sa valeur.

- Interroger une API web pour obtenir des données.

- Envoyer une commande à une API web (et répondre à un rappel avec son résultat).

- Procéder à une validation.

Vous pouvez effectuer toutes ces tâches avec JavaScript seulement, mais de nombreuses bibliothèques permettent de simplifier les étapes. L’une des premières et les plus fructueuses de ces bibliothèques est jQuery, qui reste un choix populaire pour simplifier ces tâches sur les pages Web. Pour les applications monopages (SPA), jQuery ne fournit pas les nombreuses fonctionnalités qu’offrent Angular et React.

### <a name="legacy-web-apps-with-jquery"></a>Applications web héritées avec jQuery

Bien que les normes de framework JavaScript, jQuery continuent à être une bibliothèque couramment utilisée pour travailler avec HTML/CSS et à créer des applications qui effectuent des appels AJAX à des API Web. Toutefois, jQuery fonctionne au niveau DOM (Document Object Model) du navigateur et offre par défaut uniquement un modèle impératif et non déclaratif.

Par exemple, supposons qu’un élément de la page doit être visible si la valeur d’une zone de texte dépasse 10. Dans jQuery, cette fonctionnalité est généralement implémentée en écrivant un gestionnaire d’événements avec du code qui inspecterait la valeur de la zone de texte et définissait la visibilité de l’élément cible en fonction de cette valeur. Ce processus est une approche impérative basée sur le code. En revanche, un autre framework peut à la place utiliser la liaison de données pour lier la visibilité de l’élément à la valeur de la zone de texte de manière déclarative. Cette approche ne nécessite pas l’écriture de code, mais nécessite uniquement la décoration des éléments impliqués dans les attributs de liaison de données. Comme les comportements côté client sont plus complexes, les approches de liaison de données se traduisent souvent par des solutions plus simples, avec moins de code et une complexité conditionnelle.

### <a name="jquery-vs-a-spa-framework"></a>Comparaison entre jQuery et un framework SPA

| **Factor** | **JQuery** | **Angular**|
|--------------------------|------------|-------------|
| Fait abstraction du DOM | **Oui** | **Oui** |
| Prise en charge d’Ajax | **Oui** | **Oui** |
| Liaison de données déclarative | **Non** | **Oui** |
| Routage de style MVC | **Non** | **Oui** |
| Création de modèles | **Non** | **Oui** |
| Routage de lien ciblé | **Non** | **Oui** |

La plupart des fonctionnalités absentes dans jQuery peuvent être ajoutées par le biais d’autres bibliothèques. Toutefois, un framework SPA comme Angular fournit ces fonctionnalités de façon plus intégrée, puisqu’elles sont prises en compte dès sa conception. De plus, jQuery est une bibliothèque impérative, ce qui signifie que vous devez appeler des fonctions jQuery pour faire quoi que ce soit avec jQuery. La plupart des tâches et des fonctionnalités que fournissent les frameworks SPA peuvent être effectuées de façon déclarative, sans avoir réellement à écrire du code.

La liaison de données est un excellent exemple de cette fonctionnalité. Dans jQuery, il suffit généralement d’une seule ligne de code pour obtenir la valeur d’un élément DOM ou définir la valeur d’un élément. Toutefois, vous devez écrire ce code chaque fois que vous devez modifier la valeur de l’élément, ce qui se produit parfois dans plusieurs fonctions sur une page. Un autre exemple courant est la visibilité de l’élément. Dans jQuery, il peut y avoir de nombreux emplacements différents où vous écrirez du code pour contrôler si certains éléments étaient visibles. Dans chacun de ces cas, si vous utilisez la liaison de données, vous n’avez plus besoin d’écrire du code. Vous devez simplement lier la valeur ou la visibilité des éléments en question à un *ViewModel* sur la page, et les modifications apportées à ce ViewModel seront automatiquement reflétées dans les éléments liés.

### <a name="angular-spas"></a>SPA Angular

Angulaire reste l’un des frameworks JavaScript les plus populaires au monde. Étant donné que l’angulaire 2, l’équipe a reconstruit le Framework de bout en bout (à l’aide de la [machine à écrire](https://www.typescriptlang.org/)) et rebaptisé le nom de AngularJS d’origine en angulaire. Désormais, il y a plusieurs années, l’angle repensé repensée continue d’être une infrastructure robuste pour la création d’applications à page unique.

Les applications Angular sont créées à partir de composants. Les composants combinent des modèles HTML et des objets spéciaux, et contrôlent une partie de la page. Un composant simple provenant de la documentation d’Angular est présenté ici :

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

Les composants sont définis à l’aide de la fonction d’élément décoratif @Component qui récupère les métadonnées du composant. La propriété Selector identifie l’ID de l’élément sur la page où ce composant sera affiché. La propriété de modèle est un modèle HTML simple qui inclut un espace réservé correspondant à la propriété de nom du composant, défini sur la dernière ligne.

Parce qu’elles utilisent des composants et des modèles, au lieu d’éléments DOM, les applications Angular peuvent fonctionner à un niveau d’abstraction supérieur et avec moins de code global que les applications écrites seulement à l’aide de JavaScript (également appelées « Vanilla JS ») ou avec jQuery. Angular impose également un certain ordre pour l’organisation de vos fichiers de script côté client. Par convention, les applications Angular utilisent une structure de dossiers commune, avec des fichiers de script de module et de composant situés dans un dossier d’application. Les scripts Angular qui permettent de créer, déployer et tester l’application sont généralement placés dans un dossier de niveau supérieur.

Vous pouvez développer des applications angulaires à l’aide d’une interface CLI. Pour commencer à développer localement des applications avec Angular (ce qui suppose que vous avez déjà installé git et npm), vous devez simplement cloner un dépôt à partir de GitHub, puis exécuter `npm install` et `npm start`. En outre, angulaire fournit sa propre interface CLI, qui peut créer des projets, ajouter des fichiers et assister aux tâches de test, de regroupement et de déploiement. Cette convivialité de l’interface CLI rend l’angle particulièrement compatible avec ASP.NET Core, qui offre également une excellente prise en charge de l’interface de commande.

Microsoft a développé une application de référence, eShopOnContainers, qui inclut une implémentation d’application SPA Angular. Cette application intègre des modules Angular pour gérer le panier d’achat de la boutique en ligne, charger et afficher des éléments du catalogue et gérer la création de commandes. Vous pouvez afficher et télécharger l’exemple d’application à partir de [GitHub](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA).

### <a name="react"></a>React

Contrairement à Angular, qui offre une implémentation complète du modèle MVC (Model-View-Controller), React concerne uniquement les affichages. Comme ce n’est pas un framework, mais une simple bibliothèque, vous devez utiliser des bibliothèques supplémentaires pour créer une application SPA. Il existe plusieurs bibliothèques conçues pour être utilisées avec REACT pour produire des applications de page unique riches.

Une des fonctionnalités les plus importantes de React est qu’il utilise un modèle DOM virtuel. Le modèle DOM virtuel offre à React plusieurs avantages, notamment au niveau des performances (le modèle DOM virtuel peut optimiser les parties du modèle DOM réel qui doivent être mises à jour) et de la testabilité (pas besoin d’utiliser un navigateur pour tester React et ses interactions avec son modèle DOM virtuel).

React est également inédit dans la façon dont il utilise le code HTML. Au lieu d’avoir une séparation stricte entre le code et le balisage (avec des références à JavaScript apparaissant dans des attributs HTML, par exemple), React ajoute du code HTML directement dans le code JavaScript sous la forme JSX. JSX est une syntaxe de type HTML qui peut compiler du code en JavaScript pur. Par exemple :

```js
<ul>
{ authors.map(author =>
    <li key={author.id}>{author.name}</li>
)}
</ul>
```

Si vous connaissez déjà JavaScript, vous apprendrez facilement à utiliser React. Il n’implique pas de courbe d’apprentissage ou de syntaxe spéciale comme pour Angular ou d’autres bibliothèques connues.

Comme React n’est pas un framework complet, vous avez généralement besoin d’autres bibliothèques pour gérer des opérations comme le routage, les appels d’API web et la gestion des dépendances. Ce qui est intéressant, c’est que vous pouvez choisir la meilleure bibliothèque pour chaque opération. En revanche, vous devez prendre toutes ces décisions et vérifiez que toutes les bibliothèques choisies fonctionnent bien ensemble une fois que vous avez terminé. Si vous voulez un bon point de départ, vous pouvez utiliser un starter kit comme React Slingshot, qui empaquette avec React un ensemble de bibliothèques compatibles.

### <a name="vue"></a>Vue

Dans son guide de prise en main, «vue est une infrastructure progressive pour la création d’interfaces utilisateur. Contrairement à d’autres infrastructures monolithiques, la vue de vue est conçue de manière à pouvoir être remplacée de manière incrémentielle. La bibliothèque principale est axée sur la couche de vue uniquement et est facile à récupérer et à intégrer avec d’autres bibliothèques ou des projets existants. En revanche, la vue d’ensemble est parfaitement en capacité d’alimenter des applications de Single-Page sophistiquées en cas d’utilisation avec les outils modernes et les bibliothèques de prise en charge.»

La prise en main de la vue nécessite simplement l’inclusion de son script dans un fichier HTML :

```html
<!-- development version, includes helpful console warnings -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

Une fois l’infrastructure ajoutée, vous pouvez ensuite restituer les données dans le DOM à l’aide de la syntaxe de création de modèles simple de la vue de données :

```html
<div id="app">
  {{ message }}
</div>
```

puis en ajoutant le script suivant :

```js
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
```

Cela suffit pour afficher « Hello vue ! » sur la page. Notez, cependant, que la vue vue n’est pas simplement le simple rendu du message à la balise div. Il prend en charge la liaison de type de liaison et les mises à jour dynamiques, de sorte que si la valeur de `message` change, la valeur dans le `<div>` est immédiatement mise à jour pour refléter ce dernier.

Bien entendu, cela ne fait que gratter la surface de la vue. Il s’agit d’une grande popularité au cours des dernières années et a une vaste communauté. La [liste des composants et des bibliothèques de prise en charge](https://github.com/vuejs/awesome-vue#redux) qui fonctionnent avec la vue pour l’étendre également est une énorme et en pleine expansion. Si vous envisagez d’ajouter un comportement côté client à votre application Web ou si vous envisagez de créer un SPA complet, vous devez examiner la vue.

### <a name="no-locblazor-webassembly"></a>Blazor Webassembly

Contrairement aux autres infrastructures JavaScript, `Blazor WebAssembly` est une infrastructure d’application à page unique (Spa) qui vous aide à créer des applications Web interactives côté client avec .net. Blazor Webassembly utilise des normes Web ouvertes sans plug-ins ni recompilation du code dans d’autres langages. Blazor Webassembly fonctionne dans tous les navigateurs Web modernes, y compris les navigateurs mobiles.

L’exécution de code .NET dans des navigateurs Web est rendue possible par webassembly (abrégé `wasm` ). WebAssembly est un format bytecode compact optimisé pour un téléchargement rapide et une vitesse d’exécution maximale. WebAssembly est un standard web ouvert pris en charge dans les navigateurs web sans plug-in.

Le code webassembly peut accéder aux fonctionnalités complètes du navigateur via JavaScript, appelé interopérabilité JavaScript, souvent abrégé en COM Interop ou l’interopérabilité JS. Le code .NET exécuté via WebAssembly dans le navigateur s’exécute dans le bac à sable JavaScript du navigateur avec les protections offertes par le bac à sable contre les actions malveillantes sur l’ordinateur client.

Pour plus d’informations, consultez [Introduction à Blazor ASP.net Core](https://docs.microsoft.com/aspnet/core/blazor/?view=aspnetcore-5.0)

### <a name="choosing-a-spa-framework"></a>Choix d’un framework SPA

Lorsque vous envisagez l’option qui convient le mieux pour la prise en charge de votre SPA, gardez à l’esprit les considérations suivantes :

- Votre équipe est-elle familiarisée avec le framework et ses dépendances (y compris TypeScript dans certains cas) ?

- Quel est le degré de rigidité du framework et acceptez-vous son mode de fonctionnement par défaut ?

- Toutes les fonctionnalités nécessaires pour votre application sont-elles incluses dans le framework ou dans une bibliothèque complémentaire ?

- Est-il bien documenté ?

- Sa communauté est-elle active ? Les nouveaux projets sont-ils générés ?

- Son équipe principale est-elle active ? Les problèmes sont-ils résolus et de nouvelles versions sont-elles publiées régulièrement ?

Les infrastructures continuent d’évoluer avec la vitesse très. Utilisez les considérations ci-dessus pour vous aider à limiter les risques en évitant de choisir un framework que vous pourriez regretter par la suite. Si vous ne voulez prendre aucun risque, choisissez un framework qui offre un support commercial et/ou est développé par une grande entreprise.

> ### <a name="references--client-web-technologies"></a>Références - Technologies web clientes
>
> - **HTML et CSS**  
> <https://www.w3.org/standards/webdesign/htmlcss>
> - **Sass et LESS**  
> <https://www.keycdn.com/blog/sass-vs-less/>
> - **Application de styles aux applications ASP.NET Core avec LESS, Sass et Font Awesome**  
> <https://docs.microsoft.com/aspnet/core/client-side/less-sass-fa>
> - **Développement côté client dans ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/client-side/>
> - **JQuery**  
> <https://jquery.com/>
> - **jQuery vs AngularJS**  
> <https://www.airpair.com/angularjs/posts/jquery-angularjs-comparison-migration-walkthrough>
> - **Angular**  
> <https://angular.io/>
> - **React**  
> <https://reactjs.org/>
> - **Vue**  
> <https://vuejs.org/>
> - **Angulaire vs REACT vs vue : Framework à choisir dans 2020**
> <https://www.codeinwp.com/blog/angular-vs-vue-vs-react/>
> - **Les principales infrastructures JavaScript pour le développement de Front-End dans 2020**  
> <https://www.freecodecamp.org/news/complete-guide-for-front-end-developers-javascript-frameworks-2019/>

>[!div class="step-by-step"]
>[Précédent](common-web-application-architectures.md) 
> [Suivant](develop-asp-net-core-mvc-apps.md)
