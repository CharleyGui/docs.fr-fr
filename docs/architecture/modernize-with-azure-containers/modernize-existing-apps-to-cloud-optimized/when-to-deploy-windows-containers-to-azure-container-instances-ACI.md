---
title: Quand déployer des conteneurs Windows sur Azure Container Instances (ACI)
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Quand déployer des conteneurs Windows sur Azure Container Instances (ACI)
ms.date: 12/21/2020
ms.openlocfilehash: 556fe7cbec7d259db9ec886b777feda9eed09116
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025131"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Quand déployer des conteneurs Windows sur Azure Container Instances (ACI)

La principale valeur de Azure Container Instances est que vous pouvez immédiatement déployer des conteneurs sur celui-ci et que vous n’avez pas besoin de gérer cet environnement, vous n’avez pas besoin de mettre à niveau/corriger le système d’exploitation sous-jacent ou les machines virtuelles, tout ce qui est transparent et vous déployez simplement des conteneurs dans un environnement prêt à l’emploi.

Les raisons et les scénarios dans lesquels vous souhaiteriez utiliser ACI sont similaires aux scénarios principaux lorsque vous utilisez des machines virtuelles Azure avec des conteneurs. fondamentalement, les principaux scénarios d’utilisation de Azure Container Instances sont les suivants :

- **Scénarios de développement et de test**
- **Automatisation des tâches**
- **Agents CI/CD**
- **Traitement par lots de petite/échelle**
- **Applications Web simples**

Le scénario Web Apps simple est un scénario équitable pour ACI mais tient compte du fait que dans ACI, vous ne pouvez avoir qu’une seule instance de conteneur par image de conteneur, vous n’avez pas de haute disponibilité et n’avez qu’une évolutivité limitée.

Toutefois, même quand ACI est considéré comme une infrastructure, car elle fournit simplement des instances de conteneur uniques, il y a un avantage énorme par rapport aux machines virtuelles Azure classiques avec Windows Server. Avec ACI, vous déployez simplement les conteneurs dans un environnement autonome et vous payez uniquement pour ces conteneurs. Vous n’avez pas besoin de gérer/mettre à jour/corriger les machines virtuelles. il s’agit donc d’une plateforme bien meilleure pour la plupart des scénarios dans lesquels vous pouvez utiliser des machines virtuelles avec des conteneurs. En utilisant ACI, vous déployez simplement un conteneur, il n’est pas nécessaire de créer un environnement de machine virtuelle que vous venez de déployer.

Les principaux avantages de Azure Container Instances (ACI) sont les suivants :

- Exécuter des conteneurs sans gérer les serveurs
- Améliorez l’agilité avec les conteneurs à la demande
- Déployez des conteneurs dans le Cloud avec une simplicité et une rapidité sans précédent, à l’aide d’une seule commande.
- Sécuriser les applications avec l’isolation hyperviseur

En bref, avec ACI, vous pouvez développer rapidement des applications sans avoir à gérer des machines virtuelles ou à apprendre de nouveaux outils. C’est simplement votre application, dans un conteneur, qui s’exécute dans le Cloud.

> [!div class="step-by-step"]
> [Précédent](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md) 
>  [Suivant](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
