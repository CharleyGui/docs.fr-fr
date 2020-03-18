---
title: Soulevez et déplacez les applications .NET existantes vers Azure IaaS (Cloud Infrastructure-Ready)
description: Modernisez les applications .NET existantes avec le cloud Azure et les conteneurs Windows.
ms.date: 04/28/2018
ms.openlocfilehash: c7638a034dbb27baea1b097bdb66175bfb5a71f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73089638"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>Soulevez et déplacez les applications .NET existantes vers Azure IaaS (Cloud Infrastructure-Ready)

> Vision : Dans un premier temps, pour réduire votre investissement sur site et le coût total de la maintenance matérielle et réseautage, il suffit de relogeler vos applications existantes dans le cloud.

Avant d’entrer dans *la façon* de migrer vos applications existantes vers l’infrastructure Azure en tant que plate-forme de service (IaaS), il est important d’analyser les raisons *pour lesquelles* vous souhaitez migrer directement vers IaaS à Azure. Le scénario à ce niveau de maturité de modernisation est essentiellement de commencer à utiliser des VM dans le cloud, au lieu de continuer à utiliser votre infrastructure actuelle sur place.

Un autre point à analyser est *pourquoi* vous pourriez vouloir migrer vers le nuage IaaS pur au lieu de simplement ajouter des services gérés plus avancés dans Azure. Déterminez les cas qui pourraient nécessiter l’IaaS en premier lieu.

La figure 2-1 positionne les applications Cloud Infrastructure-Ready dans les niveaux de maturité de modernisation :

![Positionnement des applications Cloud Infrastructure-Ready](./media/image2-1.png)

**Figure 2-1.** Positionnement des applications Cloud Infrastructure-Ready

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Pourquoi migrer les applications web .NET existantes vers Azure IaaS

La principale raison de migrer vers le cloud, même à un niveau initial IaaS, est d’atteindre des réductions de coûts. En utilisant des services d’infrastructure plus gérés, votre organisation peut réduire son investissement dans la maintenance matérielle, l’approvisionnement et le déploiement de VM, ainsi que dans la gestion de l’infrastructure.

Après avoir pris la décision de déplacer vos applications vers le cloud, la principale raison pour laquelle vous pourriez choisir IaaS au lieu d’options plus avancées comme PaaS est simplement que l’environnement IaaS sera plus familier. Le passage à un environnement similaire à votre environnement actuel sur place offre une courbe d’apprentissage plus basse, ce qui en fait le chemin le plus rapide vers le cloud.

Cependant, prendre le chemin le plus rapide vers le cloud ne signifie pas que vous gagnerez le plus d’avantages d’avoir vos applications en cours d’exécution dans le nuage. Toute organisation tirera les avantages les plus significatifs d’une migration en nuage aux niveaux de maturité cloud-Optimized et Cloud-Native déjà introduits.

Il est également devenu évident que les applications sont plus faciles à moderniser et à réarchit à l’avenir quand elles sont déjà en cours d’exécution dans le nuage, même sur IaaS. La migration des données d’application a déjà été réalisée. De plus, votre organisation aura acquis les compétences requises pour travailler dans le cloud et a fait le passage à l’exploitation dans une « culture cloud ».

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>Quand migrer vers IaaS au lieu de PaaS

Les sections suivantes traitent des applications optimisées pour le Cloud qui sont principalement basées sur les plates-formes et services PaaS. Ces applications vous donnent le plus d’avantages de la migration vers le cloud.

Si votre objectif est simplement de déplacer les applications existantes vers le cloud, d’abord, identifiez les applications existantes qui ne nécessiteraient pas de modification substantielle pour s’exécuter dans Azure App Service. Ces applications devraient être les premiers candidats pour Cloud-Optimized.

Ensuite, pour les applications qui ne peuvent toujours pas se déplacer vers Windows Containers et PaaS tels que App Service ou orchestrateurs comme Azure Kubernetes Service, migrez-les vers des VM simples (IaaS).

Mais, gardez à l’esprit que la configuration correcte, la sécurisation et le maintien des VM nécessite beaucoup plus de temps et d’expertise informatique par rapport à l’utilisation des services PaaS dans Azure. Si vous envisagez Azure Virtual Machines, assurez-vous de prendre en compte les efforts de maintenance en cours requis pour corriger, mettre à jour et gérer votre environnement VM. Azure Virtual Machines est IaaS.

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Utilisez Azure Migrate pour analyser et migrer vos applications existantes vers Azure

La migration vers le nuage n’a pas besoin d’être difficile. Mais de nombreuses organisations ont du mal à démarrer - pour obtenir une visibilité profonde dans l’environnement et les interdépendances étroites entre les applications, les charges de travail et les données. Sans cette visibilité, il peut être difficile de planifier la voie à suivre. Sans informations détaillées sur ce qui est nécessaire pour une migration réussie, vous ne pouvez pas avoir les bonnes conversations au sein de votre organisation. Vous n’en savez pas assez sur les avantages potentiels des coûts, ou si les charges de travail pourraient simplement lever et déplacer ou nécessiterait une refonte importante pour migrer avec succès. Pas étonnant que beaucoup d’organisations hésitent.

[Azure Migrate](https://aka.ms/azuremigrate) est un nouveau service qui fournit les conseils, les idées et les mécanismes nécessaires pour vous aider à migrer vers Azure. Azure Migrate fournit :

- Découverte et évaluation pour les machines virtuelles sur site

- Cartographie de dépendance intégrée pour la découverte de haute confiance des applications à plusieurs niveaux

- Droit intelligent de taille aux machines virtuelles Azure

- Rapports de compatibilité avec des lignes directrices pour remédier aux problèmes potentiels

- Intégration avec le service de gestion de base de données Azure pour la découverte et la migration des bases de données

Azure Migrate vous donne la certitude que vos charges de travail peuvent migrer avec un impact minimal sur l’entreprise et fonctionner comme prévu dans Azure. Avec les bons outils et conseils, vous pouvez obtenir un rendement sur investissement maximal tout en veillant à ce que les besoins critiques en matière de performance et de fiabilité soient satisfaits.

La figure 2-2 vous montre la cartographie intégrée de la dépendance pour toutes les connexions serveur et application effectuées par Azure Migrate.

![Positionnement des applications Cloud Infrastructure-Ready](./media/image2-2.png)

**Figure 2-2.** Positionnement des applications Cloud Infrastructure-Ready

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Utilisez Azure Site Recovery pour migrer vos VM existants vers les VM Azure

Dans le cadre de la [migration Azure](https://aka.ms/azuremigrate)De bout en bout , [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) est un outil que vous pouvez utiliser pour migrer facilement vos applications web vers les machines à VM en Azure. Vous pouvez utiliser La récupération du site pour reproduire les VM sur site et les serveurs physiques à Azure, ou pour les reproduire à un emplacement secondaire sur place. Vous pouvez même reproduire une charge de travail qui fonctionne sur un Azure VM pris en charge, sur un *Hyper-V* VM sur place, sur un *VMware* VM, ou sur un serveur physique Windows ou Linux. La réplication sur Azure réduit le coût et la complexité qu’implique la maintenance d’un centre de données secondaire.

Le rétablissement du site est également fait spécifiquement pour les environnements hybrides qui sont en partie sur place et en partie sur Azure. La récupération de site contribue à assurer la continuité de vos activités en gardant vos applications qui fonctionnent sur les magnétoscopes et les serveurs physiques sur site disponibles en cas de panne d’un site. Il reproduit les charges de travail qui sont en cours d’exécution sur les VM et les serveurs physiques afin qu’ils restent disponibles dans un emplacement secondaire si le site principal n’est pas disponible. Ce service récupère les charges de travail sur le site principal lorsqu’il fonctionne à nouveau.

La figure 2-3 montre l’exécution de multiples migrations de VM en utilisant azure Site Recovery.

![Positionnement des applications Cloud Infrastructure-Ready](./media/image2-3.png)

**Figure 2-3.** Positionnement des applications Cloud Infrastructure-Ready

### <a name="additional-resources"></a>Ressources supplémentaires

- **Feuille de données Azure Migrate**

    <https://aka.ms/azuremigration\_datasheet>

- **Migrement Azure**

    <https://aka.ms/azuremigrate>

- **Centre de migration Azure**

    <https://azure.microsoft.com/migration/>

- **Effectuer une migration vers Azure avec Site Recovery**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- **Aperçu du service de récupération du site Azure**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- **Migrer les machines À sous-Œuvre dans les AWS vers les machines VM Azure**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
>[Suivant précédent](index.md)
>[Next](migrate-your-relational-databases-to-azure.md) <!-- Next Chapter -->
