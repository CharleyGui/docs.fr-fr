---
title: Choisir entre des applications web traditionnelles et des applications monopages
description: Apprenez à choisir entre des applications web traditionnelles et des applications monopages (SPA) quand il s’agit de créer des applications web.
author: ardalis
ms.author: wiwagn
no-loc:
- Blazor
- WebAssembly
ms.date: 12/01/2020
ms.openlocfilehash: c29e58fb4c748d6025b7c2fbe62a54a85cc71fba
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851651"
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>Choisir entre des applications web traditionnelles et des applications monopages

> « Loi d’Atwood : Toute application pouvant être écrite en JavaScript sera au bout du compte écrite en JavaScript. »  
> _\- Jeff Atwood_

Il existe aujourd’hui deux approches générales pour la création d’applications Web : les applications Web traditionnelles qui effectuent la majeure partie de la logique d’application sur le serveur et les applications à page unique (SPAs) qui exécutent la majeure partie de la logique de l’interface utilisateur dans un navigateur Web, en communiquant avec le serveur Web principalement à l’aide d’API Web. Une approche hybride est également possible, la plus simple hébergeant une ou plusieurs sous-applications de type SPA riches au sein d’une plus grande application Web traditionnelle.

Utilisez des applications Web traditionnelles dans les cas suivants :

- Les exigences côté client de votre application sont simples (voire même lecture seule).

- Votre application doit fonctionner dans les navigateurs sans prise en charge de JavaScript.

- Votre équipe ne connaît pas très bien les techniques de développement JavaScript ou TypeScript.

Utilisez un SPA dans les cas suivants :

- Votre application doit exposer une interface utilisateur élaborée offrant de nombreuses fonctionnalités.

- Votre équipe connaît bien JavaScript, la machine à écrire ou le Blazor WebAssembly développement.

- Votre application doit déjà exposer une API pour d’autres clients (internes ou publics).

De plus, les frameworks SPA demandent de plus grandes connaissances en architecture et en sécurité. Elles subissent davantage de modifications que les applications web traditionnelles en raison des mises à jour fréquentes et des nouveaux frameworks. La configuration de processus de génération et de déploiement automatisés et l’utilisation d’options de déploiement comme les conteneurs peuvent être plus difficiles avec les applications de SPA que les applications Web traditionnelles.

Les améliorations de l’expérience utilisateur rendues possibles par l’approche SPA doivent être comparées à ces considérations.

## Blazor

ASP.NET Core comprend un modèle pour créer des interfaces utilisateur riches, interactives et composables appelées Blazor . Blazor côté serveur, les développeurs peuvent créer une interface utilisateur avec C# et Razor sur le serveur et pour que l’interface utilisateur soit connectée de manière interactive au navigateur en temps réel à l’aide d’une connexion Signalr persistante. BlazorWebAssemblyintroduit une autre option pour les Blazor applications, ce qui leur permet de s’exécuter dans le navigateur à l’aide de WebAssembly . Étant donné qu’il s’agit de .NET en cours d’exécution sur WebAssembly , vous pouvez réutiliser le code et les bibliothèques à partir de parties côté serveur de votre application.

Blazor fournit une nouvelle option, troisième option, à prendre en compte lors de l’évaluation de la nécessité de créer une application Web entièrement rendue serveur ou un SPA. Vous pouvez créer des comportements côté client riches en mode SPA à l’aide de Blazor , sans avoir besoin d’un développement JavaScript significatif. Blazor les applications peuvent appeler des API pour demander des données ou effectuer des opérations côté serveur. Ils peuvent interagir avec JavaScript quand cela est nécessaire pour tirer parti des bibliothèques et des infrastructures JavaScript.

Envisagez de créer votre application Web avec Blazor lorsque :

- Votre application doit exposer une interface utilisateur riche

- Votre équipe est plus à l’aise avec le développement .NET que le développement JavaScript ou de machine à écrire

Si vous avez une application Web Forms existante que vous envisagez de migrer vers .NET Core ou le .NET le plus récent, vous souhaiterez peut-être consulter le livre électronique gratuit, [ Blazor pour Web Forms aux développeurs](../blazor-for-web-forms-developers/index.md) de voir s’il est judicieux de les migrer vers Blazor .

Pour plus d’informations sur Blazor , consultez la page [prise en main Blazor de ](https://blazor.net/docs/get-started.html).

## <a name="when-to-choose-traditional-web-apps"></a>Quand choisir les applications web traditionnelles

La section suivante est une explication plus détaillée des raisons indiquées précédemment pour choisir des applications Web traditionnelles.

**Votre application présente des exigences côté client simples, éventuellement de lecture seule**

De nombreuses applications web sont consommées principalement en lecture seule par la grande majorité de leurs utilisateurs. Les applications en lecture seule (ou essentiellement en lecture) ont tendance à être beaucoup plus simples que les applications qui maintiennent et manipulent un grand nombre d’États. Par exemple, un moteur de recherche peut être constitué d’un seul point d’entrée avec une zone de texte et d’une deuxième page pour afficher les résultats de recherche. Les utilisateurs anonymes peuvent facilement effectuer des requêtes, et peu de logique côté client est nécessaire. De même, une application publique de blog ou de système de gestion de contenu est généralement surtout constituée de contenu avec peu de comportement côté client. De telles applications sont facilement créées en tant qu’applications Web serveur traditionnelles, qui exécutent la logique sur le serveur Web et restituent le code HTML à afficher dans le navigateur. Le fait que chaque page unique du site ait sa propre URL qui peut être marquée et indexée par les moteurs de recherche (par défaut, sans qu’il soit nécessaire d’ajouter cette fonctionnalité en tant que fonctionnalité distincte de l’application) est également un avantage évident dans ces scénarios.

**Votre application doit fonctionner dans les navigateurs sans prise en charge de JavaScript**

Les applications web qui doivent fonctionner dans les navigateurs avec peu ou aucune prise en charge de JavaScript doivent être écrites à l’aide de workflows d’applications web traditionnelles (ou au moins être en mesure de revenir à un comportement de ce type). Les applications SPA nécessitent JavaScript côté client pour pouvoir fonctionner. S’il n’est pas disponible, elles ne constituent pas un bon choix.

**Votre équipe ne connaît pas les techniques de développement JavaScript ou de machine à écrire**

Si votre équipe ne connaît pas bien JavaScript ou TypeScript, mais sait comment développer des applications web côté serveur, elle pourra probablement générer une application web traditionnelle plus rapidement qu’une application SPA. Les applications web traditionnelles sont un choix plus productif pour les équipes qui ont l’habitude de créer ce genre d’application, à moins que l’apprentissage de la programmation d’applications SPA soit un objectif ou que l’expérience utilisateur offerte par une application SPA soit absolument nécessaire.

## <a name="when-to-choose-spas"></a>Quand choisir des applications SPA

La section suivante est une explication plus détaillée de la façon de choisir un style de développement d’applications à page unique pour votre application Web.

**Votre application doit exposer une interface utilisateur élaborée offrant de nombreuses fonctionnalités**

Les applications SPA peuvent prendre en charge des fonctionnalités avancées côté client qui ne nécessitent pas le rechargement de la page quand les utilisateurs effectuent des actions ou naviguent parmi les zones de l’application. Les applications SPA peuvent se charger plus rapidement et récupérer des données en arrière-plan, et les différentes actions utilisateur sont plus réactives car les rechargements de page complète sont rares. Les applications SPA peuvent prendre en charge les mises à jour incrémentielles, l’enregistrement de formulaires ou de documents partiellement remplis sans que l’utilisateur ne doive cliquer sur un bouton pour envoyer un formulaire. Les applications SPA peuvent prendre en charge des comportements avancés côté client, tels que le glisser-déplacer, beaucoup plus facilement que les applications traditionnelles. Les applications SPA peuvent être conçues pour s’exécuter en mode déconnecté afin d’effectuer des mises à jour d’un modèle côté client qui sont par la suite synchronisées sur le serveur une fois qu’une connexion a été rétablie. Choisissez une application de type SPA si les exigences de votre application incluent des fonctionnalités riches qui vont au-delà de ce que proposent les formulaires HTML standard.

En général, la commande à la fois doit implémenter des fonctionnalités qui sont intégrées à des applications Web traditionnelles, telles que l’affichage d’une URL significative dans la barre d’adresses reflétant l’opération en cours (et la possibilité pour les utilisateurs de créer des signets ou des liens détaillés vers cette URL pour y revenir). Les applications SPA doivent aussi permettre aux utilisateurs de cliquer sur les boutons Précédent et Suivant du navigateur avec des résultats auxquels ils doivent s’attendre.

**Votre équipe connaît le développement JavaScript et/ou la machine à écrire**

L’écriture d’applications SPA nécessite une bonne connaissance des bibliothèques et des techniques de programmation côté client et JavaScript et/ou TypeScript. Votre équipe doit savoir écrire du code JavaScript moderne à l’aide d’un framework SPA comme Angular.

> ### <a name="references--spa-frameworks"></a>Références – Frameworks de SPA
>
> - **Angular**  
>   <https://angular.io>
> - **Réagir**
>   <https://reactjs.org/>
> - **Comparaison des frameworks JavaScript**  
>   <https://jsreport.io/the-ultimate-guide-to-javascript-frameworks/>

**Votre application doit déjà exposer une API pour d’autres clients (internes ou publics)**

Si vous prenez déjà en charge une API web pour une utilisation par d’autres clients, il peut être plus facile de créer une implémentation de SPA qui tire parti de ces API, plutôt que de reproduire la logique côté serveur. Les applications SPA utilisent beaucoup les API web pour interroger et mettre à jour des données quand les utilisateurs interagissent avec l’application.

## <a name="when-to-choose-no-locblazor"></a>Quand choisir Blazor

La section suivante est une explication plus détaillée du moment où choisir Blazor pour votre application Web.

**Votre application doit exposer une interface utilisateur riche**

Comme pour les applications basées sur JavaScript, les Blazor applications peuvent prendre en charge le comportement de client riche sans rechargements de pages. Ces applications sont plus réactives aux utilisateurs et récupèrent uniquement les données (ou HTML) requises pour répondre à une interaction utilisateur donnée. Conçu correctement, les applications côté serveur Blazor peuvent être configurées pour s’exécuter en tant qu’applications côté client Blazor avec des modifications minimes une fois cette fonctionnalité prise en charge.

**Votre équipe est plus à l’aise avec le développement .NET que le développement JavaScript ou de machine à écrire**

De nombreux développeurs sont plus productifs avec .NET et Razor qu’avec les langages côté client tels que JavaScript ou la machine à écrire. Étant donné que le côté serveur de l’application est déjà en cours de développement avec .NET, l’utilisation de Blazor garantit que chaque développeur .net de l’équipe puisse comprendre et générer potentiellement le comportement de la partie frontale de l’application.

## <a name="decision-table"></a>Table de décision

Le tableau de décision suivant résume certains des facteurs de base à prendre en compte lors du choix entre une application Web traditionnelle, un SPA ou une Blazor application.

| **Factor**                                           | **Application web traditionnelle** | **Application à une seule page** | **Blazor Lancement**  |
| ---------------------------------------------------- | ----------------------- | --------------------------- | --------------- |
| Connaissances de l’équipe de JavaScript/TypeScript | **Minimal**             | **Obligatoire**                | **Minimal**     |
| Prise en charge des navigateurs sans script                   | **Pris en charge**           | **Non pris en charge**           | **Pris en charge**   |
| Comportement d’application côté client minimal             | **Adapté**         | **Non adapté**                | **Viabilité**      |
| Exigences d’une interface utilisateur riche et complexe            | **Limité**             | **Adapté**             | **Adapté** |

>[!div class="step-by-step"]
>[Précédent](modern-web-applications-characteristics.md) 
> [Suivant](architectural-principles.md)
