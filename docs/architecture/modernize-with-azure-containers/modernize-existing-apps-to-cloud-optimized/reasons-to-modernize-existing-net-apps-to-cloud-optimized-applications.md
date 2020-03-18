---
title: Raisons de moderniser les applications .NET existantes aux applications Cloud-Optimized
description: Moderniser les applications .NET existantes avec les conteneurs Azure Cloud et Windows (fr) Raisons de moderniser les applications .NET existantes aux applications Cloud-Optimized
ms.date: 04/28/2018
ms.openlocfilehash: 55eb3fb9b0b6c91e25bcdb23056a8a8e51463ef7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73093632"
---
# <a name="reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications"></a>Raisons de moderniser les applications .NET existantes aux applications Cloud-Optimized

Grâce à une application Cloud-Optimized, vous pouvez fournir rapidement et à plusieurs reprises des applications fiables à vos clients. Vous gagnez une agilité et une fiabilité essentielles en reportant une grande partie de la complexité opérationnelle de votre application à la plate-forme.

Si vous ne pouvez pas commercialiser vos applications rapidement, au moment où vous expédiez votre application, le marché que vous ciblagez aura évolué. Vous pourriez être trop tard, peu importe comment l’application a été conçu ou conçu. Vous pourriez échouer ou ne pas atteindre votre plein potentiel parce que vous ne pouvez pas synchroniser la livraison d’applications avec les besoins du marché.

Le besoin d’innovation continue dans les affaires pousse les équipes de développement et d’exploitation à la limite. La seule façon d’atteindre l’agilité dont vous avez besoin dans l’innovation commerciale continue est de moderniser vos applications avec des technologies comme les conteneurs et des principes d’application spécifiques Cloud-Optimized.

L’essentiel est que lorsqu’une organisation construit et gère des applications optimisées en nuage, elle peut mettre des solutions entre les mains des clients plus tôt et mettre de nouvelles idées sur le marché lorsqu’elles sont pertinentes.

## <a name="cloud-optimized-application-principles-and-tenets"></a>Principes et principes d’application optimisés pour le cloud

Les améliorations dans le cloud sont principalement axées sur l’atteinte de deux objectifs : réduire les coûts et améliorer la croissance de l’entreprise en améliorant l’agilité. Ces objectifs sont atteints en simplifiant les processus et en réduisant les frictions lorsque vous relâchez et expédiez des applications.

Votre application est optimisée pour le Cloud si vous pouvez développer votre application de manière agile de manière autonome à partir d’autres applications sur site, puis libérer, déployer, à l’échelle automatique, surveiller et dépanner votre application dans le cloud.

La clé est *l’agilité*. Vous ne pouvez pas expédier avec agilité à moins de réduire au minimum les problèmes de déploiement à la production et les problèmes d’environnement de dev/test. Les conteneurs (en particulier, Docker, en tant que norme de facto) et les services gérés ont été conçus spécifiquement à cette fin.

Pour atteindre l’agilité, vous avez également besoin de processus DevOps automatisés basés sur les pipelines CI/CD qui se libèrent sur des plates-formes évolutives dans le cloud. Les plates-formes CI/CD (comme Azure DevOps Services ou Jenkins) qui se déploient sur une plate-forme cloud évolutive et résiliente (comme Azure App Service ou Azure Kubernetes Service) sont des technologies clés pour atteindre l’agilité dans le cloud.

La liste suivante décrit les principes ou les pratiques principaux pour les applications Cloud-Optimized. Notez que vous pouvez adopter tout ou seulement certains de ces principes, dans une approche progressive ou progressive :

- **Conteneurs**. Les conteneurs vous donnent la possibilité d’inclure les dépendances d’application avec l’application elle-même. La conteneurisation réduit considérablement le nombre de problèmes que vous pourriez rencontrer lorsque vous vous déployez dans des environnements de production ou que vous testez dans des environnements de mise en scène. En fin de compte, les conteneurs améliorent l’agilité de la livraison des applications.

- **Nuage résilient et évolutif**. Le cloud fournit une plate-forme qui est gérée, élastique, évolutive et résiliente. Ces caractéristiques sont fondamentales pour obtenir des améliorations des coûts et expédier des applications hautement disponibles et fiables dans une livraison continue. Les services gérés comme les bases de données gérées, le cache géré comme service (CaaS) et le stockage géré sont des éléments fondamentaux pour alléger les coûts de maintenance de votre application.

- **Surveillance**. Vous ne pouvez pas avoir une application fiable sans avoir un bon moyen de détecter et de diagnostiquer les exceptions et les problèmes de performances d’application. Vous devez obtenir des informations exploitables grâce à la gestion des performances d’applications et à l’analyse instantanée.

- **Culture DevOps et livraison continue**. Adopter les pratiques de DevOps nécessite un changement culturel dans lequel les équipes ne travaillent plus en silos indépendants. Les pipelines CI/CD ne sont possibles que lorsqu’il y a une collaboration accrue entre les équipes de développement et d’opérations informatiques, appuyées par des conteneurs et des outils CI/CD.

La figure 4-2 montre les principaux piliers optionnels d’une application Cloud-Optimized. Plus vous implémentez de piliers, plus votre application sera réadsible pour répondre aux attentes de vos clients.

![Diagramme nommant les piliers principaux d’une application Cloud-Optimized.](./media/main-pillars-cloud-optimized-application.png)

**Figure 4-2.** Principaux piliers d’une application Cloud-Optimized

Pour résumer, une application Cloud-Optimized est une approche de construction et de gestion d’applications qui tire parti du modèle d’informatique en nuage, tout en utilisant une combinaison de conteneurs, d’infrastructures cloud gérées, de techniques d’application résilientes, surveillance, livraison continue et DevOps, le tout sans avoir besoin de réécouvrer et de recoder vos applications existantes.

Votre organisation peut adopter progressivement ces technologies et approches. Vous n’avez pas à les embrasser tous, tout à la fois. Vous pouvez les adopter progressivement, en fonction des priorités de l’entreprise et des besoins des utilisateurs.

## <a name="benefits-of-a-cloud-optimized-application"></a>Avantages d’une application Cloud-Optimized

Vous pouvez obtenir les avantages suivants en convertissant une application existante en une application optimisée en nuage (sans rétropuces ni codage) :

- **Réduction des coûts, car l’infrastructure gérée est gérée par le fournisseur de cloud**. Les applications optimisées pour le cloud bénéficient des avantages du cloud en utilisant l’élasticité, l’autonomie et la grande disponibilité du cloud. Les avantages sont liés non seulement aux fonctionnalités de calcul (VMs et conteneurs), mais dépendent également des ressources dans le cloud, comme DBaaS, CaaS, et toute infrastructure dont une application pourrait avoir besoin.

- **Application et infrastructure résilientes**. Lorsque vous migrez vers le nuage, vous devez embrasser les échecs transitoires; défaillances se produiront dans le nuage. En outre, l’infrastructure et le matériel cloud sont « remplaçables », ce qui augmente les possibilités d’indisponibilité transitoire. Dans le même temps, les capacités de cloud intérieur et certaines techniques de développement d’applications qui mettent en œuvre la résilience et automatisent la récupération facilitent la récupération des défaillances imprévues du cloud.

- **Des aperçus plus approfondis des performances de l’application**. Les outils de surveillance cloud comme Azure Application Insights permettent de visualiser la gestion de la santé, l’enregistrement et les notifications. Les journaux d’audit facilitent le débogé et l’audit des applications, fondamentales pour une application cloud fiable.

- **Portabilité d’application, avec des déploiements agiles.** Les conteneurs (conteneurs Linux ou Windows basés sur Docker Engine) offrent la meilleure solution pour éviter une application verrouillée par le cloud. En utilisant des conteneurs, des hôtes Docker et des orchestrateurs multi-nuages, vous pouvez facilement passer d’un environnement ou d’un nuage à un autre. Les conteneurs éliminent le frottement qui se produit généralement dans les déploiements dans n’importe quel environnement (stade/test/production).

Tous ces avantages offrent en fin de compte des réductions de coûts clés pour votre cycle de vie de la demande de bout en bout.

Dans les sections suivantes, ces avantages sont expliqués plus en détail et sont liés à des technologies spécifiques.

>[!div class="step-by-step"]
>[Suivant précédent](index.md)
>[Next](microsoft-technologies-in-cloud-optimized-applications.md)
