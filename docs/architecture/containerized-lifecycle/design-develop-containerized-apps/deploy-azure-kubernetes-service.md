---
title: Orchestration des microservices et des applications à plusieurs conteneurs pour une grande scalabilité et une haute disponibilité
description: Apprenez à déployer une application à l’aide d’Azure Kubernetes Service.
ms.date: 08/06/2020
ms.openlocfilehash: ba9887c0a4837c16a60ebeb006416c0fa8c105e0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163594"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a>Déployer sur Azure Kubernetes Service (AKS)

Vous pouvez interagir avec AKS à l’aide de votre système d’exploitation client préféré (Windows, macOS ou Linux) avec l’interface de ligne de commande Azure (Azure CLI) installée. Pour plus d’informations, consultez Azure CLI Guide de [documentation](/cli/azure/?view=azure-cli-latest) et d' [installation](/cli/azure/install-azure-cli?view=azure-cli-latest) pour les environnements disponibles.

## <a name="create-the-aks-environment-in-azure"></a>Créer l’environnement AKS dans Azure

Il existe plusieurs façons de créer l’environnement AKS. Vous pouvez le faire à l’aide des commandes Azure CLI ou à l’aide de l’Portail Azure.

Ici, vous pouvez explorer des exemples à l’aide de la Azure CLI pour créer le cluster et le Portail Azure pour passer en revue les résultats. Vous devez aussi disposer de Kubectl et de Docker sur votre ordinateur de développement.

## <a name="create-the-aks-cluster"></a>Créer le cluster AKS

Créez le cluster AKS à l’aide de cette commande (le groupe de ressources doit exister) :

```console
az aks create --resource-group explore-docker-aks-rg --name explore-docker-aks --node-vm-size Standard_B2s --node-count 1 --generate-ssh-keys --location westeurope
```

> [!NOTE]
> Les `--node-vm-size` `--node-count` valeurs des paramètres et sont suffisantes pour une application d’exemple/développement.

Une fois le travail de création terminé, vous pouvez voir :

- Cluster AKS créé dans le groupe de ressources initial
- Nouveau groupe de ressources associé, contenant les ressources associées au cluster AKS, comme indiqué dans les images suivantes.

Le groupe de ressources initial, avec le cluster AKS :

![Vue d’un groupe de ressources AKS dans le navigateur.](media/deploy-azure-kubernetes-service/aks-cluster-view.png)

**Figure 4-17**. Vue du groupe de ressources AKS dans Azure.

Groupe de ressources de cluster AKS :

![Vue du groupe de ressources Azure AKS dans le navigateur.](media/deploy-azure-kubernetes-service/aks-resource-group-view.png)

**Figure 4-18**. Vue d’AKS dans Azure.

> [!IMPORTANT]
> En général, vous ne devez pas modifier les ressources dans le groupe de ressources de cluster AKS. Par exemple, le groupe de ressources est supprimé lorsque vous supprimez le cluster AKS.

Vous pouvez aussi examiner le nœud créé en utilisant `Azure CLI` et `Kubectl`.

Première étape : obtention des informations d’identification :

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![Sortie de la console à partir de la commande ci-dessus : fusionnée « explore-docker-AKS » comme contexte actuel dans/Home/Miguel/.Kube/config.](media/deploy-azure-kubernetes-service/get-credentials-command-result.png)

**Figure 4-19**. Résultat de la commande `aks get-credentials`.

Ensuite, obtention des nœuds à partir de Kubectl :

```console
kubectl get nodes
```

![Sortie de la console à partir de la commande ci-dessus : liste des nœuds dont l’État, l’âge (heure d’exécution) et la version](media/deploy-azure-kubernetes-service/kubectl-get-nodes-command-result.png)

**Figure 4-20**. Résultat de la commande `kubectl get nodes`.

> [!div class="step-by-step"]
> [Précédent](orchestrate-high-scalability-availability.md) 
>  [Suivant](docker-apps-development-environment.md)
