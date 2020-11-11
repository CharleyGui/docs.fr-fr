---
title: Microservices .NET. Architecture pour les applications .NET en conteneur
description: Architecture des microservices .NET pour les applications .NET en conteneur | Les microservices sont des services modulables qui peuvent se déployer indépendamment. Les conteneurs Docker (pour Linux et Windows) simplifient le déploiement et les tests en regroupant un service et ses dépendances dans une seule unité, laquelle est ensuite exécutée dans un environnement isolé.
ms.date: 11/10/2020
ms.openlocfilehash: 2055dacd46f90ba3714edb1437bcacad4c175e65
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507265"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a>Microservices .NET : Architecture pour les applications .NET en conteneur

![Couverture de livre](./media/cover-small.png)

**Edition v 3.1** -mise à jour vers ASP.net Core 3,1

Reportez-vous à [Journal des modifications](https://aka.ms/MicroservicesEbookChangelog) pour les mises à jour de livres et les contributions de la communauté.

Ce guide est une introduction au développement d’applications basées sur les microservices et à la gestion de celles-ci au moyen de conteneurs. Il traite de la conception architecturale et des approches d’implémentation utilisant .NET Core et les conteneurs Docker.

Pour faciliter la prise en main, ce guide met en lumière une application de référence en conteneur basée sur des microservices que vous pouvez explorer. L’application de référence est disponible sur le dépôt GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).

## <a name="action-links"></a>Liens d'action

- Ce livre électronique est également disponible au [Téléchargement](https://aka.ms/microservicesebook) au format PDF (version anglaise uniquement).

- Clonez/dupliquez (fork) l’application de référence [eShopOnContainers sur GitHub](https://github.com/dotnet-architecture/eShopOnContainers)

- Regardez la [vidéo d’introduction sur Channel 9](https://aka.ms/microservices-video)

- Familiarisez-vous avec [l’architecture de microservices](https://aka.ms/MicroservicesArchitecture) immédiatement

## <a name="introduction"></a>Introduction

Les entreprises cherchent de plus en plus à réaliser des économies, à résoudre les problèmes de déploiement et à améliorer les opérations DevOps et de production en utilisant des conteneurs. Microsoft a fait preuve d’innovation dans le domaine des conteneurs pour Windows et Linux en créant des produits comme Azure Kubernetes Service et Azure Service Fabric et en formant des partenariats avec des acteurs phares du secteur tels que Docker, Mesosphere et Kubernetes. Ces produits offrent aux entreprises des solutions de conteneur qui leur permettent de créer et déployer des applications à la vitesse et à l’échelle du cloud, indépendamment de la plateforme ou des outils qu’elles ont choisi d’utiliser.

Docker est en passe de devenir de facto le standard dans le domaine du conteneur, recueillant l’adhésion des éditeurs les plus en vue dans les écosystèmes Windows et Linux. (Microsoft est l’un des principaux fournisseurs de Cloud qui prennent en charge l’arrimeur.) À l’avenir, l’arrimeur sera probablement omniprésent dans n’importe quel centre de l’environnement Cloud ou local.

Par ailleurs, l’architecture de [microservices](https://martinfowler.com/articles/microservices.html) est une approche qui devient importante pour les applications stratégiques distribuées. Dans une architecture basée sur les microservices, l’application repose sur un ensemble de services qui peuvent être développés, testés, déployés et versionnés de manière indépendante.

## <a name="about-this-guide"></a>À propos de ce guide

Ce guide est une introduction au développement d’applications basées sur les microservices et à la gestion de celles-ci au moyen de conteneurs. Il traite de la conception architecturale et des approches d’implémentation utilisant .NET Core et les conteneurs Docker. Pour faciliter la prise en main des conteneurs et des microservices, ce guide met en lumière une application de référence en conteneur basée sur des microservices que vous pouvez explorer. L’exemple d’application est disponible sur le dépôt GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).

Ce guide livre des conseils de base en matière de développement et d’architecture au niveau de l’environnement de développement avec deux technologies mises en avant : Docker et .NET Core. Notre objectif est que vous lisiez ce guide en pensant à la conception de votre application sans vous polariser sur l’infrastructure (cloud ou locale) de votre environnement de production. Vous prendrez vos décisions concernant l’infrastructure plus tard, au moment de créer vos applications pour la production. Par conséquent, ce guide se veut neutre concernant l’infrastructure et davantage centré sur l’environnement de développement.

Après avoir examiné ce guide, votre prochaine étape consistera à vous familiariser avec les microservices prêts pour la production dans Microsoft Azure.

## <a name="version"></a>Version

Ce guide a été révisé pour couvrir la version **3,1 de .net Core** , ainsi que de nombreuses mises à jour supplémentaires liées aux mêmes « vagues » de technologies (c’est-à-dire, Azure et des technologies tierces) qui coïncident avec la version 3,1 de .net core. C’est la raison pour laquelle la version du livre a également été mise à jour vers la version **3,1**.

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

La deuxième partie du guide commence par la section [Processus de développement des applications basées sur Docker](./docker-application-development-process/index.md). Il se concentre sur les modèles de développement et de microservice pour implémenter des applications à l’aide de .NET Core et de Dockr. Cette section intéressera plus particulièrement les développeurs et les architectes qui souhaitent se concentrer sur le code et les détails concernant les modèles et l’implémentation.

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a>Application de référence basée sur des conteneurs et des microservices : eShopOnContainers

L’application eShopOnContainers est une application de référence open source pour .NET Core et les microservices qui a été conçue pour être déployée en utilisant des conteneurs Docker. L’application se compose de plusieurs sous-systèmes, y compris plusieurs serveurs frontaux d’interface utilisateur du magasin e-Store (une application Web MVC, un SPA Web et une application mobile native). Elle inclut aussi les microservices et les conteneurs backend pour toutes les opérations côté serveur nécessaires.

L’objectif de l’application est de présenter des modèles architecturaux. **IL NE S’AGIT PAS D’UN MODÈLE PRÊT POUR LA PRODUCTION** permettant de démarrer des applications réelles. En fait, l’application est dans un État bêta permanent, car elle est également utilisée pour tester de nouvelles technologies potentiellement intéressantes lorsqu’elles s’affichent.

## <a name="send-us-your-feedback"></a>Envoyez-nous vos commentaires !

Nous avons rédigé ce guide pour vous aider à comprendre l’architecture des applications en conteneur et des microservices dans .NET. Le guide et l’application de référence associée étant voués à évoluer, nous faisons bon accueil à vos commentaires ! Si vous avez des commentaires sur la façon dont ce guide peut être amélioré, envoyez vos commentaires à l’adresse <https://aka.ms/ebookfeedback> .

## <a name="credits"></a>Crédits

Coauteurs :

> **Cesar de la Torre** , chef de produit, équipe produit .NET, Microsoft Corp.
>
> **Bill Wagner** , développeur de contenu en chef, C+E, Microsoft Corp.
>
> **Mike Rousos** , ingénieur logiciel principal, équipe DevDiv CAT, Microsoft

Rédacteurs :

> **Mike Pope**
>
> **Steve Hoag**

Participants et réviseurs :

> **Jeffrey Richter** , ingénieur logiciel partenaire, équipe Azure, Microsoft
>
> **Jimmy Bogard** , architecte en chef chez Headspring
>
> **Udi Dahan** , fondateur et PDG, Particular Software
>
> **Jimmy Nilsson** , co-fondateur et PDG de Factor10
>
> **Glenn Condron** , gestionnaire de programmes en chef, équipe ASP.NET
>
> **Mark Fussell** , responsable principal de la gestion de projets, équipe Azure Service Fabric, Microsoft
>
> **Diego Vega** , responsable de la gestion de projets, équipe Entity Framework, Microsoft
>
> **Barry Dorrans** , gestionnaire de programmes de sécurité en chef
>
> **Rowan Miller** , gestionnaire de programmes en chef, Microsoft
>
> **Ankit Asthana** , responsable principal de la gestion de projets, équipe .NET, Microsoft
>
> **Scott Hunter** , chef de projet directeur partenaire, équipe .NET, Microsoft
>
> **Nish Anil** , responsable de programme senior, équipe .NET, Microsoft
>
> **Dylan Reisenberger** , architecte et responsable de développement chez Polly
>
> **Steve « ardalis » Smith** - Architecte et formateur logiciel - [Ardalis.com](https://ardalis.com)
>
> **Ian Cooper** , architecte développement chez Brighter
>
> **Unai Zorrilla** , architecte et responsable de développement chez Plain Concepts
>
> **Eduard Tomas** , responsable de développement chez Plain Concepts
>
> **Ramon Tomas** , développeur chez Plain Concepts
>
> **David Sanz** , développeur chez Plain Concepts
>
> **Javier Valero** , chef des opérations chez Grupo Solutio
>
> **Pierre Millet** , consultant en chef, Microsoft
>
> **Michael Friis** , chef de produit, Docker Inc.
>
> **Charles Lowell** , ingénieur logiciel, équipe VS CAT, Microsoft
>
> **Miguel Veloso** , ingénieur de développement logiciel chez des concepts simples
>
> **Sumit Ghosh** , consultant principal chez Neudesic

## <a name="copyright"></a>copyright

PUBLIÉ PAR

Division Développeurs Microsoft, équipes produit .NET et Visual Studio

Division de Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2020 par Microsoft Corporation

Tous droits réservés. Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.

Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur. Les points de vue, les opinions et les informations exprimés dans ce document, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.

 Certains exemples sont fournis à titre indicatif uniquement et sont fictifs. Toute association ou lien est purement involontaire ou fortuit.

Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur <https://www.microsoft.com> sont des marques du groupe Microsoft.

Mac et macOS sont des marques commerciales d’Apple Inc.

Le logo de la baleine de l’arrimeur est une marque déposée de Dockr, Inc. utilisée par l’autorisation.

Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.

>[!div class="step-by-step"]
>[Next](container-docker-introduction/index.md)
