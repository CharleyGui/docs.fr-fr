---
title: Scénarios de migration vers le cloud hybride
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Migrer vers des scénarios de Cloud hybride
ms.date: 04/30/2018
ms.openlocfilehash: 4348a9b538042fee7ebd9c08f480491f17425937
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394542"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>Scénarios de migration vers le cloud hybride

Certaines organisations et entreprises ne peuvent pas migrer certaines de leurs applications vers des clouds publics comme Microsoft Azure ou tout autre cloud public en raison de réglementations ou de leurs propres stratégies. Toutefois, il est probable qu’une organisation puisse tirer parti de certaines de ses applications dans le cloud public et d’autres applications locales. Toutefois, un environnement mixte peut entraîner une complexité excessive dans les environnements en raison des différentes plateformes et technologies utilisées dans les clouds publics et les environnements locaux.

Microsoft fournit la meilleure solution de Cloud hybride, dans laquelle vous pouvez optimiser vos ressources existantes localement et dans le cloud public, tout en garantissant la cohérence dans un Cloud hybride Azure. Vous pouvez optimiser vos compétences existantes et bénéficier d’une approche unifiée et flexible de la création d’applications qui peuvent s’exécuter dans le Cloud ou localement, grâce à Azure Stack (sur site) et Azure (cloud public).

En matière de sécurité, vous pouvez centraliser la gestion et la sécurité dans votre Cloud hybride. Vous pouvez contrôler toutes les ressources, de votre centre de donnée vers le Cloud, en fournissant une authentification unique aux applications locales et Cloud. Pour ce faire, vous étendez Active Directory à un Cloud hybride et à l’aide de la gestion des identités.

Enfin, vous pouvez distribuer et analyser les données en toute transparence, utiliser les mêmes langages de requête pour les ressources Cloud et locales, et appliquer des analyses et une formation profonde dans Azure pour enrichir vos données, quelle que soit leur source.

## <a name="azure-stack"></a>Azure Stack

Azure Stack est une plateforme Cloud hybride qui vous permet de fournir des services Azure à partir du centre de donnes de votre organisation. Azure Stack est conçu pour prendre en charge de nouvelles options pour vos applications modernes dans des scénarios clés, tels que des environnements Edge et non connectés, ou pour répondre à des exigences spécifiques en matière de sécurité et de conformité.

La figure 4-13 montre une vue d’ensemble de la véritable plateforme Cloud hybride offerte par Microsoft.

![Diagramme de la plateforme Cloud hybride Microsoft avec Azure Stack et Azure.](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

**Figure 4-13.** Plateforme Cloud hybride Microsoft avec Azure Stack et Azure

Azure Stack est proposé dans deux options de déploiement pour répondre à vos besoins :

- Systèmes intégrés Azure Stack

- Kit de développement Azure Stack

### <a name="azure-stack-integrated-systems"></a>Systèmes intégrés Azure Stack

Azure Stack systèmes intégrés sont proposés par le biais d’un partenariat entre Microsoft et des partenaires matériels. Le partenariat crée une solution qui offre une innovation à l’rythme du Cloud qui est équilibrée par la simplicité de la gestion. Étant donné que Azure Stack est proposé en tant que système intégré de matériel et de logiciels, vous bénéficiez de la flexibilité et du contrôle appropriés, tout en adoptant l’innovation à partir du Cloud. Azure Stack systèmes intégrés ont une taille comprise entre 4 et 12 nœuds et sont pris en charge conjointement par le partenaire matériel et Microsoft. Utilisez Azure Stack systèmes intégrés pour implémenter de nouveaux scénarios pour vos charges de travail de production.

### <a name="azure-stack-development-kit"></a>Kit de développement Azure Stack

Microsoft Azure Stack Kit de développement est un déploiement à un seul nœud de Azure Stack, que vous pouvez utiliser pour évaluer et découvrir les Azure Stack. Vous pouvez également utiliser Kit de développement Azure Stack en tant qu’environnement de développement, où vous pouvez développer à l’aide d’API et d’outils qui sont cohérents avec Azure. Kit de développement Azure Stack n’est pas destiné à être utilisé en tant qu’environnement de production.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Cloud hybride Azure**

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- **Azure Stack**

    <https://azure.microsoft.com/overview/azure-stack/>

- **Active Directory les comptes de service pour les conteneurs Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- **Créer un conteneur avec prise en charge de Active Directory**

    <https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/>

- **Licences Azure Hybrid Benefit**

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
>[Précédent](life-cycle-ci-cd-pipelines-devops-tools.md)
>[Suivant](../walkthroughs-technical-get-started-overview.md)
