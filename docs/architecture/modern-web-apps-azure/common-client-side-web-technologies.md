---
title: Technologies Web communes côté client
description: Architect Modern Web Applications avec ASP.NET Core et Azure (fr) Technologies Web communes côté client
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: 2809c8539b42e8e2250039dceed1389b3cbdcd8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449372"
---
# <a name="common-client-side-web-technologies"></a>Technologies Web communes côté client

> « Un site web doit faire bonne impression aussi bien à l’intérieur qu’à l’extérieur ».  
> _- Paul Cookson_

Les applications ASP.NET Core sont des applications web qui reposent généralement sur des technologies web côté client de type HTML, CSS et JavaScript. En séparant le contenu de la page (le code HTML) de la mise en page et du style (le code CSS) et du comportement (via JavaScript), les applications web complexes peuvent tirer parti du principe de la séparation des rôles. Quand les rôles ne sont pas interconnectés, toute modification ultérieure de la structure, de la conception ou du comportement de l’application peut être effectuée plus facilement.

Les codes HTML et CSS sont relativement stables, mais JavaScript, en raison des frameworks d’application et des utilitaires que les développeurs utilisent pour créer des applications web, évolue très rapidement. Ce chapitre examine quelques façons dont JavaScript est utilisé par les développeurs Web et fournit un aperçu de haut niveau des bibliothèques angulaires et réagir côté client.

> [!NOTE]
> Blazor offre une alternative aux cadres JavaScript pour la construction d’interfaces utilisateur client interactives riches. Le soutien de Blazor côté client est toujours en avant-première, donc pour l’instant il est hors de portée pour ce chapitre.

## <a name="html"></a>HTML

HTML est le langage de balisage standard utilisé pour créer des pages Web et des applications Web. Ses éléments forment les blocs de construction des pages, qui sont le texte mis en forme, les images, les entrées de formulaire et d’autres structures. Quand un navigateur envoie une demande à une URL, qu’il s’agisse de récupérer une page ou une application, la première chose retournée est un document HTML. Ce document HTML peut référencer ou inclure des informations supplémentaires concernant l’apparence et la disposition sous la forme de code CSS, ou le comportement sous la forme de code JavaScript.

## <a name="css"></a>CSS

Le code CSS (feuilles de style en cascade) est utilisé pour contrôler l’apparence et la disposition des éléments HTML. Les styles CSS peuvent être appliqués directement à un élément HTML, définis séparément dans la même page ou définis dans un fichier distinct référencé par la page. Les styles sont organisés en cascade selon la manière dont ils sont utilisés pour sélectionner un élément HTML donné. Par exemple, un style qui s’applique à l’ensemble d’un document est remplacé par un style appliqué à un élément particulier. De même, un style spécifique à un élément serait remplacé par un style qui s’appliquait à une classe CSS qui s’appliquait à l’élément, qui à son tour serait remplacé par un style ciblant un exemple spécifique de cet élément (via son ID). Figure 6-1

![Règles de spécificité du CSS](./media/image6-1.png)

**Figure 6-1.** Règles de spécificité CSS, dans l’ordre.

Il est préférable de conserver les styles dans leurs propres fichiers de feuille de style séparés et d’utiliser une cascade basée sur la sélection pour implémenter des styles cohérents et réutilisables au sein de l’application. Évitez autant que possible de placer des règles de style dans le HTML et, si vous devez appliquer des styles à des éléments individuels (plutôt qu’à toute une classe d’éléments ou à des éléments sur lesquels est appliquée une classe CSS particulière), faites-le à titre exceptionnel.

### <a name="css-preprocessors"></a>Préprocesseurs CSS

Les feuilles de style CSS ne prennent pas en charge la logique conditionnelle, les variables et d’autres fonctionnalités de langage de programmation. Ainsi, les grandes feuilles de style incluent souvent un peu de répétition, car la même couleur, police, ou autre réglage est appliqué à beaucoup de différentes variations d’éléments HTML et de classes CSS. Les préprocesseurs CSS peuvent permettre à vos feuilles de style de suivre le [principe DRY](https://deviq.com/don-t-repeat-yourself/) en ajoutant la prise en charge des variables et de la logique.

Les préprocesseurs CSS les plus connus sont Sass et LESS. Tous deux étendent le code CSS, pour lequel ils offrent une compatibilité descendante, ce qui signifie qu’un fichier CSS simple est un fichier Sass ou LESS valide. Sass est basé sur Ruby et LESS sur JavaScript. Ils s’exécutent généralement dans le cadre de votre processus de développement local. Tous deux disposent d’outils de ligne de commande, ainsi que d’un support intégré dans Visual Studio pour les exécuter à l’aide de tâches Gulp ou Grunt.

## <a name="javascript"></a>JavaScript

JavaScript est un langage de programmation dynamique interprété qui a été normalisé dans la spécification du langage ECMAScript. Il s’agit du langage de programmation du web. Tout comme CSS, JavaScript peut être défini sous forme d’attributs dans les éléments HTML, de blocs de script dans une page ou dans des fichiers distincts. Tout comme CSS, il est recommandé d’organiser JavaScript en fichiers séparés, le gardant séparé autant que possible du HTML trouvé sur les pages Web individuelles ou les vues d’application.

Quand vous utilisez JavaScript dans votre application web, vous devez généralement effectuez certaines tâches :

- Sélectionner un élément HTML et récupérer et/ou mettre à jour sa valeur.

- Interroger une API web pour obtenir des données.

- Envoyer une commande à une API web (et répondre à un rappel avec son résultat).

- Procéder à une validation.

Vous pouvez effectuer toutes ces tâches avec JavaScript seulement, mais de nombreuses bibliothèques permettent de simplifier les étapes. La première et la plus renommée de ces bibliothèques est jQuery, qui reste choisie par le plus grand nombre pour simplifier ces tâches sur les pages web. Pour les applications monopages (SPA), jQuery ne fournit pas les nombreuses fonctionnalités qu’offrent Angular et React.

### <a name="legacy-web-apps-with-jquery"></a>Applications web héritées avec jQuery

Bien qu’ancienne par les normes de cadre JavaScript, jQuery continue d’être une bibliothèque couramment utilisée pour travailler avec HTML /CSS et les applications de construction qui font des appels AJAX aux API Web. Toutefois, jQuery fonctionne au niveau DOM (Document Object Model) du navigateur et offre par défaut uniquement un modèle impératif et non déclaratif.

Par exemple, supposons qu’un élément de la page doit être visible si la valeur d’une zone de texte dépasse 10. Dans jQuery, vous implémentez cette fonction en écrivant un gestionnaire d’événements avec du code pour inspecter la valeur de la zone de texte et définir la visibilité de l’élément cible en fonction de cette valeur. Il s’agit d’une approche impérative, basée sur le code. En revanche, un autre framework peut à la place utiliser la liaison de données pour lier la visibilité de l’élément à la valeur de la zone de texte de manière déclarative. Pour cela vous n’avez pas besoin d’écrire de code, mais vous devez décorer les éléments concernés avec des attributs de liaison de données. À mesure que les comportements côté client deviennent plus complexes, les approches de liaison des données se traduisent souvent par des solutions plus simples avec moins de code et de complexité conditionnelle.

### <a name="jquery-vs-a-spa-framework"></a>Comparaison entre jQuery et un framework SPA

| **Factor** | **Jquery** | **Angular**|
|--------------------------|------------|-------------|
| Fait abstraction du DOM | **Oui** | **Oui** |
| Prise en charge d’Ajax | **Oui** | **Oui** |
| Liaison de données déclarative | **Non** | **Oui** |
| Routage de style MVC | **Non** | **Oui** |
| Création de modèles | **Non** | **Oui** |
| Routage de lien ciblé | **Non** | **Oui** |

La plupart des fonctionnalités absentes dans jQuery peuvent être ajoutées par le biais d’autres bibliothèques. Toutefois, un framework SPA comme Angular fournit ces fonctionnalités de façon plus intégrée, puisqu’elles sont prises en compte dès sa conception. En outre, jQuery est une bibliothèque impérative, ce qui signifie que vous devez appeler jQuery fonctions afin de faire n’importe quoi avec jQuery. La plupart des tâches et des fonctionnalités que fournissent les frameworks SPA peuvent être effectuées de façon déclarative, sans avoir réellement à écrire du code.

La liaison de données en est un bon exemple. Dans jQuery, il suffit généralement d’une seule ligne de code pour obtenir la valeur d’un élément DOM ou pour définir la valeur d’un élément. Cependant, vous devez écrire ce code chaque fois que vous avez besoin de changer la valeur de l’élément, et parfois cela se produira dans plusieurs fonctions sur une page. Un autre exemple courant est la visibilité de l’élément. Dans jQuery, il pourrait y avoir beaucoup d’endroits différents où vous écriviez du code pour contrôler si certains éléments étaient visibles. Dans chacun de ces cas, si vous utilisez la liaison de données, vous n’avez plus besoin d’écrire du code. Vous lieriez simplement la valeur ou la visibilité des éléments en question à un *modèle de vue* sur la page, et les modifications apportées à ce modèle de vue seraient automatiquement reflétées dans les éléments liés.

### <a name="angular-spas"></a>SPA Angular

Angular reste l’un des cadres JavaScript les plus populaires au monde. Depuis Angular 2, l’équipe a reconstruit le cadre à partir de zéro (en utilisant [TypeScript](https://www.typescriptlang.org/)) et rebaptisé du nom original AngularJS à tout simplement Angular. Aujourd’hui âgé de plusieurs années, l’angulaire redessinée continue d’être un cadre solide pour la construction d’applications à une page unique.

Les applications Angular sont créées à partir de composants. Les composants combinent des modèles HTML et des objets spéciaux, et contrôlent une partie de la page. Un composant simple provenant de la documentation d’Angular est présenté ici :

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

Les composants sont définis à l’aide de la fonction d’élément décoratif @Component qui récupère les métadonnées du composant. La propriété du sélecteur identifie l’ID de l’élément sur la page où ce composant sera affiché. La propriété de modèle est un modèle HTML simple qui inclut un espace réservé correspondant à la propriété de nom du composant, défini sur la dernière ligne.

Parce qu’elles utilisent des composants et des modèles, au lieu d’éléments DOM, les applications Angular peuvent fonctionner à un niveau d’abstraction supérieur et avec moins de code global que les applications écrites seulement à l’aide de JavaScript (également appelées « Vanilla JS ») ou avec jQuery. Angular impose également un certain ordre pour l’organisation de vos fichiers de script côté client. Par convention, les applications Angular utilisent une structure de dossiers commune, avec des fichiers de script de module et de composant situés dans un dossier d’application. Les scripts Angular qui permettent de créer, déployer et tester l’application sont généralement placés dans un dossier de niveau supérieur.

Vous pouvez développer des applications angulaires à l’aide d’un CLI. Pour commencer à développer localement des applications avec Angular (ce qui suppose que vous avez déjà installé git et npm), vous devez simplement cloner un dépôt à partir de GitHub, puis exécuter `npm install` et `npm start`. Au-delà de cela, Angular expédie son propre CLI, qui peut créer des projets, ajouter des fichiers et aider à tester, grouper et déployer des tâches. Cette convivialité CLI rend Angulaire particulièrement compatible avec ASP.NET Core, qui dispose également d’un grand support CLI.

Microsoft a développé une application de référence, [eShopOnContainers](https://aka.ms/MicroservicesArchitecture), qui inclut une implémentation d’application SPA Angular. Cette application intègre des modules Angular pour gérer le panier d’achat de la boutique en ligne, charger et afficher des éléments du catalogue et gérer la création de commandes. Vous pouvez afficher et télécharger l’exemple d’application à partir de [GitHub](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA).

### <a name="react"></a>React

Contrairement à Angular, qui offre une implémentation complète du modèle MVC (Model-View-Controller), React concerne uniquement les affichages. Comme ce n’est pas un framework, mais une simple bibliothèque, vous devez utiliser des bibliothèques supplémentaires pour créer une application SPA. Il existe un certain nombre de bibliothèques qui sont conçues pour être utilisées avec React pour produire des applications riches d’une seule page.

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

Dès son guide de départ, "Vue est un cadre progressif pour la construction d’interfaces utilisateur. Contrairement à d’autres cadres monolithiques, Vue est conçu à partir de zéro pour être progressivement adoptable. La bibliothèque centrale est axée uniquement sur la couche de vue et est facile à ramasser et à intégrer avec d’autres bibliothèques ou projets existants. D’autre part, Vue est parfaitement capable d’alimenter des applications sophistiquées à une page unique lorsqu’elle est utilisée en combinaison avec l’outillage moderne et les bibliothèques de soutien.

Démarrer avec Vue nécessite simplement d’inclure son script dans un fichier HTML :

```html
<!-- development version, includes helpful console warnings -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

Avec le cadre ajouté, vous êtes alors en mesure de rendre les données déclarativement au DOM en utilisant la syntaxe de templating simple de Vue :

```html
<div id="app">
  {{ message }}
</div>
```

puis en ajoutant le script suivant:

```js
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
```

C’est suffisant pour rendre "Bonjour Vue!" sur la page. Notez, cependant, que Vue ne se contente pas de rendre le message à la div une fois. Il prend en charge la databinding `message` et les mises `<div>` à jour dynamiques de sorte que si la valeur des changements, la valeur dans le est immédiatement mis à jour pour le refléter.

Bien sûr, cela ne fait qu’effleurer la surface de ce dont Vue est capable. Il a gagné beaucoup de popularité au cours des dernières années et a une grande communauté. Il ya une [liste énorme et croissante de composants de soutien et les bibliothèques](https://github.com/vuejs/awesome-vue#redux) qui travaillent avec Vue pour l’étendre ainsi. Si vous cherchez à ajouter un comportement côté client à votre application web ou envisagez de construire une SPA complète, Vue vaut la peine d’enquêter.

### <a name="choosing-a-spa-framework"></a>Choix d’un framework SPA

Quand vous devez choisir le framework JavaScript qui convient le mieux pour prendre en charge votre SPA, tenez compte des considérations suivantes :

- Votre équipe est-elle familiarisée avec le framework et ses dépendances (y compris TypeScript dans certains cas) ?

- Quel est le degré de rigidité du framework et acceptez-vous son mode de fonctionnement par défaut ?

- Toutes les fonctionnalités nécessaires pour votre application sont-elles incluses dans le framework ou dans une bibliothèque complémentaire ?

- Est-il bien documenté?

- Sa communauté est-elle active ? De nouveaux projets sont-ils en cours de construction?

- Son équipe principale est-elle active ? Les problèmes sont-ils résolus et de nouvelles versions sont-elles publiées régulièrement ?

Les frameworks JavaScript évoluent très rapidement. Utilisez les considérations ci-dessus pour vous aider à limiter les risques en évitant de choisir un framework que vous pourriez regretter par la suite. Si vous ne voulez prendre aucun risque, choisissez un framework qui offre un support commercial et/ou est développé par une grande entreprise.

> ### <a name="references--client-web-technologies"></a>Références - Technologies web clientes
>
> - **HTML et CSS**  
> <https://www.w3.org/standards/webdesign/htmlcss>
> - **Sass vs LESS**  
> <https://www.keycdn.com/blog/sass-vs-less/>
> - **Application de styles aux applications ASP.NET Core avec LESS, Sass et Font Awesome**  
> <https://docs.microsoft.com/aspnet/core/client-side/less-sass-fa>
> - **Développement du côté client dans ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/client-side/>
> - **Jquery**  
> <https://jquery.com/>
> - **jQuery vs AngularJS**  
> <https://www.airpair.com/angularjs/posts/jquery-angularjs-comparison-migration-walkthrough>
> - **Angular**  
> <https://angular.io/>
> - **React**  
> <https://reactjs.org/>
> - **Vue**  
> <https://vuejs.org/>
> - **Angular vs React vs Vue: Quel cadre choisir en 2020**
> <https://www.codeinwp.com/blog/angular-vs-vue-vs-react/>
> - **Les cadres JavaScript haut pour le développement frontale en 2020**  
> <https://www.freecodecamp.org/news/complete-guide-for-front-end-developers-javascript-frameworks-2019/>

>[!div class="step-by-step"]
>[Suivant précédent](common-web-application-architectures.md)
>[Next](develop-asp-net-core-mvc-apps.md)
