---
title: Déploiement de conteneurs dans Azure
description: Déploiement de conteneurs dans Azure avec Azure Container Registry, le service Azure Kubernetes et Azure Dev Spaces.
ms.date: 06/30/2019
ms.openlocfilehash: 6d95db26b6a45dd6825c88693308ffe90d1ed071
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183265"
---
# <a name="deploying-containers-in-azure"></a>Déploiement de conteneurs dans Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Les conteneurs présentent de nombreux avantages, dont l’un est portabilité. Vous pouvez facilement utiliser le même conteneur que vous avez développé et testé localement et le déployer sur Azure où il peut exécuter votre application dans des environnements intermédiaires et de production. Azure fournit un certain nombre d’options pour l’hébergement d’applications basées sur des conteneurs et prend également en charge plusieurs moyens de déploiement différents. L’approche la plus courante et la plus souple consiste à déployer vos conteneurs sur Azure Container Registry (ACR), où ils sont accessibles par les services que vous souhaitez utiliser pour les héberger. Azure Web App pour conteneurs, Azure Kubernetes services (AKS) et Azure Container instance (ACI) peuvent tous accéder aux images de conteneur ayant fait l’objet d’un push vers ACR.

## <a name="azure-container-registry"></a>Azure Container Registry

Azure Container Registry (ACR) vous permet de créer, de stocker et de gérer des images pour tous vos déploiements de conteneur. Il existe d’autres registres de conteneur, publics et privés, sur lesquels vous pouvez déployer des conteneurs. L’avantage de ACR par rapport à d’autres options est que vous pouvez garder vos images plus près de votre environnement de production, ce qui améliore les temps de création et de déploiement. Vous pouvez également les sécuriser à l’aide des mêmes procédures de sécurité que celles que vous utilisez pour le reste de vos ressources Azure, ce qui améliore la sécurité et réduit l’effort de gestion des ressources.

Vous [créez un registre de conteneurs à l’aide du portail Azure](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-portal) ou [à l’aide des outils Azure CLI](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-azure-cli) ou [PowerShell](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-powershell). Pour créer un registre de conteneurs, vous devez simplement disposer d’un abonnement Azure, d’un groupe de ressources et d’un nom unique. La figure 3-11 montre les options de base pour la création d’un registre, qui sera hébergé sur *registryname*. azurecr.IO.

![Créez le Registre](./media/create-container-registry.png)
de conteneurs**figure 3-11**. Créer un registre de conteneurs

Une fois que vous avez créé un registre, vous devez vous authentifier auprès de celui-ci avant de pouvoir l’utiliser. En règle générale, vous vous connectez au registre à l’aide de la commande Azure CLI :

```azurecli
az acr login --name *registryname*
```

Une fois que vous avez créé un registre dans Azure Container Registry, vous pouvez utiliser les commandes de l’arrimeur pour envoyer des images de conteneur vers celui-ci. Toutefois, avant de pouvoir le faire, vous devez d’abord baliser votre image avec le nom complet (URL) de votre serveur de connexion ACR. Le format est *registryname*. azurecr.IO.

```console
docker tag mycontainer myregistry.azurecr.io/mycontainer:v1
```

Une fois que vous avez balisé l’image, vous `docker push` utilisez la commande pour envoyer l’image à votre instance ACR.

```console
docker push myregistry.azurecr.io/mycontainer:v1
```

Une fois que vous avez envoyé une image vers le registre, il est judicieux de supprimer l’image de votre environnement d’ancrage local, à l’aide de la commande suivante :

```console
docker rmi myregistry.azurecr.io/mycontainer:v1
```

Les développeurs doivent rarement envoyer des notifications push directement depuis leurs ordinateurs vers un registre de conteneurs. Au lieu de cela, un pipeline de build défini dans un outil comme Azure DevOps doit être responsable de ce processus. Pour en savoir plus, consultez le [chapitre DevOps natif de Cloud](devops.md).

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Si votre application basée sur un conteneur implique plusieurs conteneurs, vous souhaiterez probablement définir et gérer les interactions entre les conteneurs à l’aide d’un *orchestrateur* comme Kubernetes. Une fois que vous avez déployé vos images de conteneur dans ACR, vous pouvez facilement configurer les services Azure Kubernetes pour déployer automatiquement les images mises à jour à partir de ACR. Avec un pipeline CI/CD complet, vous pouvez configurer une stratégie de mise à jour des [Canaries](https://martinfowler.com/bliki/CanaryRelease.html) pour réduire le risque lié à la rapidité de déploiement des mises à jour. La nouvelle version de l’application est initialement configurée en production sans acheminer le trafic vers celle-ci, puis un petit nombre d’utilisateurs est routé vers la nouvelle version déployée de l’application. À mesure que l’équipe gagne en confiance dans la nouvelle version du logiciel, d’autres instances de la nouvelle version sont déployées et les instances de la version précédente sont retirées. AKS prend en charge facilement ce type de déploiement.

Comme pour la plupart des ressources dans Azure, vous pouvez créer des clusters Azure Kubernetes à l’aide du portail ou à l’aide d’outils en ligne de commande ou d’outils d’automatisation d’infrastructure tels que Helm ou Terraform. Pour commencer à utiliser un nouveau cluster, vous devez fournir les informations suivantes :

- Abonnement Azure
- Groupe de ressources
- Nom du cluster Kubernetes
- Région
- Version de Kubernetes
- Préfixe du nom DNS
- Taille du nœud
- Nombre de nœuds

Ces informations sont suffisantes pour commencer. Dans le cadre du processus de création dans le portail Azure, vous pouvez également configurer des options pour les fonctionnalités suivantes de votre cluster :

- Échelle
- Authentification
- Réseau
- Analyse
- Balises

Ce [Guide de démarrage rapide vous guide dans le déploiement d’un cluster AKS à l’aide de l’portail Azure](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

Les clusters Kubernetes complexes peuvent nécessiter des ressources importantes pour héberger, ce qui peut compliquer l’exécution de l’application entière sur un seul ordinateur (en particulier un ordinateur portable) pour les développeurs. Azure Dev Spaces offre une solution en permettant aux développeurs de travailler avec leurs propres versions des clusters Azure Kubernetes hébergés dans Azure. Azure Dev Spaces est conçu pour faciliter le développement d’applications basées sur des microservices à l’aide de AKS.

Pour comprendre la valeur de Azure Dev Spaces, permettez-moi de partager ce devis à partir de Gabe Monroy, responsable des conteneurs à l’Microsoft Azure :

«Imaginez que vous êtes un nouvel employé tentant de résoudre un bogue dans une application de microservices complexe composée de dizaines de composants, chacun avec ses propres services de configuration et de stockage. Pour commencer, vous devez configurer votre environnement de développement local afin qu’il puisse imiter la production, y compris la configuration de votre IDE, la création d’une chaîne d’outils, les dépendances de service en conteneur, un environnement Kubernetes local, des simulacres pour les services de stockage, et bien plus encore. Avec tout le temps nécessaire à la configuration de votre environnement de développement, la résolution de ce premier bogue peut prendre plusieurs jours.

> Ou vous pouvez utiliser des espaces de développement et des AKS.»

Le processus d’utilisation de Azure Dev Spaces implique les étapes suivantes :

1. Créez l’espace de développement.
2. Configurez l’espace de développement racine.
3. Configurez un espace de développement enfant (pour votre propre version du système).
4. Connectez-vous à l’espace de développement.

Toutes ces étapes peuvent être effectuées à l’aide de la Azure CLI `azds` et de nouveaux outils en ligne de commande. Par exemple, pour créer un espace de développement Azure pour un cluster Kubernetes donné, vous devez utiliser une commande similaire à celle-ci :

```azurecli
az aks use-dev-spaces -g my-aks-resource-group -n MyAKSCluster
```

Ensuite, vous pouvez utiliser la `azds prep` commande pour générer les ressources de l’ancrage et du graphique Helm nécessaires pour l’exécution de l’application. Ensuite, vous exécutez votre code dans AKS `azds up`à l’aide de. La première fois que vous exécutez cette commande, le graphique Helm est installé et le ou les conteneurs sont générés et déployés conformément à vos instructions. Cette opération peut prendre quelques minutes la première fois qu’elle est exécutée. Toutefois, une fois que vous avez apporté des modifications, vous pouvez vous connecter à votre `azds space select` propre espace de développement enfant à l’aide de, puis déployer et déboguer vos mises à jour dans votre espace de développement enfant isolé. Une fois que votre espace de développement est opérationnel, vous pouvez lui envoyer des mises à jour en émettant à nouveau la `azds up` commande ou vous pouvez utiliser les outils intégrés dans Visual Studio ou Visual Studio code. Avec VS Code, vous utilisez la palette de commandes pour vous connecter à votre espace de développement. La figure 3-12 montre comment lancer votre application Web à l’aide de Azure Dev Spaces dans Visual Studio.

![Connectez-vous à Azure dev Spaces dans](./media/azure-dev-spaces-visual-studio-launchsettings.png)
Visual Studio**figure 3-12**. Se connecter à Azure Dev Spaces dans Visual Studio

## <a name="references"></a>Références

- [Version de la Canaries](https://martinfowler.com/bliki/CanaryRelease.html)
- [Azure Dev Spaces avec VS Code](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore)
- [Azure Dev Spaces avec Visual Studio](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore-visualstudio)

>[!div class="step-by-step"]
>[Précédent](combine-containers-serverless-approaches.md)
>[Suivant](scale-containers-serverless.md)
