---
title: 'Applications serverless : Architecture, modèles et implémentation Azure'
description: Guide sur l’architecture serverless. Découvrez quand, pourquoi et comment implémenter une architecture serverless (par opposition à une infrastructure IaaS ou une plateforme PaaS) pour les applications de votre entreprise.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 9dea7dbccb5c9e125f792e6a7287a7dd2fad26f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73093548"
---
# <a name="serverless-apps-architecture-patterns-and-azure-implementation"></a>Applications serverless : Architecture, modèles et implémentation Azure

![Capture d’écran qui montre la couverture du livre électronique Serverless Apps.](./media/index/serverless-apps-cover.jpg)

> TÉLÉCHARGEMENT disponible à l’adresse suivante : <https://aka.ms/serverless-ebook>

PUBLIÉ PAR

Division Développeurs Microsoft, équipes produit .NET et Visual Studio

Division de Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2018 Microsoft Corporation

Tous droits réservés. Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.

Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur. Les points de vue, les opinions et les informations exprimés dans ce document, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.

 Certains exemples sont fournis à titre indicatif uniquement et sont fictifs. Toute association ou lien est purement involontaire ou fortuit.

Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur <https://www.microsoft.com> sont des marques du groupe Microsoft.

Mac et macOS sont des marques commerciales d’Apple Inc.

Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.

Auteur :

> **[Jeremy Likness](https://twitter.com/jeremylikness)**, Senior Cloud Advocate, Microsoft Corp.

Collaborateur :

> **[Cecil Phillip](https://twitter.com/cecilphillip)**, Senior Cloud Advocate, Microsoft Corp.

Rédacteurs :

> **[Bill Wagner](https://twitter.com/billwagner)**, Développeur de contenu senior, Microsoft Corp.

> **[Maira Wenzel](https://twitter.com/mairacw)**, Développeur de contenu senior, Microsoft Corp.

Participants et réviseurs :

> **[Steve Smith](https://twitter.com/ardalis)**, propriétaire, Ardalis Services.

## <a name="introduction"></a>Introduction

[Serverless](https://azure.microsoft.com/solutions/serverless/) est l’évolution des plates-formes cloud dans la direction du code natif du cloud pur. Il rapproche les développeurs d’une logique métier en les éloignant des problèmes d’infrastructure. Il ne s’agit pas d’un modèle qui n’implique « aucun serveur », mais plutôt d’un modèle qui implique « moins de serveurs ». Le code serverless est basé sur les événements. Le code peut être déclenché par n’importe quoi, une requête web HTTP traditionnelle, un minuteur ou le résultat du chargement d’un fichier. L’infrastructure derrière le modèle serverless permet une mise à l’échelle instantanée pour répondre à des besoins élastiques et offre une micro-facturation pour un vrai « paiement à l’utilisation. » Le modèle serverless demande de penser et d’approcher autrement la création d’applications et n’est pas la solution à tous les problèmes. En tant que développeur, vous devez déterminer :

- Quels sont les avantages et les inconvénients du modèle serverless ?
- Pourquoi devriez-vous envisager le modèle serverless pour vos propres applications ?
- Comment générer, tester, déployer et gérer votre code serverless ?
- Où est-il judicieux de migrer du code vers un modèle serverless dans les applications existantes, et quel est le meilleur moyen d’accomplir cette transformation ?

## <a name="about-this-guide"></a>À propos de ce guide

Ce guide se concentre sur le développement natif cloud des applications qui utilisent le modèle serverless. Il met en avant les avantages, présente les éventuels inconvénients de développer des applications serverless et fournit une étude des architectures serverless. De nombreux exemples d’utilisation du modèle serverless sont illustrés avec différents modèles de conception serverless.

Ce guide décrit les composants de la plateforme serverless Azure et se concentre en particulier sur l’implémentation du modèle serverless avec [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview). Vous allez non seulement découvrir les déclencheurs et les liaisons, mais aussi comment implémenter des applications serverless qui s’appuient sur l’état à l’aide de fonctions durables. Enfin, des exemples et des études de cas en entreprise vont vous permettre d’avoir du contexte et un cadre de référence pour déterminer si le modèle serverless est la bonne approche pour vos projets.

## <a name="evolution-of-cloud-platforms"></a>Évolution des plateformes cloud

Le modèle serverless est le point culminant de plusieurs itérations de plateformes cloud. L’évolution a commencé par les centres de données physiques pour continuer avec les infrastructures IaaS (Infrastructure as a service) et les plateformes PaaS (Platform as a Service).

![Du local au serverless](./media/serverless-evolution-iaas-paas.png)

Avant le cloud, une délimitation perceptible existait entre le développement et les opérations. Le déploiement d’une application supposait de répondre à une multitude de questions comme :

- Quel matériel doit être installé ?
- Comment l’accès physique à l’ordinateur est sécurisé ?
- Faut-il un onduleur pour le centre de données ?
- Où sont envoyées les sauvegardes de stockage ?
- Un système d’alimentation redondant doit-il être envisagé ?

La liste s’allongeait et la surcharge était énorme. Dans de nombreux cas, les services informatiques étaient obligés de gaspiller considérablement. Les déchets étaient dus à une sur-allocation des serveurs comme machines de sauvegarde pour la récupération en cas de catastrophe et des serveurs de secours pour permettre l’étalement. Heureusement, l’introduction de la technologie de virtualisation (comme [Hyper-V](/virtualization/hyper-v-on-windows/about/)) avec des machines virtuelles (VM) a donné lieu à l’infrastructure en tant que service (IaaS). Avec une infrastructure virtualisée, des opérations permettaient de définir un ensemble standard de serveurs comme épine dorsale, donnant ainsi un environnement flexible capable de provisionner des serveurs uniques « à la demande ». Plus important, la virtualisation préparait le terrain pour utiliser le cloud afin de fournir des machines virtuelles « en tant que service ». Les entreprises pouvaient alors aisément arrêter de se préoccuper du système d’alimentation redondant ou des ordinateurs physiques. Elles se concentraient plutôt sur l’environnement virtuel.

IaaS implique quand même une surcharge conséquente parce que les opérations sont encore responsables de différentes tâches. Il s’agit notamment des tâches suivantes :

- Correction et sauvegarde des serveurs.
- Installation de packages.
- Mise à jour du système d’exploitation.
- Supervision de l’application.

L’évolution d’après a réduit la surcharge avec l’introduction des plateformes PaaS. Avec PaaS, le fournisseur de cloud gère les systèmes d’exploitation, les correctifs de sécurité et même les packages nécessaires à la prise en charge d’une plateforme spécifique. Au lieu de créer une machine virtuelle, de configurer le .NET Framework et de mettre sur pied des serveurs IIS (Internet Information Services), les développeurs choisissent simplement une « cible de plateforme », comme une « application web » ou un « point de terminaison d’API », puis déploient le code directement. Les questions d’infrastructure se réduisent à :

- Quels services de taille sont nécessaires ?
- Comment les services montent en charge (ajout d’autres serveurs ou nœuds) ?
- Comment les services montent en puissance (augmentation de la capacité des serveurs ou des nœuds d’hébergement) ?

Le modèle serverless réduit davantage la place des serveurs en se concentrant sur du code basé sur les événements. Au lieu d’une plateforme, les développeurs peuvent se concentrer sur un microservice qui fait une seule chose. Les deux questions clés pour générer le code serverless se résument à :

- Qu’est-ce qui déclenche le code ?
- Que fait le code ?

Avec le modèle serverless, l’infrastructure est réduite. Dans certains cas, le développeur n’a plus à se préoccuper de l’hôte du tout. Qu’une instance IIS, Kestrel, Apache ou autre serveur web s’exécute ou pas pour gérer les demandes web, le développeur se concentre sur un déclencheur HTTP. Le déclencheur fournit la charge utile multiplateforme standard de la requête. La charge utile non seulement simplifie le processus de développement, mais facilite aussi les tests et rend parfois le code facilement portable sur plusieurs plateformes.

Une autre fonctionnalité du modèle serverless est la micro-facturation. Il est courant que les applications web hébergent les points de terminaison des API web. Dans les implémentations traditionnelles de systèmes nus, IaaS et même PaaS, les ressources pour héberger les API sont tout le temps payantes. Cela signifie que vous payez pour héberger les points de terminaison même quand ils n’enregistrent aucun accès. Vous constaterez souvent qu’une API est plus appelée que les autres, du coup l’intégralité du système est mis à l’échelle en fonction de la prise en charge des points de terminaison populaires. Avec le modèle serverless, vous pouvez mettre à l’échelle chaque point de terminaison indépendamment et payer à l’utilisation pour éviter d’être facturé quand les API ne sont pas appelées. Dans de nombreux cas, la migration peut réduire considérablement les frais de prise en charge des points de terminaison.

## <a name="what-this-guide-doesnt-cover"></a>Ce que ce guide ne couvre pas

Ce guide met avant tout l’accent sur les approches d’architecture et les modèles de conception, mais ne rentre pas dans les détails d’implémentation d’Azure Functions, de [Logic Apps](https://docs.microsoft.com/azure/logic-apps/logic-apps-what-are-logic-apps) ou autres plateformes serverless. Par exemple, il ne couvre ni les flux de travail avancés avec Logic Apps ni les fonctionnalités Azure Functions, telles que la configuration du partage des ressources Cross-Origin (CORS), l’application de domaines personnalisés ou le chargement de certificats SSL. Ces détails sont disponibles en ligne dans la [documentation Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-reference).

### <a name="additional-resources"></a>Ressources supplémentaires

- [Centre d’architecture Azure](https://docs.microsoft.com/azure/architecture/)
- [Meilleures pratiques pour les applications cloud](https://docs.microsoft.com/azure/architecture/best-practices/api-design)

## <a name="who-should-use-the-guide"></a>Public visé par ce guide

Ce guide a été écrit pour les développeurs et les architectes de solutions qui veulent générer des applications d’entreprise avec .NET qui sont susceptibles d’utiliser des composants serverless localement ou dans le cloud. Il est utile pour les développeurs, architectes et décideurs informatiques qui souhaitent :

- Comprendre les avantages et les inconvénients du développement serverless
- Découvrir comment approcher l’architecture serverless
- Exemples d’implémentation d’applications serverless

## <a name="how-to-use-the-guide"></a>Comment utiliser ce guide

La première partie de ce guide examine pourquoi le modèle serverless est une option viable en comparant plusieurs approches d’architecture différentes. Il examine à la fois la technologie et le cycle de vie du développement, car tous les aspects du développement logiciel sont impactés par les décisions d’architecture. Le guide examine ensuite les cas d’usage et les modèles de conception et inclut des implémentations de référence avec Azure Functions. Chaque section contient des ressources supplémentaires pour en savoir plus sur un domaine en particulier. Le guide se conclut par des ressources de procédures pas à pas et une exploration pratique d’une implémentation serverless.

## <a name="send-your-feedback"></a>Envoyez votre feedback

Le guide et les exemples associés sont en constante évolution, donc votre feedback est le bienvenu ! Si vous avez des commentaires sur la façon dont ce guide peut être amélioré, utilisez la section de feedback au bas des pages reposant sur [GitHub issues](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Suivant](architecture-approaches.md)
