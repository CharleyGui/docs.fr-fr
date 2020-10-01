---
title: Caractéristiques des applications web modernes
description: Architecturer des applications web modernes avec ASP.NET Core et Azure | Caractéristiques des applications web modernes
author: ardalis
ms.author: wiwagn
no-loc:
- Blazor
- WebAssembly
ms.date: 12/04/2019
ms.openlocfilehash: 6241a9a3a51bd4d5228841caeaf3a7b652fc6eaa
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608359"
---
# <a name="characteristics-of-modern-web-applications"></a>Caractéristiques des applications web modernes

> "… avec une bonne conception, les fonctionnalités sont peu coûteuses. Cette approche est compliquée, mais continue à porter ses fruits. »  
> _\- Ritchie Denis_

Les attentes et les exigences des utilisateurs vis-à-vis des applications web modernes n’ont jamais été aussi élevées. Les applications web d’aujourd’hui sont censées être disponibles 24 heures sur 24, sept jours sur sept, depuis n’importe où dans le monde, et être utilisables avec presque n’importe quel appareil ou taille d’écran. Elles doivent être sécurisées, flexibles et scalables afin de répondre aux pics de demande. De plus en plus, des scénarios complexes doivent être gérés par des expériences utilisateur complexes générées sur le client à l’aide de JavaScript et qui communiquent efficacement par le biais d’API web.

ASP.NET Core est optimisé pour les applications web modernes et les scénarios d’hébergement cloud. Grâce à sa conception modulaire, les applications dépendent uniquement des fonctionnalités qu’elles utilisent réellement, ce qui améliore les performances et la sécurité de l’application tout en réduisant les besoins en ressources d’hébergement.

## <a name="reference-application-eshoponweb"></a>Application de référence : eShopOnWeb

Ce guide comprend une application de référence, _eShopOnWeb_, qui illustre certains principes et recommandations. L’application est un magasin en ligne simple qui prend en charge la navigation dans un catalogue de chemises, tasses à café et autres articles marketing. Cette application de référence est délibérément simple afin de la rendre facile à comprendre.

![eShopOnWeb](./media/image2-1.png)

**Figure 2-1.** eShopOnWeb

> ### <a name="reference-application"></a>Application de référence
>
> - **eShopOnWeb**  
>   <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>Hébergées dans le cloud et scalables

ASP.NET Core est optimisé pour le cloud (cloud public, cloud privé, n’importe quel cloud), car il consomme peu de mémoire et offre un débit élevé. Le plus petit encombrement des applications ASP.NET Core signifie que vous pouvez en héberger plus sur le même matériel et vous payez pour moins de ressources lors de l’utilisation de services d’hébergement cloud avec paiement à l’utilisation. Le débit plus élevé signifie que vous pouvez servir davantage de clients à partir d’une application avec le même matériel, réduisant ainsi la nécessité d’investir dans des serveurs et une infrastructure d’hébergement.

## <a name="cross-platform"></a>Multiplateforme

ASP.NET Core est multiplateforme et peut s’exécuter sur Linux, macOS et Windows. Cela ouvre de nombreuses nouvelles options pour le développement et le déploiement d’applications générées avec ASP.NET Core. Les conteneurs Docker, qu’ils exécutent Linux ou Windows, peuvent héberger des applications ASP.NET Core, ce qui leur permet de tirer parti des avantages offerts par les [conteneurs et microservices](../microservices/index.md).

## <a name="modular-and-loosely-coupled"></a>Faiblement couplées et modulaires

Les packages NuGet sont des citoyens de première classe dans .NET Core, et les applications ASP.NET Core sont composées de nombreuses bibliothèques par le biais de NuGet. Avec ce niveau de granularité des fonctionnalités, les applications dépendent uniquement des fonctionnalités dont elles ont réellement besoin et déploient uniquement ces fonctionnalités, réduisant ainsi leur encombrement et leur surface d’exposition de vulnérabilité de sécurité.

ASP.NET Core prend également entièrement en charge l' [injection de dépendances](https://deviq.com/dependency-injection/), à la fois en interne et au niveau de l’application. Les interfaces peuvent avoir plusieurs implémentations qui peuvent être échangées en fonction des besoins. L’injection de dépendances permet aux applications d’être faiblement couplées avec ces interfaces, plutôt qu’avec des implémentations spécifiques, ce qui les rend plus faciles à étendre, mettre à jour et tester.

## <a name="easily-tested-with-automated-tests"></a>Facilement testées avec des tests automatisés

Les applications ASP.NET Core prennent en charge les tests unitaires, et leur faible couplage et leur prise en charge de l’injection de dépendances facilitent le remplacement des infrastructures à problème par des implémentations factices à des fins de test. ASP.NET Core est également fourni avec un TestServer qui peut être utilisé pour héberger des applications en mémoire. Des tests fonctionnels peuvent ensuite effectuer des demandes à ce serveur en mémoire en testant la pile d’application complète (notamment les middlewares, le routage, la liaison de modèle, les filtres, etc.) et en recevant une réponse, tout ceci en une fraction du temps qui serait nécessaire pour héberger l’application sur un serveur réel et effectuer des demandes par le biais de la couche réseau. Ces tests sont particulièrement faciles à écrire et utiles pour les API, qui sont de plus en plus importantes dans les applications web modernes.

## <a name="traditional-and-spa-behaviors-supported"></a>Comportements des applications traditionnelles et SPA pris en charge

Les applications web traditionnelles impliquent peu de comportement côté client, mais repose sur le serveur pour la navigation, les requêtes et les mises à jour que l’application peut avoir besoin d’effectuer. Chaque nouvelle opération effectuée par l’utilisateur se traduit par une nouvelle requête web, le résultat étant un rechargement complet de la page dans le navigateur de l’utilisateur final. Les frameworks MVC (Model-View-Controller) classiques suivent généralement cette approche, chaque nouvelle requête correspondant à une action de contrôleur différente, qui à son tour fonctionne avec un modèle et retourne une vue. Certaines opérations individuelles dans une page donnée peuvent être améliorées avec des fonctionnalités AJAX (Asynchronous JavaScript and XML), mais l’architecture globale de l’application utilise de nombreuses vues MVC et points de terminaison d’URL différents. De plus, ASP.NET Core MVC prend également en charge Razor Pages, un moyen plus simple d’organiser les pages de style MVC.

Les applications monopages (SPA, Single-Page Applications), en revanche, impliquent très peu de chargements de page côté serveur générés de manière dynamique (voire aucun). De nombreuses applications monopages sont initialisées dans un fichier HTML statique qui charge les bibliothèques JavaScript nécessaires pour démarrer et exécuter l’application. Ces applications utilisent de manière intensive des API web pour leurs besoins en données, et peuvent fournir des expériences utilisateur beaucoup plus riches.

De nombreuses applications web impliquent une combinaison des comportements d’application web traditionnelle (en général pour le contenu) et d’application SPA (pour l’interactivité). ASP.NET Core prend en charge les API web et MVC (basées sur les vues ou les pages) dans la même application, en utilisant le même ensemble d’outils et de bibliothèques de framework sous-jacentes.

## <a name="simple-development-and-deployment"></a>Développement et déploiement simples

ASP.NET Core applications peuvent être écrites à l’aide d’éditeurs de texte et d’interfaces de ligne de commande simples, ou d’environnements de développement complets tels que Visual Studio. Les applications monolithiques sont généralement déployées sur un seul point de terminaison. Les déploiements peuvent facilement être automatisés et faire partie d’un pipeline d’intégration continue (CI) et de livraison continue (CD). Outre les outils CI/CD traditionnels, Microsoft Azure a intégré la prise en charge des dépôts Git et peut déployer automatiquement les mises à jour à mesure qu’elles sont effectuées sur une branche ou une étiquette git spécifiée. Azure DevOps fournit un pipeline de déploiement et de création d’intégration continue et de CD complet, et les actions GitHub fournissent une autre option pour les projets hébergés ici.

## <a name="traditional-aspnet-and-web-forms"></a>ASP.NET traditionnel et Web Forms

En plus d’ASP.NET Core, la plateforme ASP.NET 4.x traditionnelle reste robuste et fiable pour la création d’applications web. ASP.NET prend en charge les modèles de développement d’API Web et MVC, ainsi que Web Forms, ce qui est bien adapté au développement d’applications basées sur des pages riches et aux fonctionnalités d’un écosystème de composants tiers riche. Microsoft Azure offre une excellente prise en charge des applications ASP.NET 4. x, et de nombreux développeurs connaissent cette plateforme.

## Blazor

Blazor est inclus avec ASP.NET Core 3,0 et versions ultérieures. Il fournit un nouveau mécanisme pour créer des applications clientes Web interactives riches à l’aide de Razor, C# et ASP.NET Core. Il offre une autre solution à prendre en compte lors du développement d’applications Web modernes. Il existe deux versions de Blazor à prendre en compte : côté serveur et côté client.

Le côté serveur Blazor a été publié dans 2019 avec ASP.NET Core 3,0. Comme son nom l’indique, il s’exécute sur le serveur et restitue les modifications apportées au document client dans le navigateur via le réseau. Côté serveur Blazor fournit une expérience client riche sans nécessiter de code JavaScript côté client et sans nécessiter de chargement de page distinct pour chaque interaction de page client. Les modifications apportées à la page chargée sont demandées et traitées par le serveur, puis renvoyées au client à l’aide de Signalr.

Le côté client Blazor libéré en mai 2020 élimine le besoin d’afficher les modifications sur le serveur. Au lieu de cela, il s’appuie WebAssembly sur pour exécuter du code .net au sein du client. Le client peut toujours effectuer des appels d’API au serveur si nécessaire pour demander des données, mais tous les comportements côté client s’exécutent sur le client via WebAssembly , qui est déjà pris en charge par tous les principaux navigateurs et n’est qu’une bibliothèque JavaScript.

> ### <a name="references--modern-web-applications"></a>Informations de référence sur les applications web modernes
>
> - **Introduction à ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/>
> - **Test dans ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - **Blazor -Prise en main**  
>   <https://blazor.net/docs/get-started.html>

>[!div class="step-by-step"]
>[Précédent](index.md) 
> [Suivant](choose-between-traditional-web-and-single-page-apps.md)
