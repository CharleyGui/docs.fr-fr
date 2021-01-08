---
title: Quand déployer des conteneurs Windows sur des machines virtuelles Azure (cloud IaaS)
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Quand déployer des conteneurs Windows sur des machines virtuelles Azure (Cloud IaaS)
ms.date: 12/21/2020
ms.openlocfilehash: 64ba53fa56227266ee0e61a128d18373a2dbbc93
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025092"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Quand déployer des conteneurs Windows sur des machines virtuelles Azure (cloud IaaS)

Si votre organisation utilise des machines virtuelles Azure, même si vous utilisez également des conteneurs Windows, vous avez toujours affaire à IaaS. Cela signifie que le traitement des opérations d’infrastructure, des correctifs du système d’exploitation de la machine virtuelle et de la complexité de l’infrastructure pour les applications hautement évolutives lorsque vous devez effectuer un déploiement sur plusieurs machines virtuelles dans une infrastructure à charge équilibrée. Les principaux scénarios d’utilisation des conteneurs Windows dans une machine virtuelle Azure sont les suivants :

- **Environnement de développement/test**: une machine virtuelle dans le Cloud est parfaite pour le développement et le test dans le Cloud. Vous pouvez rapidement créer ou arrêter l’environnement en fonction de vos besoins.

- **Besoins en matière d’évolutivité petite et moyenne**: dans les scénarios où vous pouvez avoir besoin de quelques machines virtuelles pour votre environnement de production, la gestion de quelques machines virtuelles peut être abordable jusqu’à ce que vous puissiez passer à des environnements PaaS plus avancés, comme les orchestrateurs.

- **Environnement de production avec les outils de déploiement existants**: vous pouvez migrer à partir d’un environnement local dans lequel vous avez investi dans des outils pour effectuer des déploiements complexes sur des machines virtuelles ou des serveurs nus (tels que marionnette ou outils similaires). Pour migrer vers le Cloud avec des modifications minimes des procédures de déploiement de l’environnement de production, vous pouvez continuer à utiliser ces outils pour déployer sur des machines virtuelles Azure. Toutefois, vous souhaiterez utiliser des conteneurs Windows comme unité de déploiement pour améliorer l’expérience de déploiement.

>[!div class="step-by-step"]
>[Précédent](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md) 
> [Suivant](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
