---
title: Microservices .NET. Architecture pour les applications .NET en conteneur
description: Architecture des microservices .NET pour les applications .NET en conteneur | Les microservices sont des services modulables qui peuvent se déployer indépendamment. Les conteneurs Docker (pour Linux et Windows) simplifient le déploiement et les tests en regroupant un service et ses dépendances dans une seule unité, laquelle est ensuite exécutée dans un environnement isolé.
ms.date: 01/07/2019
ms.openlocfilehash: a348a9c122ef7f0293a1385aa05dc98f61deab7e
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66195973"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a>Microservices .NET : Architecture pour les applications .NET en conteneur

![Couverture de livre](./media/cover-small.png)

**ÉDITION v2.2.00** – Mise à jour vers ASP.NET Core 2.2

Ce guide est une introduction au développement d’applications basées sur les microservices et à la gestion de celles-ci au moyen de conteneurs. Il traite de la conception architecturale et des approches d’implémentation utilisant .NET Core et les conteneurs Docker. 

Pour faciliter la prise en main, ce guide met en lumière une application de référence en conteneur basée sur des microservices que vous pouvez explorer. L’application de référence est disponible sur le dépôt GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).

## <a name="action-links"></a>Liens d'action

* Téléchargez ce livre électronique au format de votre choix : | [PDF](https://aka.ms/microservicesebook) | [MOBI](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-epub) |

* Clonez/dupliquez (fork) l’application de référence [eShopOnContainers sur GitHub](https://github.com/dotnet-architecture/eShopOnContainers)
 
* Regardez la [vidéo d’introduction sur Channel 9](https://aka.ms/microservices-video)

* Familiarisez-vous avec [l’architecture de microservices](https://aka.ms/MicroservicesArchitecture) immédiatement

## <a name="introduction"></a>Introduction

Les entreprises cherchent de plus en plus à réaliser des économies, à résoudre les problèmes de déploiement et à améliorer les opérations DevOps et de production en utilisant des conteneurs. Microsoft a fait preuve d’innovation dans le domaine des conteneurs pour Windows et Linux en créant des produits comme Azure Kubernetes Service et Azure Service Fabric et en formant des partenariats avec des acteurs phares du secteur tels que Docker, Mesosphere et Kubernetes. Ces produits offrent aux entreprises des solutions de conteneur qui leur permettent de créer et déployer des applications à la vitesse et à l’échelle du cloud, indépendamment de la plateforme ou des outils qu’elles ont choisi d’utiliser.

Docker est en passe de devenir de facto le standard dans le domaine du conteneur, recueillant l’adhésion des éditeurs les plus en vue dans les écosystèmes Windows et Linux. (Microsoft est l’un des principaux fournisseurs de cloud à se ranger du côté de Docker.) Dans l’avenir, Docker sera probablement omniprésent dans les centres de données cloud ou locaux.

Par ailleurs, l’architecture de [microservices](https://martinfowler.com/articles/microservices.html) est une approche qui devient importante pour les applications stratégiques distribuées. Dans une architecture basée sur les microservices, l’application repose sur un ensemble de services qui peuvent être développés, testés, déployés et versionnés de manière indépendante.

## <a name="about-this-guide"></a>À propos de ce guide

Ce guide est une introduction au développement d’applications basées sur les microservices et à la gestion de celles-ci au moyen de conteneurs. Il traite de la conception architecturale et des approches d’implémentation utilisant .NET Core et les conteneurs Docker. Pour faciliter la prise en main des conteneurs et des microservices, ce guide met en lumière une application de référence en conteneur basée sur des microservices que vous pouvez explorer. L’exemple d’application est disponible sur le dépôt GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).

Ce guide livre des conseils de base en matière de développement et d’architecture au niveau de l’environnement de développement avec deux technologies mises en avant : Docker et .NET Core. Notre objectif est que vous lisiez ce guide en pensant à la conception de votre application sans vous polariser sur l’infrastructure (cloud ou locale) de votre environnement de production. Vous prendrez vos décisions concernant l’infrastructure plus tard, au moment de créer vos applications pour la production. Par conséquent, ce guide se veut neutre concernant l’infrastructure et davantage centré sur l’environnement de développement.

Après avoir examiné ce guide, votre prochaine étape consistera à vous familiariser avec les microservices prêts pour la production dans Microsoft Azure.

## <a name="version"></a>Version

Ce guide a été modifié afin de couvrir la version **.NET Core 2.2** ainsi que les nombreuses mises à jour supplémentaires liées à la même « vague » technologique (c’est-à-dire Azure et autres technologies tierces) qui coïncident d’un point de vue chronologique avec .NET Core 2.2. C’est pourquoi la version du livre a également été mise à jour avec la version **2.2**. 

## <a name="what-this-guide-does-not-cover"></a>Sujets non abordés dans ce guide

Ce guide ne traite pas du cycle de vie des applications, de DevOps, des pipelines CI/CD, ni du travail d’équipe. Le guide complémentaire intitulé [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) (Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft) porte essentiellement sur ce sujet. Le présent guide ne fournit pas non plus de détails sur l’implémentation de l’infrastructure Azure, notamment sur les orchestrateurs spécifiques.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (livre électronique téléchargeable)  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a>Public visé par ce guide

Nous avons rédigé ce guide à l’intention des développeurs et des architectes de solutions qui n’ont pas d’expérience en matière développement d’applications Docker et d’architecture basée sur les microservices. Ce guide s’adresse à vous si votre intention est d’apprendre à architecturer, concevoir et implémenter des applications de type preuve de concept avec les technologies de développement Microsoft (plus particulièrement .NET Core) et des conteneurs Docker.

Ce guide saura aussi vous intéresser si vous êtes un décideur technique, tel qu’un architecte d’entreprise, désireux d’avoir une vue d’ensemble de l’architecture et des technologies avant d’opter pour telle ou telle approche d’application distribuée nouvelle et moderne.

### <a name="how-to-use-this-guide"></a>Comment utiliser ce guide

La première partie de ce guide offre une présentation des conteneurs Docker, explique comment choisir entre .NET Core et le .NET Framework comme framework de développement et propose une vue d’ensemble des microservices. Ce contenu s’adresse aux architectes et aux décideurs techniques qui souhaitent obtenir une vue d’ensemble, mais qui n’ont pas besoin de s’attarder sur les détails d’implémentation de code.

La deuxième partie du guide commence par la section [Processus de développement des applications basées sur Docker](./docker-application-development-process/index.md). Elle porte essentiellement sur les modèles de développement et de microservices pour l’implémentation d’applications utilisant .NET Core et Docker. Cette section intéressera plus particulièrement les développeurs et les architectes qui souhaitent se concentrer sur le code et les détails concernant les modèles et l’implémentation.

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a>Application de référence basée sur des conteneurs et des microservices : eShopOnContainers

L’application eShopOnContainers est une application de référence open source pour .NET Core et les microservices qui a été conçue pour être déployée en utilisant des conteneurs Docker. L’application est constituée de divers sous-systèmes, notamment de plusieurs frontends d’interface utilisateur d’e-store (une application MVC web, une application SPA web et une application mobile native). Elle inclut aussi les microservices et les conteneurs backend pour toutes les opérations côté serveur nécessaires. 

L’objectif de l’application est de présenter des modèles architecturaux. **IL NE S’AGIT PAS D’UN MODÈLE PRÊT POUR LA PRODUCTION** permettant de démarrer des applications réelles. En fait, l’application est dans un état bêta permanent, car elle est également utilisée pour tester les nouvelles technologies potentiellement intéressantes.

## <a name="send-us-your-feedback"></a>Envoyez-nous vos commentaires !

Nous avons rédigé ce guide pour vous aider à comprendre l’architecture des applications en conteneur et des microservices dans .NET. Le guide et l’application de référence associée étant voués à évoluer, nous faisons bon accueil à vos commentaires ! Si vous avez des commentaires à formuler sur la façon dont ce guide peut être amélioré, communiquez-les nous à l’adresse :

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

## <a name="credits"></a>Crédits

Coauteurs :

> **Cesar de la Torre**, chef de produit, équipe produit .NET, Microsoft Corp.
>
> **Bill Wagner**, développeur de contenu en chef, C+E, Microsoft Corp.
>
> **Mike Rousos**, ingénieur logiciel principal, équipe DevDiv CAT, Microsoft

Rédacteurs :

> **Mike Pope**
>
> **Steve Hoag**

Participants et réviseurs :

> **Jeffrey Richter**, ingénieur logiciel partenaire, équipe Azure, Microsoft
>
> **Jimmy Bogard**, architecte en chef chez Headspring
>
> **Udi Dahan**, fondateur et PDG, Particular Software
>
> **Jimmy Nilsson**, co-fondateur et PDG de Factor10
>
> **Glenn Condron**, gestionnaire de programmes en chef, équipe ASP.NET
>
> **Mark Fussell**, responsable principal de la gestion de projets, équipe Azure Service Fabric, Microsoft
>
> **Diego Vega**, responsable de la gestion de projets, équipe Entity Framework, Microsoft
>
> **Barry Dorrans**, gestionnaire de programmes de sécurité en chef
>
> **Rowan Miller**, gestionnaire de programmes en chef, Microsoft
>
> **Ankit Asthana**, responsable principal de la gestion de projets, équipe .NET, Microsoft
>
> **Scott Hunter**, chef de projet directeur partenaire, équipe .NET, Microsoft
>
> **Nish Anil**, responsable de programme senior, équipe .NET, Microsoft
>
> **Dylan Reisenberger**, architecte et responsable de développement chez Polly
>
> **Steve Smith**, artisan logiciel et formateur chez ASPSmith Ltd.
>
> **Ian Cooper**, architecte développement chez Brighter
>
> **Unai Zorrilla**, architecte et responsable de développement chez Plain Concepts
>
> **Eduard Tomas**, responsable de développement chez Plain Concepts
>
> **Ramon Tomas**, développeur chez Plain Concepts
>
> **David Sanz**, développeur chez Plain Concepts
>
> **Javier Valero**, chef des opérations chez Grupo Solutio
>
> **Pierre Millet**, consultant en chef, Microsoft
>
> **Michael Friis**, chef de produit, Docker Inc.
>
> **Charles Lowell**, ingénieur logiciel, équipe VS CAT, Microsoft
>
> **Miguel Veloso**, consultant en chef, Turing Challenge

## <a name="copyright"></a>Copyright

TÉLÉCHARGEMENT disponible à l’adresse suivante : <https://aka.ms/microservicesebook>

PUBLIÉ PAR

Division Développeurs Microsoft, équipes produit .NET et Visual Studio

Division de Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2018 Microsoft Corporation

Tous droits réservés. Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.

Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur. Les points de vue, les opinions et les informations exprimés dans ce document, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.

Certains exemples décrits dans ce document ne sont fournis qu’à titre d’illustration et sont purement fictifs. Toute ressemblance ou tout lien avec le monde réel sont purement fortuits et involontaires.

Microsoft et les marques commerciales mentionnées dans la page web « Marques » à l’adresse <https://www.microsoft.com> sont des marques du groupe de sociétés Microsoft.

Mac et macOS sont des marques commerciales d’Apple Inc.

Le logo de Docker représentant une baleine est une marque déposée de Docker, Inc. Utilisé sous autorisation.

Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.

>[!div class="step-by-step"]
>[Next](container-docker-introduction/index.md)
