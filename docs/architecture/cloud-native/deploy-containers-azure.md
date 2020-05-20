---
title: Déploiement de conteneurs dans Azure
description: Déploiement de conteneurs dans Azure avec Azure Container Registry, Azure Kubernetes service et Azure Dev Spaces.
ms.date: 04/13/2020
ms.openlocfilehash: ba2854323ee0f1394a3cff0dd3756cb3c7c32d5b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614147"
---
# <a name="deploying-containers-in-azure"></a>Déploiement de conteneurs dans Azure

Nous avons abordé les conteneurs dans ce chapitre et dans le chapitre 1. Nous avons vu que les conteneurs offrent de nombreux avantages aux applications Cloud natives, y compris la portabilité. Dans le Cloud Azure, vous pouvez déployer les mêmes services en conteneur dans les environnements intermédiaires et de production. Azure propose plusieurs options pour héberger ces charges de travail en conteneur :

- Azure Kubernetes Services (AKS)
- Azure Container Instances (ACI)
- Web Apps Azure pour les conteneurs

## <a name="azure-container-registry"></a>Azure Container Registry

Lors du conteneur d’un microservice, vous commencez par créer une image de conteneur de Build. L’image est une représentation binaire du code de service, des dépendances et du Runtime. Bien que vous puissiez créer manuellement une image à l’aide de la `Docker Build` commande à partir de l’API d’ancrage, une meilleure approche consiste à la créer dans le cadre d’un processus de génération automatisé.

Une fois créés, les images de conteneur sont stockées dans des registres de conteneurs. Ils vous permettent de créer, de stocker et de gérer des images de conteneur. De nombreux registres sont disponibles, publics et privés. Azure Container Registry (ACR) est un service de registre de conteneurs entièrement géré dans le Cloud Azure. Il conserve vos images dans le réseau Azure, ce qui réduit le temps de déploiement sur les hôtes de conteneur Azure. Vous pouvez également les sécuriser à l’aide des mêmes procédures de sécurité et d’identité que celles que vous utilisez pour d’autres ressources Azure.

Vous créez un Azure Container Registry à l’aide des outils [portail Azure](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-portal), [Azure CLI](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-azure-cli)ou [PowerShell](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-powershell). La création d’un registre dans Azure est simple. Il nécessite un abonnement Azure, un groupe de ressources et un nom unique. La figure 3-11 montre les options de base pour la création d’un registre, qui sera hébergé sur `registryname.azurecr.io` .

![Créer un registre de conteneurs](./media/create-container-registry.png)

**Figure 3-11**. Créer un registre de conteneurs

Une fois que vous avez créé le registre, vous devez vous authentifier auprès de celui-ci avant de pouvoir l’utiliser. En règle générale, vous vous connectez au registre à l’aide de la commande Azure CLI :

```azurecli
az acr login --name *registryname*
```

Une fois authentifié, vous pouvez utiliser les commandes de l’arrimeur pour envoyer des images de conteneur vers celui-ci. Toutefois, avant de pouvoir le faire, vous devez baliser votre image avec le nom complet (URL) de votre serveur de connexion ACR. Son format est *registryname*. azurecr.IO.

```console
docker tag mycontainer myregistry.azurecr.io/mycontainer:v1
```

Une fois que vous avez balisé l’image, vous utilisez la `docker push` commande pour envoyer l’image à votre instance ACR.

```console
docker push myregistry.azurecr.io/mycontainer:v1
```

Une fois que vous avez envoyé une image vers le registre, il est judicieux de supprimer l’image de votre environnement d’ancrage local, à l’aide de la commande suivante :

```console
docker rmi myregistry.azurecr.io/mycontainer:v1
```

En guise de meilleure pratique, les développeurs ne doivent pas transmettre manuellement les images à un registre de conteneurs. Au lieu de cela, un pipeline de build défini dans un outil tel que GitHub ou Azure DevOps doit être responsable de ce processus. Pour en savoir plus, consultez le [chapitre DevOps natif de Cloud](devops.md).

## <a name="acr-tasks"></a>ACR Tasks

[ACR tâches](https://docs.microsoft.com/azure/container-registry/container-registry-tasks-overview) est un ensemble de fonctionnalités disponibles à partir de la Azure Container Registry. Il étend le [cycle de développement de la boucle interne](https://docs.microsoft.com/dotnet/architecture/containerized-lifecycle/design-develop-containerized-apps/docker-apps-inner-loop-workflow) en générant et en gérant des images de conteneur dans le Cloud Azure. Au lieu d’appeler un `docker build` et `docker push` localement sur votre machine de développement, elles sont gérées automatiquement par des tâches ACR dans le Cloud.

La commande suivante AZ CLI génère une image conteneur et la transmet à ACR :

```azurecli
# create a container registry
az acr create --resource-group myResourceGroup --name myContainerRegistry008 --sku Basic

# build container image in ACR and push it into your container regsitry
az acr build --image sample/hello-world:v1  --registry myContainerRegistry008 --file Dockerfile .
```

Comme vous pouvez le voir à partir du bloc de commandes précédent, il n’est pas nécessaire d’installer le Bureau de l’ordinateur d’amarrage sur votre ordinateur de développement. En outre, vous pouvez configurer des déclencheurs de tâche ACR pour reconstruire des images de conteneurs sur le code source et les mises à jour d’image de base.

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Nous avons abordé le service Azure Kubernetes (AKS) à la longueur de ce chapitre. Nous avons vu qu’il s’agit de l’orchestrateur de conteneurs de facto qui gère les applications Cloud natives en conteneur.

Une fois que vous avez déployé une image dans un registre, tel que ACR, vous pouvez configurer AKS pour l’extraire et le déployer automatiquement. Avec un pipeline CI/CD en place, vous pouvez configurer une stratégie de mise à jour des [Canaries](https://martinfowler.com/bliki/CanaryRelease.html) pour réduire le risque lié à la rapidité de déploiement des mises à jour. La nouvelle version de l’application est initialement configurée en production, sans acheminer le trafic vers celle-ci. Le système achemine ensuite un petit pourcentage d’utilisateurs vers la version récemment déployée. À mesure que l’équipe gagne en confiance dans la nouvelle version, elle peut déployer plus d’instances et mettre l’ancien hors service. AKS prend en charge facilement ce type de déploiement.

Comme pour la plupart des ressources dans Azure, vous pouvez créer un cluster de service Azure Kubernetes à l’aide du portail, de la ligne de commande ou des outils d’automatisation tels que Helm ou Terraform. Pour commencer à utiliser un nouveau cluster, vous devez fournir les informations suivantes :

- Abonnement Azure
- Resource group
- Nom du cluster Kubernetes
- Région
- Version de Kubernetes
- Préfixe du nom DNS
- Taille du nœud
- Nombre de nœuds

Ces informations sont suffisantes pour commencer. Dans le cadre du processus de création de la Portail Azure, vous pouvez également configurer des options pour les fonctionnalités suivantes de votre cluster :

- Scale
- Authentification
- Mise en réseau
- Surveillance
- Étiquettes

Ce [Guide de démarrage rapide vous guide dans le déploiement d’un cluster AKS à l’aide de l’portail Azure](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

Les applications Cloud natives peuvent rapidement devenir volumineuses et complexes, ce qui nécessite des ressources de calcul importantes pour s’exécuter. Dans ces scénarios, l’ensemble de l’application ne peut pas être hébergé sur un ordinateur de développement (en particulier un ordinateur portable). Azure Dev Spaces est conçu pour résoudre ce problème à l’aide de AKS. Il permet aux développeurs de travailler avec une version locale de leurs services tout en hébergeant le reste de l’application dans un cluster de développement AKS.

Les développeurs partagent une instance en cours d’exécution (développement) dans un cluster AKS qui contient l’application en conteneur entière. Mais ils utilisent des espaces personnels configurés sur leur ordinateur pour développer localement leurs services. Lorsqu’ils sont prêts, ils testent de bout en bout dans le cluster AKS, sans répliquer les dépendances. Azure Dev Spaces fusionne le code à partir de l’ordinateur local avec les services dans AKS. Les développeurs peuvent rapidement itérer et déboguer du code directement dans Kubernetes à l’aide de Visual Studio ou Visual Studio Code.

Pour comprendre la valeur de Azure Dev Spaces, permettez-moi de partager ce devis à partir de Gabe Monroy, responsable des conteneurs à l’Microsoft Azure :

> «Imaginez que vous êtes un nouvel employé tentant de résoudre un bogue dans une application de microservices complexe composée de dizaines de composants, chacun avec ses propres services de configuration et de stockage. Pour commencer, vous devez configurer votre environnement de développement local afin qu’il puisse imiter la production, y compris la configuration de votre IDE, la création d’une chaîne d’outils, les dépendances de service en conteneur, un environnement Kubernetes local, des simulacres pour les services de stockage, et bien plus encore. Avec tout le temps nécessaire à la configuration de votre environnement de développement, la résolution de ce premier bogue peut prendre plusieurs jours.
> Ou vous pouvez utiliser des espaces de développement et des AKS.»

Le processus d’utilisation de Azure Dev Spaces implique les étapes suivantes :

1. Créez l’espace de développement.
2. Configurez l’espace de développement racine.
3. Configurez un espace de développement enfant (pour votre propre version du système).
4. Connectez-vous à l’espace de développement.

Toutes ces étapes peuvent être effectuées à l’aide de la Azure CLI et de nouveaux `azds` outils en ligne de commande. Par exemple, pour créer un espace de développement Azure pour un cluster Kubernetes donné, vous devez utiliser une commande similaire à celle-ci :

```azurecli
az aks use-dev-spaces -g my-aks-resource-group -n MyAKSCluster
```

Ensuite, vous pouvez utiliser la `azds prep` commande pour générer les ressources de l’ancrage et du graphique Helm nécessaires pour l’exécution de l’application. Ensuite, vous exécutez votre code dans AKS à l’aide de `azds up` . La première fois que vous exécutez cette commande, le graphique Helm est installé. Les conteneurs sont générés et déployés conformément à vos instructions. Cette tâche peut prendre quelques minutes la première fois qu’elle est exécutée. Toutefois, une fois que vous avez apporté des modifications, vous pouvez vous connecter à votre propre espace de développement enfant à l’aide de, puis `azds space select` déployer et déboguer vos mises à jour dans votre espace de développement enfant isolé. Une fois que votre espace de développement est opérationnel, vous pouvez lui envoyer des mises à jour en réexécutant la `azds up` commande ou vous pouvez utiliser les outils intégrés dans Visual Studio ou Visual Studio code. Avec VS Code, vous utilisez la palette de commandes pour vous connecter à votre espace de développement. La figure 3-12 montre comment lancer votre application Web à l’aide de Azure Dev Spaces dans Visual Studio.

![Connectez-vous à Azure Dev Spaces dans Visual Studio ](./media/azure-dev-spaces-visual-studio-launchsettings.png)
 **figure 3-12**. Se connecter à Azure Dev Spaces dans Visual Studio

>[!div class="step-by-step"]
>[Précédent](combine-containers-serverless-approaches.md) 
> [Suivant](scale-containers-serverless.md)
