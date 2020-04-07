---
title: Applications candidates pour le cloud natif
description: Découvrez quels types d’applications bénéficient d’une approche cloud-native
author: robvet
ms.date: 03/31/2020
ms.openlocfilehash: 8e58f5bd3aa0a4503ea73ab454e42e863eb0bb5d
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805614"
---
# <a name="candidate-apps-for-cloud-native"></a>Applications candidates pour le cloud natif

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Regardez les applications de votre portefeuille. Combien d’entre eux sont admissibles à une architecture cloud-native? Tous ? Peut-être un peu?

En appliquant une analyse coûts/avantages, il y a de fortes chances que la plupart ne supportent pas l’étiquette de prix élevé requise pour être natif du cloud. Le coût d’être natif du cloud dépasserait de loin la valeur commerciale de l’application.

Quel type d’application pourrait être un candidat pour le cloud natif?

- Un grand système d’entreprise stratégique qui doit constamment faire évoluer les capacités/fonctionnalités de l’entreprise

- Une application qui nécessite une vitesse de libération élevée - avec une grande confiance

- Un système avec où les caractéristiques individuelles doivent être libérées *sans* redéploiement complet de l’ensemble du système

- Une application développée par des équipes ayant une expertise dans différentes piles technologiques

- Une application avec des composants qui doivent évoluer indépendamment

Ensuite, il y a les systèmes hérités. Bien que nous aimerions tous construire de nouvelles applications, nous sommes souvent responsables de la modernisation des charges de travail héritées qui sont essentielles à l’entreprise. Au fil du temps, une application héritée pourrait être décomposée en microservices, conteneurisées et finalement « réplatformées » en une architecture cloud-native.

### <a name="modernizing-legacy-apps"></a>Moderniser les applications héritées

L’e-book microsoft gratuit [Modernise les applications .NET existantes avec le cloud Azure et Windows Containers](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) fournit des conseils pour migrer les charges de travail sur site dans le cloud. La figure 1-10 montre qu’il n’existe pas une seule stratégie universelle pour moderniser les applications héritées.

![Stratégies pour la migration des charges de travail héritées](./media/strategies-for-migrating-legacy-workloads.png)

**Figure 1-10**. Stratégies pour la migration des charges de travail héritées

Les applications monolithiques qui ne sont pas critiques bénéficient en grande partie d’une migration rapide de levage et de décalage[(Cloud Infrastructure-Ready).](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md) Ici, la charge de travail sur place est réhossée à un VM basé sur le cloud, sans modifications. Cette approche utilise le [modèle IaaS (Infrastructure as a Service).](https://azure.microsoft.com/overview/what-is-iaas/) Azure comprend plusieurs outils tels [qu’Azure Migrate](https://azure.microsoft.com/services/azure-migrate/), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)et [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) pour faciliter une telle démarche. Bien que cette stratégie puisse permettre de réaliser des économies de coûts, ces applications n’ont généralement pas été conçue pour débloquer et tirer parti des avantages de l’informatique en nuage.

Les applications monolithiques qui sont essentielles à l’entreprise bénéficient souvent d’une migration améliorée de levage et de décalage *(Cloud Optimized).* Cette approche comprend des optimisations de déploiement qui permettent des services cloud clés - sans changer l’architecture de base de l’application. Par exemple, vous pouvez [conteneuriser](https://docs.microsoft.com/virtualization/windowscontainers/about/) l’application et la déployer à un orchestrateur de conteneurs, comme [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/), discuté plus tard dans ce livre. Une fois dans le cloud, l’application peut consommer d’autres services cloud tels que des bases de données, des files d’attente de messages, une surveillance et une mise en cache distribuée.

Enfin, les applications monolithiques qui remplissent des fonctions d’entreprise stratégiques pourraient mieux bénéficier d’une approche *Cloud-Native,* le sujet de ce livre. Cette approche offre agilité et vitesse. Mais, il vient à un coût de replatformation, rétropuces, et la réécriture du code.

Si vous et votre équipe pensez qu’une approche cloud-native est appropriée, il vous incombe de rationaliser la décision avec votre organisation. Quel est exactement le problème d’affaires qu’une approche cloud-native résoudra? Comment s’alignerait-il sur les besoins des entreprises?

- Des versions rapides de fonctionnalités avec une confiance accrue?

- Évolutivité à grain fin - utilisation plus efficace des ressources?

- Amélioration de la résilience du système?

- Amélioration des performances du système?

- Plus de visibilité sur les opérations?

- Mélanger les plates-formes de développement et les magasins de données pour arriver au meilleur outil pour le travail?

- Investissement d’application à l’épreuve de l’avenir?

La bonne stratégie de migration dépend des priorités organisationnelles et des systèmes que vous ciblez. Pour beaucoup, il peut être plus rentable d’optimiser un nuage d’une application monolithique ou d’ajouter des services à grain grossier à une application N-Tier. Dans ces cas, vous pouvez toujours utiliser pleinement les capacités Cloud PaaS comme celles offertes par Azure App Service.

## <a name="summary"></a>Résumé

Dans ce chapitre, nous avons introduit l’informatique en nuage. Nous avons fourni une définition ainsi que les capacités clés qui conduisent une application cloud-native. Nous avons examiné les types de demandes qui pourraient justifier cet investissement et cet effort.

Avec l’introduction derrière, nous plongeons maintenant dans un regard beaucoup plus détaillé sur les natifs du nuage.

### <a name="references"></a>References

- [Fondation Cloud Native Computing](https://www.cncf.io/)

- [.NET Microservices: Architecture for Containerized .NET applications](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Moderniser les applications .NET existantes avec le cloud Azure et les conteneurs Windows](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [Cloud Native Patterns par Cornelia Davis](https://www.manning.com/books/cloud-native-patterns)

- [Au-delà de l’application à douze facteurs](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [Qu’est-ce que l’infrastructure comme Code](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)

- [Le micro-déploiement d’Uber Engineering : déploiement quotidien en toute confiance](https://eng.uber.com/micro-deploy/)

- [Comment Netflix déploie le code](https://www.infoq.com/news/2013/06/netflix/)

- [Contrôle de surcharge pour la mise à l’échelle weChat Microservices](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
>[Suivant précédent](definition.md)
>[Next](introduce-eshoponcontainers-reference-app.md)
