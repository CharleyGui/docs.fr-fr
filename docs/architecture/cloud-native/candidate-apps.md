---
title: Applications candidates pour le Cloud Native
description: Découvrez les types d’applications qui bénéficient d’une approche Cloud Native
author: robvet
ms.date: 05/14/2020
ms.openlocfilehash: 8f00633a575dad12b0bc1d5adb83acac03db0659
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160942"
---
# <a name="candidate-apps-for-cloud-native"></a>Applications candidates pour le Cloud Native

Examinez les applications de votre portefeuille. Combien d’entre elles sont éligibles pour une architecture Cloud Native ? Tous ? Peut-être ?

En appliquant une analyse des coûts/avantages, il y a de bonnes chances que la plupart ne prenne pas en charge la balise Price lourdeur nécessaire pour être Cloud native. Le coût du Cloud Native dépasserait beaucoup la valeur métier de l’application.

Quel type d’application peut être candidat pour le Cloud Native ?

- Système d’entreprise stratégique qui doit faire évoluer constamment les fonctionnalités et fonctionnalités de l’entreprise

- Application nécessitant une rapidité de publication élevée, avec une haute confiance

- Système avec lequel des fonctionnalités individuelles doivent être libérées *sans* redéploiement complet de l’ensemble du système

- Une application développée par les équipes ayant une expertise dans différentes piles technologiques

- Application avec des composants qui doivent être mis à l’échelle indépendamment

Il existe alors des systèmes hérités. Bien que nous aimerions tout pour créer de nouvelles applications, nous sommes souvent responsables de la modernisation des charges de travail héritées qui sont essentielles pour l’entreprise. Au fil du temps, une application héritée peut être décomposée en microservices, en conteneur et finalement « replate-forme » dans une architecture Cloud native.

### <a name="modernizing-legacy-apps"></a>Moderniser des applications héritées

Le livre électronique gratuit de Microsoft, [moderniser les applications .NET existantes avec des conteneurs Cloud et Windows Azure](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) fournit des conseils pour la migration des charges de travail locales vers le Cloud. La figure 1-10 montre qu’il n’existe pas de stratégie unique, unique et adaptée à la modernisation des applications héritées.

![Stratégies de migration des charges de travail héritées](./media/strategies-for-migrating-legacy-workloads.png)

**Figure 1-10**. Stratégies de migration des charges de travail héritées

Les applications monolithiques non critiques bénéficient en grande partie d’une migration rapide (prête à l'[emploi pour l’infrastructure cloud](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)). Ici, la charge de travail locale est réhébergée sur une machine virtuelle basée sur le Cloud, sans modification. Cette approche utilise le [modèle IaaS (infrastructure as a service)](https://azure.microsoft.com/overview/what-is-iaas/). Azure comprend plusieurs outils tels que [Azure Migrate](https://azure.microsoft.com/services/azure-migrate/), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)et [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) pour faciliter ce type de déplacement. Bien que cette stratégie puisse entraîner des économies, ces applications n’ont généralement pas été conçues pour se déverrouiller et tirer parti des avantages de cloud computing.

Les applications monolithiques qui sont essentielles pour l’entreprise bénéficient souvent d’une migration améliorée avec élévation et décalage (*optimisée*pour le Cloud). Cette approche comprend des optimisations de déploiement qui activent les services de Cloud Computing clés, sans modifier l’architecture principale de l’application. Par exemple, vous pouvez créer un [conteneur](/virtualization/windowscontainers/about/) pour l’application et la déployer dans un Orchestrator de conteneur, comme [Azure Kubernetes services](https://azure.microsoft.com/services/kubernetes-service/), abordé plus loin dans cet ouvrage. Une fois dans le Cloud, l’application peut consommer d’autres services Cloud tels que les bases de données, les files d’attente de messages, la surveillance et la mise en cache distribuée.

Enfin, les applications monolithiques qui exécutent des fonctions d’entreprise stratégiques peuvent tirer le meilleur parti d’une approche *Cloud Native* , l’objet de ce livre. Cette approche offre une agilité et une vélocité. Mais il s’agit d’un coût de recréation de plate-forme, de remaniement et de réécriture du code.

Si vous et votre équipe estimez qu’une approche Cloud-native est appropriée, elle vous permet de rationaliser la décision avec votre organisation. Qu’est-ce qui est exactement le problème de l’entreprise qu’une approche Cloud Native peut résoudre ? Comment l’aligner sur les besoins de l’entreprise ?

- Versions rapides des fonctionnalités avec une confiance accrue ?

- Évolutivité fine-une utilisation plus efficace des ressources ?

- Amélioration de la résilience du système ?

- Amélioration des performances du système ?

- Plus de visibilité sur les opérations ?

- Fusionnez les plateformes de développement et les magasins de données pour obtenir l’outil le mieux adapté à la tâche.

- Un investissement d’application durable ?

La stratégie de migration appropriée dépend des priorités organisationnelles et des systèmes que vous ciblez. Pour beaucoup, il peut s’avérer plus rentable de Cloud-optimiser une application monolithique ou d’ajouter des services à granularité grossière à une application multiniveau. Dans ce cas, vous pouvez toujours tirer pleinement parti des fonctionnalités PaaS du Cloud, telles que celles proposées par Azure App Service.

## <a name="summary"></a>Résumé

Dans ce chapitre, nous avons introduit l’informatique Native Cloud. Nous avons fourni une définition avec les fonctionnalités clés qui pilotent une application Cloud native. Nous avons examiné les types d’applications qui peuvent justifier cet investissement et ce travail.

Avec l’introduction de, nous nous penchons maintenant sur un examen bien plus détaillé du Cloud native.

### <a name="references"></a>Références

- [Base Cloud Native Computing](https://www.cncf.io/)

- [Microservices .NET : architecture pour les applications .NET en conteneur](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [Modèles natifs Cloud par Cornelia Davis](https://www.manning.com/books/cloud-native-patterns)

- [Au-delà de l’application à 12 facteurs](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [Qu’est-ce que l’infrastructure en tant que code ?](/azure/devops/learn/what-is-infrastructure-as-code)

- [Micro deploy de l’ingénierie Uber : déploiement quotidien en toute confiance](https://eng.uber.com/micro-deploy/)

- [Comment Netflix déploie le code](https://www.infoq.com/news/2013/06/netflix/)

- [Contrôle de surcharge pour la mise à l’échelle des microservices WeChat](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
>[Précédent](definition.md) 
> [Suivant](introduce-eshoponcontainers-reference-app.md)
