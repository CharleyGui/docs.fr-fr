---
title: Quand déployer des conteneurs de Windows Azure Container Instances (ACI)
description: Moderniser des applications .NET existantes avec des conteneurs de Cloud Azure et Windows | Quand déployer des conteneurs de Windows Azure Container Instances (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758597"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Quand déployer des conteneurs de Windows Azure Container Instances (ACI)

Azure Container Instances proposition de valeur principale est que vous pouvez immédiatement déployer des conteneurs à celui-ci et que vous n’avez pas besoin de mettre à jour de cet environnement, vous n’avez pas besoin de mise à niveau/correction, le système d’exploitation ou les machines virtuelles, tout cela est transparent sous-jacente et que vous venez de déployer conteneurs dans un environnement prêt à l’emploi.

Les raisons et les scénarios lorsque vous souhaitez utiliser ACI sont similaires pour les principaux scénarios lorsque vous utilisez des machines virtuelles Azure avec des conteneurs, en gros, les principaux scénarios pour l’utilisation d’Azure Container Instances sont :

- **Scénarios de développement/Test**
- **Automatisation des tâches**
- **Agents de CI/CD**
- **Traitement par lots de petite/mise à l’échelle**
- **Applications web simples**

Le scénario d’applications web simple est un scénario juste pour ACI mais prendre en compte qu’étant donné que dans ACI vous ne pouvez avoir qu’une instance de conteneur unique par l’image de conteneur, vous n’aurez pas une haute disponibilité et avez uniquement une évolutivité limitée.

Toutefois, même lorsque ACI est considérée comme l’infrastructure, car il fournit simplement des instances de conteneur unique, il est un énorme avantage par rapport à ceux des machines virtuelles Azure avec Windows Server. Avec ACI, vous déployez simplement les conteneurs dans un environnement de mise à jour automatique, et vous payez uniquement pour ces conteneurs. Vous n’avez pas besoin mettre à jour/mise à jour/correctifs machines virtuelles, par conséquent, il est une meilleure plateforme pour la plupart des scénarios où vous pouvez utiliser des machines virtuelles avec des conteneurs. À l’aide d’ACI est très simple, vous déployez simplement un conteneur, il est inutile de créer un environnement de machine virtuelle que vous déployez simplement des conteneurs.

Les principaux avantages d’Azure Container Instances (ACI) sont :

- Exécuter des conteneurs sans gestion de serveurs
- Augmenter l’agilité avec des conteneurs à la demande
- Déployer des conteneurs vers le cloud avec une simplicité et une vitesse, avec une seule commande.
- Applications sécurisées avec l’isolation de l’hyperviseur

En bref, vous pouvez développer des applications avec ACI rapidement sans gestion d’ordinateurs virtuels ou de devoir apprendre de nouveaux outils. Il s’agit simplement votre application, dans un conteneur, en cours d’exécution dans le cloud.

> [!div class="step-by-step"]
> [Précédent](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [Suivant](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
