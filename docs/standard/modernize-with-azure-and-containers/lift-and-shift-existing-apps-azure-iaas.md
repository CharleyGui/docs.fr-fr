---
title: Lift- and -shift des applications .NET existantes vers Azure IaaS (Infrastructure prête pour le Cloud)
description: Moderniser des Applications .NET existantes avec le Cloud Azure et les conteneurs Windows.
ms.date: 04/28/2018
ms.openlocfilehash: cda316ad01a58f26661395c804547de04e20d052
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758862"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>Lift- and -shift des applications .NET existantes vers Azure IaaS (Infrastructure prête pour le Cloud)

> Vision : Dans un premier temps, pour réduire votre investissement local et le coût total du matériel et la maintenance de la mise en réseau, il vous suffit ré-héberger vos applications existantes dans le cloud.

Avant d’aborder *comment* pour migrer vos applications existantes à l’infrastructure en tant que service (IaaS) plateforme Azure, il est important d’analyser les raisons *pourquoi* vous pourriez souhaiter migrer directement vers IaaS dans Azure. Le scénario à ce niveau de maturité de modernisation consiste essentiellement à commencer à utiliser des machines virtuelles dans le cloud, au lieu de continuer à utiliser votre infrastructure locale actuelle.

Un autre point à analyser est *pourquoi* vous pouvez choisir de migrer vers pur cloud IaaS au lieu d’ajouter simplement la plus avancée des services gérés dans Azure. Déterminer quel cas peuvent nécessiter IaaS en premier lieu.

Figure 2-1 positionne prêt pour l’Infrastructure Cloud des applications dans les niveaux de maturité de modernisation :

![Positionnement des applications de prêt pour l’Infrastructure Cloud](./media/image2-1.png)

> **Figure 2-1.** Positionnement des applications de prêt pour l’Infrastructure Cloud

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Pourquoi migrer des applications web .NET existantes vers Azure IaaS

La principale raison de migrer vers le cloud, même au niveau de IaaS initial, consiste à réduire les coûts. À l’aide des services d’infrastructure gérés plus, votre organisation peut réduire ses investissements dans la maintenance du matériel, serveur ou l’approvisionnement de machine virtuelle et le déploiement et gestion de l’infrastructure.

Une fois que vous apportez à la décision de migrer vos applications vers le cloud, la principale raison pour lesquelles vous pourriez choisir IaaS au lieu des options plus avancées telles que le PaaS est simplement que l’environnement IaaS seront plus familier. Déplacement vers un environnement qui est similaire à votre actif, environnement local offre une courbe d’apprentissage plus faible, ce qui rend le chemin d’accès plus rapide vers le cloud.

Toutefois, en prenant le chemin d’accès plus rapide vers le cloud ne signifie pas que vous serez un bénéfice maximal d’avoir vos applications s’exécutant dans le cloud. N’importe quelle organisation sera bénéficiez des avantages plus significatives à partir d’une migration vers le cloud aux niveaux de maturité de Cloud natives et optimisé pour le Cloud déjà évoqué.

Il est également devenu évident que les applications sont plus faciles à moderniser et réorganisez à l’avenir, lorsqu’ils sont déjà en cours d’exécution dans le cloud, même sur IaaS. Migration de données d’application a déjà été effectuée. En outre, votre organisation sera ont acquis des compétences nécessaires pour travailler dans le cloud et de faire l’équipe d’exploitation dans une culture « nuage ».

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>Quand migrer vers IaaS au lieu de pour PaaS

Les sections suivant est optimisé pour le Cloud des applications qui reposent principalement sur les services et plateformes PaaS. Ces applications vous offrent les avantages de la plupart à partir de la migration vers le cloud. 

Si votre objectif consiste simplement à déplacer des applications existantes vers le cloud, tout d’abord, identifiez les applications existantes qui n’exige pas de modification importante de l’exécuter dans Azure App Service. Ces applications doivent être les premières à être concernées pour optimisé pour le Cloud. 

Ensuite, pour les applications qui toujours Impossible de déplacer vers les conteneurs Windows et PaaS comme App Service ou des orchestrateurs tels que Azure Kubernetes Service, migration vers des machines virtuelles plain (IaaS) simples des. 

Toutefois, n’oubliez pas que correctement configuration, la sécurisation et la maintenance des machines virtuelles nécessitent beaucoup plus de temps et d’expertise en informatique comparé à l’utilisation des services PaaS dans Azure. Si vous envisagez d’utiliser des Machines virtuelles Azure, veillez à prendre en compte l’effort de maintenance continue pour les corriger, mettre à jour et gérer votre environnement de machine virtuelle. Machines virtuelles Azure est IaaS.

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Utilisation d’Azure Migrate pour analyser et migrer vos applications existantes vers Azure

Migration vers le nuage ne doit pas être difficile. Mais de nombreuses entreprises éprouvent des difficultés à démarrer - pour obtenir une meilleure visibilité dans l’environnement et les interdépendances étroite entre les applications, les charges de travail et les données. Sans cette visibilité, il peut être difficile à planifier le chemin d’accès vers l’avant. Sans les informations détaillées sur les éléments requis pour une migration réussie, vous ne pouvez avoir les conversations droit au sein de votre organisation. Vous ne connaissez pas suffisamment sur les avantages, économiques potentiels ou si les charges de travail peut simplement lift-and-shift ou nécessiteraient retravailler de manière importante pour migrer avec succès. Pas étonnant que de nombreuses organisations hésitent.

[Azure Migrate](https://aka.ms/azuremigrate) est un nouveau service qui fournit les conseils et les mécanismes nécessaires pour vous aider à migrer vers Azure. Azure Migrate fournit :

- Découverte et l’évaluation pour les machines virtuelles en local

- Mappage des dépendances intégré pour la découverte en toute confiance des applications multicouches

- Intelligent dimensionnement bon aux machines virtuelles Azure

- Création de rapports avec des instructions pour corriger les problèmes potentiels de compatibilité

- Intégration avec le Service de gestion de base de données Azure pour la découverte de la base de données et de migration

Azure Migrate vous donne l’assurance que vos charges de travail peuvent effectuer une migration avec un impact minimal sur l’entreprise et s’exécuter comme prévu dans Azure. Avec les bons outils et les conseils, vous pouvez obtenir maximal retour sur investissement tout en assurant que performances critiques et les besoins de fiabilité sont remplies.

Figure 2-2 montre le mappage de dépendances intégrée pour toutes les connexions de serveur et l’application effectuée par Azure Migrate.

![Positionnement des applications de prêt pour l’Infrastructure Cloud](./media/image2-2.png)

> **Figure 2-2.** Positionnement des applications de prêt pour l’Infrastructure Cloud

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Utiliser Azure Site Recovery pour migrer vos machines virtuelles existantes vers les machines virtuelles Azure

Dans le cadre de l’end-to-end [Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) est un outil qui vous permettent de facilement migrer vos applications web vers les machines virtuelles dans Azure. Vous pouvez utiliser Site Recovery pour répliquer des machines virtuelles locales et des serveurs physiques vers Azure, ou pour les répliquer vers un emplacement secondaire en local. Vous pouvez encore répliquer une charge de travail qui s’exécute sur une machine virtuelle Azure pris en charge, sur un site *Hyper-V* machine virtuelle, dans un *VMware* machine virtuelle, ou sur un serveur physique Windows ou Linux. Réplication vers Azure élimine le coût et la complexité de la maintenance d’un centre de données secondaire.

Site Recovery est également destiné spécifiquement aux environnements hybrides qui sont en partie en local et en partie sur Azure. Site Recovery permet de garantir la continuité d’activité en maintenant les applications qui sont exécutent sur des machines virtuelles et en local des serveurs physiques disponibles si un site tombe en panne. Il réplique les charges de travail qui sont exécutent sur des machines virtuelles et des serveurs physiques afin qu’ils restent disponibles dans un emplacement secondaire si le site principal n’est pas disponible. Il récupère les charges de travail sur le site principal lorsque c’est et nouveau.

Figure 2-3 illustre l’exécution de plusieurs migrations de machine virtuelle à l’aide d’Azure Site Recovery.

![Positionnement des applications de prêt pour l’Infrastructure Cloud](./media/image2-3.png)

> **Figure 2-3.** Positionnement des applications de prêt pour l’Infrastructure Cloud

### <a name="additional-resources"></a>Ressources supplémentaires

- **Azure Migrate feuille de données**

    <https://aka.ms/azuremigration\_datasheet>

- **Azure Migrate**

    <https://aka.ms/azuremigrate>

- **Centre de migration Azure**

    <https://azure.microsoft.com/migration/>

- **Migrer vers Azure avec Site Recovery**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- **Présentation de service Azure Site Recovery**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- **Migration de machines virtuelles dans AWS vers des machines virtuelles Azure**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
>[Précédent](index.md)
>[Suivant](migrate-your-relational-databases-to-azure.md)
