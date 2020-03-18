---
title: Quand déployer des conteneurs Windows dans les instances de conteneurs Azure (ACI)
description: Moderniser les applications .NET existantes avec les conteneurs Azure Cloud et Windows (fr) Quand déployer des conteneurs Windows dans les instances de conteneurs Azure (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69577932"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Quand déployer des conteneurs Windows dans les instances de conteneurs Azure (ACI)

Azure Container Instances principale proposition de valeur est que vous pouvez immédiatement déployer des conteneurs à elle et vous n’avez pas besoin de maintenir cet environnement, vous n’avez pas besoin de mettre à niveau / patcher le système d’exploitation sous-jacent ou VMs, tout ce qui est transparent et vous venez de déployer des conteneurs dans un environnement prêt à l’emploi.

Les raisons et les scénarios lorsque vous souhaitez utiliser ACI sont similaires aux principaux scénarios lorsque vous utilisez des VM Azure avec des conteneurs, donc fondamentalement, les principaux scénarios pour l’utilisation azure Container Instances sont les suivantes:

- **Scénarios Dev/Test**
- **Automatisation des tâches**
- **Agents CI/CD**
- **Traitement par lots à petite échelle**
- **Applications web simples**

Le scénario simple des applications Web est un scénario équitable pour ACI, mais prenez en compte que puisque dans ACI vous ne pouvez avoir qu’une seule instance de conteneur par image de conteneur, vous n’aurez pas une grande disponibilité et n’aurez qu’une évolutivité limitée.

Cependant, même lorsque L’ACI est considérée comme une infrastructure parce qu’elle ne fournit que des instances de conteneur unique, il y a un énorme avantage par rapport aux VM Azure réguliers avec Windows Server. Avec ACI, vous venez de déployer les conteneurs dans un environnement auto-entretenu et vous venez de payer pour ces conteneurs. Vous n’avez pas besoin de maintenir / mise à jour / patch VMs, il est donc une plate-forme beaucoup mieux pour la plupart des scénarios où vous pourriez utiliser des VM avec des conteneurs. L’utilisation d’ACI est simple, vous venez de déployer un conteneur, il n’est pas nécessaire de créer un environnement VM que vous venez de déployer des conteneurs.

Les principaux avantages des instances de conteneurs Azure (ACI) sont :

- Exécuter des conteneurs sans gérer les serveurs
- Augmenter l’agilité avec les conteneurs à la demande
- Déployez des conteneurs dans le nuage avec une simplicité et une vitesse sans précédent, avec une seule commande.
- Applications sécurisées avec isolement hyperviseur

En bref, avec ACI, vous pouvez développer des applications rapidement sans gérer les machines virtuelles ou d’avoir à apprendre de nouveaux outils. C’est juste votre application, dans un conteneur, en cours d’exécution dans le nuage.

> [!div class="step-by-step"]
> [Suivant précédent](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [Next](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
