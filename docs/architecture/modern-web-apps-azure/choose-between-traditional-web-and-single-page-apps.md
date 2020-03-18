---
title: Choisir entre des applications web traditionnelles et des applications monopages
description: Apprenez à choisir entre des applications web traditionnelles et des applications monopages (SPA) quand il s’agit de créer des applications web.
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: d4ed76455001c1a0b8e2e2f1bb90ce8715dd0052
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77450106"
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>Choisir entre des applications web traditionnelles et des applications monopages

> « Loi d’Atwood : Toute application pouvant être écrite en JavaScript sera au bout du compte écrite en JavaScript. »  
> _\-Jeff Atwood_

Aujourd’hui, vous avez le choix entre deux approches pour créer des applications web : les applications web traditionnelles qui effectuent la plupart de la logique d’application sur le serveur, et les applications monopages qui effectuent la plupart de la logique d’interface utilisateur dans un navigateur web en communiquant avec le serveur web principalement à l’aide d’API web. Une approche hybride est également possible, le plus simple étant l’hôte d’une ou plusieurs riches sous-applications SPA-like au sein d’une application web traditionnelle plus grande.

Utilisez des applications Web traditionnelles lorsque :

- Les exigences côté client de votre application sont simples (voire même lecture seule).

- Votre application doit fonctionner dans les navigateurs sans prise en charge de JavaScript.

- Votre équipe ne connaît pas très bien les techniques de développement JavaScript ou TypeScript.

Utilisez un SPA lorsque :

- Votre application doit exposer une interface utilisateur élaborée offrant de nombreuses fonctionnalités.

- Votre équipe connaît bien les techniques de développement JavaScript et/ou TypeScript.

- Votre application doit déjà exposer une API pour d’autres clients (internes ou publics).

De plus, les frameworks SPA demandent de plus grandes connaissances en architecture et en sécurité. Elles subissent davantage de modifications que les applications web traditionnelles en raison des mises à jour fréquentes et des nouveaux frameworks. La configuration des processus automatisés de construction et de déploiement et l’utilisation d’options de déploiement comme les conteneurs peuvent être plus difficiles avec les applications SPA que les applications Web traditionnelles.

Les améliorations apportées à l’expérience utilisateur rendues possibles par l’approche SPA doivent être évaluées par rapport à ces considérations.

## <a name="blazor"></a>Blazor

ASP.NET Core 3.0 introduit un nouveau modèle permettant de créer une interface utilisateur riche, interactive et composable, appelée Blazor. Blazor côté serveur permet aux développeurs de construire l’interface utilisateur avec Razor sur le serveur et pour ce code d’être livré au navigateur et exécuté côté client en utilisant [WebAssembly](https://webassembly.org/). Blazor côté serveur est disponible dès maintenant avec ASP.NET Core 3.0 ou plus tard. Blazor client-côté devrait être disponible en 2020.

Blazor offre une nouvelle, troisième option à considérer lors de l’évaluation de la construction d’une application Web purement axée sur le serveur ou un SPA. Vous pouvez construire des comportements riches, côté client spa-comme en utilisant Blazor, sans avoir besoin d’un développement JavaScript significatif. Les applications Blazor peuvent appeler des API pour demander des données ou effectuer des opérations côté serveur.

Envisagez de construire votre application web avec Blazor lorsque :

- Votre application doit exposer une interface utilisateur riche

- Votre équipe est plus à l’aise avec le développement .NET que le développement JavaScript ou TypeScript

Pour plus d’informations sur Blazor, consultez [Bien démarrer avec Blazor](https://blazor.net/docs/get-started.html).

## <a name="when-to-choose-traditional-web-apps"></a>Quand choisir les applications web traditionnelles

Voici une explication plus détaillée des raisons indiquées précédemment justifiant le choix des applications web traditionnelles.

**Votre application présente des exigences côté client simples, éventuellement de lecture seule**

De nombreuses applications web sont consommées principalement en lecture seule par la grande majorité de leurs utilisateurs. Les applications en lecture seule (ou principalement) ont tendance à être beaucoup plus simples que celles qui tiennent à jour et manipulent de nombreuses données d’état. Par exemple, un moteur de recherche peut être constitué d’un seul point d’entrée avec une zone de texte et d’une deuxième page pour afficher les résultats de recherche. Les utilisateurs anonymes peuvent facilement effectuer des requêtes, et peu de logique côté client est nécessaire. De même, une application publique de blog ou de système de gestion de contenu est généralement surtout constituée de contenu avec peu de comportement côté client. Ces applications sont facilement conçues comme des applications Web traditionnelles basées sur le serveur, qui exécutent la logique sur le serveur Web et rendent HTML pour être affichées dans le navigateur. Le fait que chaque page unique du site ait sa propre URL qui peut être ajoutée aux Favoris et indexée par des moteurs de recherche (par défaut, sans avoir à l’ajouter comme fonction distincte de l’application) est également un avantage évident dans de tels scénarios.

**Votre application doit fonctionner dans les navigateurs sans support JavaScript**

Les applications web qui doivent fonctionner dans les navigateurs avec peu ou aucune prise en charge de JavaScript doivent être écrites à l’aide de workflows d’applications web traditionnelles (ou au moins être en mesure de revenir à un comportement de ce type). Les applications SPA nécessitent JavaScript côté client pour pouvoir fonctionner. S’il n’est pas disponible, elles ne constituent pas un bon choix.

**Votre équipe n’est pas familière avec les techniques de développement JavaScript ou TypeScript**

Si votre équipe ne connaît pas bien JavaScript ou TypeScript, mais sait comment développer des applications web côté serveur, elle pourra probablement générer une application web traditionnelle plus rapidement qu’une application SPA. Les applications web traditionnelles sont un choix plus productif pour les équipes qui ont l’habitude de créer ce genre d’application, à moins que l’apprentissage de la programmation d’applications SPA soit un objectif ou que l’expérience utilisateur offerte par une application SPA soit absolument nécessaire.

## <a name="when-to-choose-spas"></a>Quand choisir des applications SPA

Voici une explication plus détaillée précisant quand il est préférable de choisir un style de développement d’application monopage pour votre application web.

**Votre application doit exposer une interface utilisateur élaborée offrant de nombreuses fonctionnalités**

Les applications SPA peuvent prendre en charge des fonctionnalités avancées côté client qui ne nécessitent pas le rechargement de la page quand les utilisateurs effectuent des actions ou naviguent parmi les zones de l’application. Les applications SPA peuvent se charger plus rapidement et récupérer des données en arrière-plan, et les différentes actions utilisateur sont plus réactives car les rechargements de page complète sont rares. Les applications SPA peuvent prendre en charge les mises à jour incrémentielles, l’enregistrement de formulaires ou de documents partiellement remplis sans que l’utilisateur ne doive cliquer sur un bouton pour envoyer un formulaire. Les applications SPA peuvent prendre en charge des comportements avancés côté client, tels que le glisser-déplacer, beaucoup plus facilement que les applications traditionnelles. Les applications SPA peuvent être conçues pour s’exécuter en mode déconnecté afin d’effectuer des mises à jour d’un modèle côté client qui sont par la suite synchronisées sur le serveur une fois qu’une connexion a été rétablie. Choisissez une application de type SPA si les exigences de votre application incluent des fonctionnalités riches qui vont au-delà de ce que les formulaires HTML typiques offrent.

Fréquemment, les SPA doivent implémenter des fonctionnalités intégrées aux applications Web traditionnelles, telles que l’affichage d’une URL significative dans la barre d’adresse reflétant l’opération actuelle (et permettant aux utilisateurs de marquer ou un lien profond vers cette URL pour y revenir). Les applications SPA doivent aussi permettre aux utilisateurs de cliquer sur les boutons Précédent et Suivant du navigateur avec des résultats auxquels ils doivent s’attendre.

**Votre équipe est familière avec le développement JavaScript et/ou TypeScript**

L’écriture d’applications SPA nécessite une bonne connaissance des bibliothèques et des techniques de programmation côté client et JavaScript et/ou TypeScript. Votre équipe doit savoir écrire du code JavaScript moderne à l’aide d’un framework SPA comme Angular.

> ### <a name="references--spa-frameworks"></a>Références – Frameworks de SPA
>
> - **Angular**  
>   <https://angular.io>
> - **Réagir**
>   <https://reactjs.org/>
> - **Comparaison des frameworks JavaScript**  
>   <https://jsreport.io/the-ultimate-guide-to-javascript-frameworks/>

**Votre demande doit déjà exposer une API pour d’autres clients (internes ou publics)**

Si vous prenez déjà en charge une API web pour une utilisation par d’autres clients, il peut être plus facile de créer une implémentation de SPA qui tire parti de ces API, plutôt que de reproduire la logique côté serveur. Les applications SPA utilisent beaucoup les API web pour interroger et mettre à jour des données quand les utilisateurs interagissent avec l’application.

## <a name="when-to-choose-blazor"></a>Quand choisir Blazor

Ce qui suit est une explication plus détaillée du moment où choisir Blazor pour votre application web.

**Votre application doit exposer une interface utilisateur riche**

Comme les SPAs basés sur JavaScript, les applications Blazor peuvent prendre en charge un comportement client riche sans rechargement de page. Ces applications sont plus sensibles aux utilisateurs, ne récupérant que les données (ou HTML) nécessaires pour répondre à une interaction utilisateur donnée. Conçues correctement, les applications Blazor côté serveur peuvent être configurées pour fonctionner en tant qu’applications Blazor côté client avec un minimum de modifications une fois cette fonctionnalité prise en charge.

**Votre équipe est plus à l’aise avec le développement .NET que le développement JavaScript ou TypeScript**

Beaucoup de développeurs sont plus productifs avec .NET et Razor qu’avec des langues côté client comme JavaScript ou TypeScript. Étant donné que le côté serveur de l’application est déjà en cours de développement avec .NET, en utilisant Blazor assure que chaque développeur .NET de l’équipe peut comprendre et potentiellement construire le comportement de l’extrémité avant de l’application.

## <a name="decision-table"></a>Tableau de décision

Le tableau de décision suivant résume certains des facteurs de base à prendre en considération lors du choix entre une application Web traditionnelle, une SPA ou une application Blazor.

| **Factor**                                           | **Application web traditionnelle** | **Applications monopage** | **Application Blazor**  |
| ---------------------------------------------------- | ----------------------- | --------------------------- | --------------- |
| Connaissances de l’équipe de JavaScript/TypeScript | **Minimales**             | **Obligatoire**                | **Minimales**     |
| Prise en charge des navigateurs sans script                   | **Soutenu**           | **Non pris en charge**           | **Soutenu**   |
| Comportement d’application côté client minimal             | **Adapté**         | **Non adapté**                | **Viable**      |
| Exigences d’une interface utilisateur riche et complexe            | **Limitée**             | **Adapté**             | **Adapté** |

>[!div class="step-by-step"]
>[Suivant précédent](modern-web-applications-characteristics.md)
>[Next](architectural-principles.md)
