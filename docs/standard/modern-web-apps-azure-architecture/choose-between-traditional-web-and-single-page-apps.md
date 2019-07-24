---
title: Choisir entre des applications web traditionnelles et des applications monopages
description: Apprenez à choisir entre des applications web traditionnelles et des applications monopages (SPA) quand il s’agit de créer des applications web.
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: d68c167dce791a31eeb5ca5729b50ec22c64f9b0
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331598"
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>Choisir entre des applications web traditionnelles et des applications monopages

> « Loi d’Atwood : Toute application pouvant être écrite en JavaScript sera au bout du compte écrite en JavaScript. »  
> _\- Jeff Atwood_

Aujourd’hui, vous avez le choix entre deux approches pour créer des applications web : les applications web traditionnelles qui effectuent la plupart de la logique d’application sur le serveur, et les applications monopages qui effectuent la plupart de la logique d’interface utilisateur dans un navigateur web en communiquant avec le serveur web principalement à l’aide d’API web. Une approche hybride est également possible, la plus simple étant d’héberger une ou plusieurs sous-applications de type monopage au sein d’une application web classique plus grande.

Vous devez utiliser des applications web traditionnelles quand :

- Les exigences côté client de votre application sont simples (voire même lecture seule).

- Votre application doit fonctionner dans les navigateurs sans prise en charge de JavaScript.

- Votre équipe ne connaît pas très bien les techniques de développement JavaScript ou TypeScript.

Vous devez utiliser une application monopage (SPA, Single-Page Application) quand :

- Votre application doit exposer une interface utilisateur élaborée offrant de nombreuses fonctionnalités.

- Votre équipe connaît bien les techniques de développement JavaScript et/ou TypeScript.

- Votre application doit déjà exposer une API pour d’autres clients (internes ou publics).

De plus, les frameworks SPA demandent de plus grandes connaissances en architecture et en sécurité. Elles subissent davantage de modifications que les applications web traditionnelles en raison des mises à jour fréquentes et des nouveaux frameworks. La configuration de processus de déploiement et de génération automatisés et l’utilisation d’options de déploiement telles que des conteneurs sont plus difficiles avec les applications SPA qu’avec les applications web traditionnelles.

Les améliorations de l’expérience utilisateur rendues possibles avec le modèle SPA doivent être comparées à ces considérations.

## <a name="blazor"></a>Blazor

ASP.NET Core 3.0 introduit un nouveau modèle permettant de créer une interface utilisateur riche, interactive et composable, appelée Blazor. Blazor côté serveur permet aux développeurs de générer une interface utilisateur avec Razor sur le serveur. Il permet aussi de fournir ce code au navigateur et de l’exécuter côté client à l’aide d’une bibliothèque JavaScript appelée WebAssembly. ASP.NET Core 3.0 est toujours en développement, mais vous verrez plus d’informations sur cette technologie dans la mise à jour 3.0 de ce livre électronique. Pour plus d’informations sur Blazor, consultez [Bien démarrer avec Blazor](https://blazor.net/docs/get-started.html).

## <a name="when-to-choose-traditional-web-apps"></a>Quand choisir les applications web traditionnelles

Voici une explication plus détaillée des raisons indiquées précédemment justifiant le choix des applications web traditionnelles.

**Votre application présente des exigences côté client simples, éventuellement de lecture seule**

De nombreuses applications web sont consommées principalement en lecture seule par la grande majorité de leurs utilisateurs. Les applications en lecture seule (ou principalement) ont tendance à être beaucoup plus simples que celles qui tiennent à jour et manipulent de nombreuses données d’état. Par exemple, un moteur de recherche peut être constitué d’un seul point d’entrée avec une zone de texte et d’une deuxième page pour afficher les résultats de recherche. Les utilisateurs anonymes peuvent facilement effectuer des requêtes, et peu de logique côté client est nécessaire. De même, une application publique de blog ou de système de gestion de contenu est généralement surtout constituée de contenu avec peu de comportement côté client. Il est facile de créer ce genre d’application en tant qu’application web traditionnelle basée sur serveur, qui exécute la logique sur le serveur web et restitue le code HTML à afficher dans le navigateur. Le fait que chaque page unique du site ait sa propre URL qui peut être ajoutée aux Favoris et indexée par des moteurs de recherche (par défaut, sans avoir à l’ajouter comme fonction distincte de l’application) est également un avantage évident dans de tels scénarios.

**Votre application doit fonctionner dans les navigateurs sans prise en charge de JavaScript**

Les applications web qui doivent fonctionner dans les navigateurs avec peu ou aucune prise en charge de JavaScript doivent être écrites à l’aide de workflows d’applications web traditionnelles (ou au moins être en mesure de revenir à un comportement de ce type). Les applications SPA nécessitent JavaScript côté client pour pouvoir fonctionner. S’il n’est pas disponible, elles ne constituent pas un bon choix.

**Votre équipe ne connaît pas très bien les techniques de développement JavaScript ou TypeScript**

Si votre équipe ne connaît pas bien JavaScript ou TypeScript, mais sait comment développer des applications web côté serveur, elle pourra probablement générer une application web traditionnelle plus rapidement qu’une application SPA. Les applications web traditionnelles sont un choix plus productif pour les équipes qui ont l’habitude de créer ce genre d’application, à moins que l’apprentissage de la programmation d’applications SPA soit un objectif ou que l’expérience utilisateur offerte par une application SPA soit absolument nécessaire.

## <a name="when-to-choose-spas"></a>Quand choisir des applications SPA

Voici une explication plus détaillée précisant quand il est préférable de choisir un style de développement d’application monopage pour votre application web.

**Votre application doit exposer une interface utilisateur élaborée offrant de nombreuses fonctionnalités**

Les applications SPA peuvent prendre en charge des fonctionnalités avancées côté client qui ne nécessitent pas le rechargement de la page quand les utilisateurs effectuent des actions ou naviguent parmi les zones de l’application. Les applications SPA peuvent se charger plus rapidement et récupérer des données en arrière-plan, et les différentes actions utilisateur sont plus réactives car les rechargements de page complète sont rares. Les applications SPA peuvent prendre en charge les mises à jour incrémentielles, l’enregistrement de formulaires ou de documents partiellement remplis sans que l’utilisateur ne doive cliquer sur un bouton pour envoyer un formulaire. Les applications SPA peuvent prendre en charge des comportements avancés côté client, tels que le glisser-déplacer, beaucoup plus facilement que les applications traditionnelles. Les applications SPA peuvent être conçues pour s’exécuter en mode déconnecté afin d’effectuer des mises à jour d’un modèle côté client qui sont par la suite synchronisées sur le serveur une fois qu’une connexion a été rétablie. Vous devez choisir une application de style SPA si les exigences de votre application incluent des fonctionnalités avancées qui vont au-delà de celles offertes par les formulaires HTML classiques.

Notez que souvent les applications SPA doivent implémenter des fonctionnalités qui sont intégrées aux applications web traditionnelles, comme l’affichage d’une URL significative dans la barre d’adresse reflétant l’opération en cours (et permettant aux utilisateurs de créer un Favori ou un lien ciblé afin de pouvoir revenir à cette URL). Les applications SPA doivent aussi permettre aux utilisateurs de cliquer sur les boutons Précédent et Suivant du navigateur avec des résultats auxquels ils doivent s’attendre.

**Votre équipe connaît bien les techniques de développement JavaScript et/ou TypeScript**

L’écriture d’applications SPA nécessite une bonne connaissance des bibliothèques et des techniques de programmation côté client et JavaScript et/ou TypeScript. Votre équipe doit savoir écrire du code JavaScript moderne à l’aide d’un framework SPA comme Angular.

> ### <a name="references--spa-frameworks"></a>Références – Frameworks de SPA
>
> - **Angular**  
>   <https://angular.io>
> - **Comparaison des frameworks JavaScript**  
>   <https://jsreport.io/the-ultimate-guide-to-javascript-frameworks/>

**Votre application doit déjà exposer une API pour d’autres clients (internes ou publics)**

Si vous prenez déjà en charge une API web pour une utilisation par d’autres clients, il peut être plus facile de créer une implémentation de SPA qui tire parti de ces API, plutôt que de reproduire la logique côté serveur. Les applications SPA utilisent beaucoup les API web pour interroger et mettre à jour des données quand les utilisateurs interagissent avec l’application.

## <a name="decision-table--traditional-web-or-spa"></a>Tableau de décision – Application web traditionnelle ou SPA

Le tableau de décision ci-dessous récapitule certains facteurs à prendre en compte lors du choix entre une application web traditionnelle et une application monopage.

| **Facteur**                                           | **Application web traditionnelle** | **Application à une seule page** |
| ---------------------------------------------------- | ----------------------- | --------------------------- |
| Connaissances de l’équipe de JavaScript/TypeScript | **Minimale**             | **Obligatoire**                |
| Prise en charge des navigateurs sans script                   | **Prise en charge**           | **Pas de prise en charge**           |
| Comportement d’application côté client minimal             | **Adapté**         | **Non adapté**                |
| Exigences d’une interface utilisateur riche et complexe            | **Limité**             | **Adapté**             |

>[!div class="step-by-step"]
>[Précédent](modern-web-applications-characteristics.md)
>[Suivant](architectural-principles.md)
