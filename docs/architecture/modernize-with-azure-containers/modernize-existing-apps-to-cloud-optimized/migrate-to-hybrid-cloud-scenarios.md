---
title: Scénarios de migration vers le cloud hybride
description: Moderniser les applications .NET existantes avec les conteneurs Azure Cloud et Windows (fr) Migrer vers des scénarios de cloud hybrides
ms.date: 04/30/2018
ms.openlocfilehash: dcbb799a45609f8bb811866c4041951abf1fda8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937361"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>Scénarios de migration vers le cloud hybride

Certaines organisations et entreprises ne peuvent pas migrer certaines de leurs applications vers des nuages publics comme Microsoft Azure ou tout autre cloud public en raison de la réglementation ou de leurs propres politiques. Cependant, il est probable que n’importe quelle organisation pourrait bénéficier d’avoir certaines de leurs applications dans le cloud public et d’autres applications sur place. Mais un environnement mixte peut conduire à une complexité excessive dans les environnements en raison de différentes plates-formes et technologies utilisées dans les nuages publics par rapport aux environnements sur place.

Microsoft fournit la meilleure solution de cloud hybride, dans laquelle vous pouvez optimiser vos actifs existants sur place et dans le cloud public, tandis que vous assurez la cohérence dans un nuage hybride Azure. Vous pouvez maximiser les compétences existantes et obtenir une approche flexible et unifiée pour construire des applications qui peuvent s’exécuter dans le cloud ou sur place, grâce à Azure Stack (sur place) et Azure (nuage public).

En matière de sécurité, vous pouvez centraliser la gestion et la sécurité à travers votre cloud hybride. Vous pouvez obtenir le contrôle de tous les actifs, de votre centre de données au cloud, en fournissant un seul signe sur les sites et les applications cloud. Pour ce faire, vous étendez Active Directory à un cloud hybride et en utilisant la gestion de l’identité.

Enfin, vous pouvez distribuer et analyser les données de manière transparente, utiliser les mêmes langages de requête pour les ressources cloud et sur site, et appliquer l’analyse et l’apprentissage profond en Azure pour enrichir vos données, quelle que soit leur source.

## <a name="azure-stack"></a>Azure Stack

Azure Stack est une plate-forme cloud hybride qui vous permet de fournir des services Azure à partir du centre de données de votre organisation. Azure Stack est conçu pour prendre en charge de nouvelles options pour vos applications modernes dans des scénarios clés, comme les environnements de bord et non connectés, ou répondre à des exigences spécifiques en matière de sécurité et de conformité.

La figure 4-13 montre un aperçu de la véritable plate-forme de cloud hybride que Microsoft offre.

![Diagramme de la plate-forme cloud hybride Microsoft avec Azure Stack et Azure.](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

**Figure 4-13.** Plateforme cloud hybride Microsoft avec Azure Stack et Azure

Azure Stack est proposé en deux options de déploiement, pour répondre à vos besoins :

- Systèmes intégrés Azure Stack

- Kit de développement Azure Stack

### <a name="azure-stack-integrated-systems"></a>Systèmes intégrés Azure Stack

Les systèmes intégrés Azure Stack sont proposés par le biais d’un partenariat entre Microsoft et des partenaires matériels. Le partenariat crée une solution qui offre une innovation au rythme cloud qui est équilibrée avec simplicité dans la gestion. Azure Stack étant proposé en tant que système intégré de matériels et de logiciels, vous bénéficiez de la flexibilité et du contrôle adéquats, tout en adoptant l’innovation propre au cloud. Les systèmes intégrés Azure Stack varient en taille de 4 à 12 nœuds, et sont pris en charge conjointement par le partenaire matériel et Microsoft. Utilisez les systèmes intégrés Azure Stack pour implémenter de nouveaux scénarios pour votre charge de travail de production.

### <a name="azure-stack-development-kit"></a>Kit de développement Azure Stack

Le Kit de développement Microsoft Azure Stack est un déploiement à un seul nœud d’Azure Stack qui vous permet de découvrir et d’évaluer Azure Stack. Vous pouvez également utiliser Azure Stack Development Kit en tant qu’environnement de développeur, où vous pouvez développer à l’aide d’API et d’outillage qui sont compatibles avec Azure. Le Kit de développement Azure Stack n’est pas destiné à être utilisé en tant qu’environnement de production.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Nuage hybride Azure**

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- **Pile Azure**

    <https://azure.microsoft.com/overview/azure-stack/>

- **Comptes de service Active Directory pour les conteneurs Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- **Créer un conteneur avec le support d’annuaire actif**

    <https://docs.microsoft.com/archive/blogs/containerstuff/create-a-container-with-active-directory-support>

- **Licence Azure Hybrid Benefit**

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
>[Suivant précédent](life-cycle-ci-cd-pipelines-devops-tools.md)
>[Next](../walkthroughs-technical-get-started-overview.md)
