---
title: Orchestration des microservices et des applications à plusieurs conteneurs pour une grande scalabilité et une haute disponibilité
description: Apprenez à déployer une application à l’aide d’Azure Kubernetes Service.
ms.date: 02/15/2019
ms.openlocfilehash: 88e76b4b0a3686f4227a6aee1b7fbd2bfe55fdcc
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2019
ms.locfileid: "65644650"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a>Déployer sur Azure Kubernetes Service (AKS)

Vous pouvez interagir avec AKS en utilisant votre système d’exploitation client préféré. Ici, nous vous montrons comment avec Microsoft Windows et une version incorporée d’Ubuntu Linux dans Windows, avec des commandes Bash.

Avant d’utiliser AKS, vous devez répondre aux prérequis suivants :

- Ordinateur de développement Linux ou Mac
- Ordinateur de développement Windows
  - Mode Développeur activé sur Windows
  - Sous-système Windows pour Linux
- Azure-CLI installé sur [Windows, Mac ou Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)

> [!NOTE]
> Pour trouver des informations complètes sur :
>
> Azure-CLI : <https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest>
>
> Sous-système Windows pour Linux : <https://docs.microsoft.com/windows/wsl/about>

## <a name="create-the-aks-environment-in-azure"></a>Créer l’environnement AKS dans Azure

Il existe plusieurs façons de créer l’environnement AKS. Il est possible d’utiliser les commandes Azure-CLI ou le portail Azure.

Vous trouverez ici quelques exemples utilisant Azure-CLI pour créer le cluster et le portail Azure pour examiner les résultats. Vous devez aussi disposer de Kubectl et de Docker sur votre ordinateur de développement.  

## <a name="create-the-aks-cluster"></a>Créer le cluster AKS

Créez le cluster AKS à l’aide de cette commande :

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

Une fois la tâche de création terminée, vous pouvez examiner le cluster AKS créé sur le portail Azure :

Le groupe de ressources :

![Vue du groupe de ressources Azure AKS dans le navigateur.](media/aks-resource-group-view.png)

**Figure 4-17**. Vue du groupe de ressources AKS dans Azure.

Le cluster AKS :

![Vue d’un groupe de ressources AKS dans le navigateur.](media/aks-cluster-view.png)

**Figure 4-18**. Vue d’AKS dans Azure.

Vous pouvez aussi examiner le nœud créé en utilisant `Azure-CLI` et `Kubectl`.

Première étape : obtention des informations d’identification :

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Sortie de la commande ci-dessus dans la console : Merged "MsSampleK8Cluster as current context in /root/.kube/config.](media/get-credentials-command-result.png)

**Figure 4-19**. Résultat de la commande `aks get-credentials`.

Ensuite, obtention des nœuds à partir de Kubectl :

```console
kubectl get nodes
```

![Sortie de la commande ci-dessus dans la console : Liste des nœuds avec indication de l’état, de l’âge (temps d’exécution) et de la version](media/kubectl-get-nodes-command-result.png)

**Figure 4-20**. Résultat de la commande `kubectl get nodes`.

>[!div class="step-by-step"]
>[Précédent](orchestrate-high-scalability-availability.md)
>[Suivant](docker-apps-development-environment.md)
