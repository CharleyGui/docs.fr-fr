---
title: Tirez et passez des applications .NET existantes à Azure IaaS (Cloud Infrastructure-prêt)
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure.
ms.date: 04/28/2018
ms.openlocfilehash: d610222aa6649c1b28e198c074794dd316f895ec
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172168"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>Tirez et passez des applications .NET existantes à Azure IaaS (Cloud Infrastructure-prêt)

> Vision : dans un premier temps, pour réduire votre investissement local et le coût total de maintenance du matériel et de la mise en réseau, il vous suffit de réhéberger vos applications existantes dans le Cloud.

Avant d' *apprendre* à migrer vos applications existantes vers la plateforme Azure infrastructure as a service (IaaS), il est important d’analyser les raisons pour *lesquelles* vous souhaiteriez migrer directement vers IaaS dans Azure. Le scénario à ce niveau de maturité de modernisation consiste essentiellement à commencer à utiliser des machines virtuelles dans le Cloud, au lieu de continuer à utiliser votre infrastructure locale actuelle.

Un autre point à analyser est la *raison pour laquelle* vous souhaiterez peut-être migrer vers le Cloud IaaS pur plutôt que d’ajouter simplement des services gérés plus avancés dans Azure. Déterminez les cas qui peuvent nécessiter IaaS en premier lieu.

La figure 2-1 positionne les applications prêtes pour l’infrastructure cloud dans les niveaux de maturité de modernisation :

![Positionnement des applications prêtes pour l’infrastructure cloud](./media/image2-1.png)

**Figure 2-1.** Positionnement des applications prêtes pour l’infrastructure cloud

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Pourquoi migrer des applications Web .NET existantes vers Azure IaaS

La principale raison de migrer vers le Cloud, même au niveau d’un IaaS initial, est de réduire les coûts. En utilisant des services d’infrastructure plus gérés, votre organisation peut réduire son investissement dans la maintenance matérielle, l’approvisionnement et le déploiement de serveurs ou de machines virtuelles, ainsi que la gestion de l’infrastructure.

Une fois que vous avez pris la décision de migrer vos applications vers le Cloud, la raison principale pour laquelle vous pouvez choisir IaaS plutôt que des options plus avancées comme PaaS est simplement que l’environnement IaaS sera plus familier. Le passage à un environnement similaire à votre environnement local actuel offre une courbe d’apprentissage inférieure, ce qui en fait le chemin le plus rapide vers le Cloud.

Toutefois, le fait d’avoir le chemin le plus rapide vers le Cloud ne signifie pas que vous tirerez le meilleur parti de l’exécution de vos applications dans le Cloud. Toute organisation bénéficiera des avantages les plus significatifs d’une migration Cloud aux niveaux de maturité déjà introduits dans le Cloud et optimisés pour le Cloud.

Il est également évident que les applications sont plus faciles à moderniser et à remanier dans le futur quand elles s’exécutent déjà dans le Cloud, même sur IaaS. La migration des données d’application a déjà été effectuée. En outre, votre organisation aura acquis les compétences nécessaires pour travailler dans le Cloud et a fait passer le fonctionnement dans une « culture Cloud ».

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>Quand migrer vers IaaS au lieu de PaaS

Les sections suivantes traitent des applications optimisées pour le Cloud qui sont principalement basées sur les plateformes et les services PaaS. Ces applications vous offrent les avantages de la migration vers le Cloud.

Si votre objectif est simplement de déplacer des applications existantes vers le Cloud, identifiez d’abord les applications existantes qui ne nécessitent pas de modifications substantielles pour s’exécuter dans Azure App Service. Ces applications doivent être les premiers candidats à l’optimisation du Cloud.

Ensuite, pour les applications qui ne peuvent toujours pas être migrées vers des conteneurs Windows et PaaS, comme des App Service ou des orchestrateurs tels que le service Azure Kubernetes, migrez-les vers des machines virtuelles simples (IaaS) simples.

Toutefois, gardez à l’esprit que la configuration, la sécurisation et la maintenance des machines virtuelles nécessitent bien plus de temps et d’expertise informatique par rapport à l’utilisation des services PaaS dans Azure. Si vous envisagez d’utiliser des machines virtuelles Azure, veillez à prendre en compte l’effort de maintenance en cours requis pour corriger, mettre à jour et gérer votre environnement de machine virtuelle. Machines virtuelles Azure est IaaS.

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Utiliser Azure Migrate pour analyser et migrer vos applications existantes vers Azure

La migration vers le Cloud n’a pas besoin d’être difficile. Toutefois, de nombreuses organisations éprouvent des difficultés à démarrer : pour bénéficier d’une visibilité détaillée de l’environnement et des interdépendances étroites entre les applications, les charges de travail et les données. Sans cette visibilité, il peut être difficile de planifier le chemin vers l’avant. Sans informations détaillées sur les éléments requis pour une migration réussie, vous ne pouvez pas avoir les bonnes conversations au sein de votre organisation. Vous ne connaissez pas les avantages en matière de coûts potentiels, ou si les charges de travail peuvent simplement être levées et déplacées ou nécessiter un retravail important pour réussir la migration. Il n’est pas étonnant que de nombreuses organisations hésitent.

[Azure Migrate](https://aka.ms/azuremigrate) est un nouveau service qui fournit des conseils, des Insights et des mécanismes nécessaires pour vous aider à migrer vers Azure. Azure Migrate fournit :

- Découverte et évaluation pour les machines virtuelles locales

- Mappage de dépendances incorporé pour la découverte à haute confiance des applications multicouches

- Dimensionnement intelligent des machines virtuelles Azure

- Rapports de compatibilité avec des instructions pour résoudre les problèmes potentiels

- Intégration au service de gestion de base de données Azure pour la découverte et la migration des bases de données

Azure Migrate vous donne la certitude que vos charges de travail peuvent migrer avec un impact minimal sur l’activité et s’exécuter comme prévu dans Azure. Avec les bons outils et conseils, vous pouvez obtenir un retour sur investissement maximal tout en garantissant la satisfaction des besoins critiques en matière de performances et de fiabilité.

La figure 2-2 montre le mappage de dépendances intégré pour toutes les connexions de serveur et d’application effectuées par Azure Migrate.

![Positionnement des applications prêtes pour l’infrastructure cloud](./media/image2-2.png)

**Figure 2-2.** Positionnement des applications prêtes pour l’infrastructure cloud

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Utiliser Azure Site Recovery pour migrer vos machines virtuelles existantes vers des machines virtuelles Azure

Dans le cadre de l' [Azure Migrate](https://aka.ms/azuremigrate)de bout en bout, [Azure Site Recovery](/azure/site-recovery/site-recovery-overview) est un outil que vous pouvez utiliser pour migrer facilement vos applications Web vers des machines virtuelles dans Azure. Vous pouvez utiliser Site Recovery pour répliquer des machines virtuelles locales et des serveurs physiques vers Azure, ou pour les répliquer vers un emplacement local secondaire. Vous pouvez même répliquer une charge de travail qui s’exécute sur une machine virtuelle Azure prise en charge, sur une machine virtuelle *Hyper-V* locale, sur une machine virtuelle *VMware* ou sur un serveur physique Windows ou Linux. La réplication sur Azure réduit le coût et la complexité qu’implique la maintenance d’un centre de données secondaire.

Site Recovery est également conçu spécifiquement pour les environnements hybrides qui sont partiellement locaux et en partie sur Azure. Site Recovery permet de garantir la continuité des activités en conservant les applications qui s’exécutent sur les machines virtuelles et les serveurs physiques locaux disponibles en cas de panne d’un site. Il réplique les charges de travail qui s’exécutent sur les machines virtuelles et les serveurs physiques afin qu’ils restent disponibles dans un emplacement secondaire si le site principal n’est pas disponible. Ce service récupère les charges de travail sur le site principal lorsqu’il fonctionne à nouveau.

La figure 2-3 illustre l’exécution de plusieurs migrations de machine virtuelle à l’aide de Azure Site Recovery.

![Positionnement des applications prêtes pour l’infrastructure cloud](./media/image2-3.png)

**Figure 2-3.** Positionnement des applications prêtes pour l’infrastructure cloud

### <a name="additional-resources"></a>Ressources supplémentaires

- **Feuille de données Azure Migrate**

    <https://aka.ms/azuremigration\_datasheet>

- **Azure Migrate**

    <https://aka.ms/azuremigrate>

- **Centre de migration Azure**

    <https://azure.microsoft.com/migration/>

- **Effectuer une migration vers Azure avec Site Recovery**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- **Présentation du service Azure Site Recovery**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- **Migration de machines virtuelles dans AWS vers des machines virtuelles Azure**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
>[Précédent](index.md) 
> [Suivant](migrate-your-relational-databases-to-azure.md) <!-- Next Chapter -->
