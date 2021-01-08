---
title: Raisons de moderniser des applications .NET existantes pour Cloud-Optimized applications
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Raisons de moderniser des applications .NET existantes pour Cloud-Optimized applications
ms.date: 12/21/2020
ms.openlocfilehash: e9b3ad151cf0591783ada8a1ab87cb0f14423a7e
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025210"
---
# <a name="reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications"></a>Raisons de moderniser des applications .NET existantes pour Cloud-Optimized applications

Avec une application Cloud-Optimized, vous pouvez fournir rapidement et à plusieurs reprises des applications fiables à vos clients. Vous bénéficiez d’une agilité et d’une fiabilité essentielles en reportant une grande partie de la complexité opérationnelle de votre application sur la plateforme.

Si vous ne parvenez pas à mettre vos applications sur le marché rapidement, au moment où vous livrez votre application, le marché ciblé aura évolué. Vous êtes peut-être trop tard, quelle que soit la façon dont l’application a été conçue ou conçue. Vous pouvez échouer ou ne pas atteindre votre potentiel complet, car vous ne pouvez pas synchroniser la livraison des applications avec les besoins du marché.

Le besoin d’une innovation continue pour l’innovation continue pousse les équipes de développement et d’exploitation jusqu’à la limite. La seule façon d’obtenir la souplesse dont vous avez besoin pour l’innovation continue consiste à moderniser vos applications avec des technologies telles que des conteneurs et des principes d’application Cloud-Optimized spécifiques.

La ligne inférieure est que lorsqu’une organisation crée et gère des applications optimisées pour le Cloud, elle peut mettre des solutions dans les mains des clients plus tôt et apporter de nouvelles idées sur le marché lorsqu’elles sont pertinentes.

## <a name="cloud-optimized-application-principles-and-tenets"></a>Principes et principes de l’application Cloud-Optimized

Les améliorations du Cloud sont principalement axées sur la réalisation de deux objectifs : réduire les coûts et améliorer la croissance de l’entreprise en améliorant l’agilité. Ces objectifs sont atteints en simplifiant les processus et en réduisant les frottements lorsque vous publiez et expédiez des applications.

Votre application est Cloud-Optimized si vous pouvez, de manière agile, développer votre application de façon autonome à partir d’autres applications locales, puis libérer, déployer, mettre à l’échelle, surveiller et dépanner votre application dans le Cloud.

La clé est l' *agilité*. Vous ne pouvez pas fournir une agilité, sauf si vous réduisez au minimum les problèmes de déploiement en production et d’environnement de développement/test. Les conteneurs (plus précisément, l’arrimeur, en tant que standard de facto) et les services managés ont été spécifiquement conçus à cet effet.

Pour obtenir de l’agilité, vous avez également besoin de processus DevOps automatisés basés sur des pipelines CI/CD qui se libèrent sur des plateformes évolutives dans le Cloud. Les plateformes CI/CD (comme Azure DevOps Services ou Jenkins) qui sont déployées sur une plateforme Cloud évolutive et résiliente (comme Azure App Service ou le service Kubernetes Azure) sont des technologies clés pour atteindre l’agilité dans le Cloud.

La liste suivante décrit les principales principes ou pratiques pour les applications Cloud-Optimized. Notez que vous pouvez adopter tout ou partie de ces principes en adoptant une approche progressive ou incrémentielle :

- **Conteneurs**. Les conteneurs vous permettent d’inclure des dépendances d’application avec l’application elle-même. La création de conteneurs réduit considérablement le nombre de problèmes que vous pouvez rencontrer quand vous déployez dans des environnements de production ou que vous testez dans des environnements intermédiaires. Enfin, les conteneurs améliorent l’agilité de la livraison des applications.

- **Cloud résilient et évolutif**. Le Cloud fournit une plateforme gérée, élastique, évolutive et résiliente. Ces caractéristiques sont fondamentales pour améliorer les coûts et livrer des applications hautement disponibles et fiables dans une livraison continue. Les services gérés comme les bases de données gérées, le cache géré en tant que service (CaaS) et le stockage géré sont des éléments fondamentaux pour réduire les coûts de maintenance de votre application.

- **Surveillance**. Vous ne pouvez pas avoir une application fiable sans disposer d’un bon moyen pour détecter et diagnostiquer les exceptions et les problèmes de performances des applications. Vous devez recevoir des Insights actionnables grâce à la gestion des performances des applications et à l’analytique instantanée.

- **Culture DevOps et livraison continue**. L’adoption des pratiques de DevOps nécessite une modification culturelle dans laquelle les équipes ne travaillent plus dans des silos indépendants. Les pipelines CI/CD ne sont possibles que lorsqu’il existe une collaboration accrue entre les équipes de développement et d’exploitation informatique, prises en charge par les conteneurs et les outils CI/CD.

La figure 4-2 montre les principaux piliers facultatifs d’une application Cloud-Optimized. Plus vous implémentez de piliers, plus votre application sera prête à répondre aux attentes de vos clients.

![Diagramme nommant les piliers principaux d’une application Cloud-Optimized.](./media/main-pillars-cloud-optimized-application.png)

**Figure 4-2.** Principaux piliers d’une application Cloud-Optimized

Pour résumer, une application Cloud-Optimized est une approche de la création et de la gestion d’applications qui tirent parti du modèle cloud computing, tout en utilisant une combinaison de conteneurs, d’une infrastructure cloud gérée, de techniques d’application résilientes, de surveillance, de livraison continue et de DevOps, sans avoir à remanier et à reconstituer vos applications existantes.

Votre organisation peut adopter ces technologies et approches de manière progressive. Vous n’avez pas à les utiliser tous en même temps. Vous pouvez les adopter de manière incrémentielle, en fonction des priorités de l’entreprise et des besoins de l’utilisateur.

## <a name="benefits-of-a-cloud-optimized-application"></a>Avantages d’une application Cloud-Optimized

Vous pouvez bénéficier des avantages suivants en convertissant une application existante en application Cloud-Optimized (sans remaniement ni codage) :

- **Réduction des coûts, car l’infrastructure gérée est gérée par le fournisseur de Cloud**. Cloud-Optimized applications bénéficient des avantages du Cloud en utilisant l’élasticité prête à l’emploi du Cloud, la mise à l’échelle automatique et la haute disponibilité. Les avantages sont liés non seulement aux fonctionnalités de calcul (machines virtuelles et conteneurs), mais également aux ressources dans le Cloud, telles que DBaaS, CaaS et toute infrastructure dont une application peut avoir besoin.

- **Application et infrastructure résilientes**. Lorsque vous migrez vers le Cloud, vous devez adopter des échecs temporaires. des erreurs se produisent dans le Cloud. En outre, l’infrastructure et le matériel de Cloud sont « remplaçables », ce qui augmente les opportunités de temps mort transitoire. En même temps, les fonctionnalités de cloud interne et certaines techniques de développement d’applications qui implémentent la résilience et automatisent la récupération facilitent grandement la récupération suite à des défaillances inattendues dans le Cloud.

- Informations plus **approfondies sur les performances des applications**. Les outils de surveillance du Cloud comme Azure Application Insights fournissent une visualisation pour la gestion de l’intégrité, la journalisation et les notifications. Les journaux d’audit rendent les applications faciles à déboguer et à auditer, fondamentales pour une application Cloud fiable.

- La **portabilité des applications, avec des déploiements agile**. Les conteneurs (conteneurs Linux ou Windows basés sur le moteur de l’arrimeur) offrent la meilleure solution pour éviter une application verrouillée dans le Cloud. En utilisant des conteneurs, des hôtes de station d’accueil et des orchestrateurs multiclouds, vous pouvez facilement vous déplacer d’un environnement ou d’un Cloud vers un autre. Les conteneurs éliminent le frottement qui se produit généralement dans les déploiements dans n’importe quel environnement (phase, test/production).

En définitive, tous ces avantages offrent des réductions de coût clés pour votre cycle de vie d’application de bout en bout.

Dans les sections suivantes, ces avantages sont expliqués plus en détail et sont liés à des technologies spécifiques.

>[!div class="step-by-step"]
>[Précédent](index.md) 
> [Suivant](microsoft-technologies-in-cloud-optimized-applications.md)
