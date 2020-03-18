---
title: Orchestration des microservices et des applications à plusieurs conteneurs pour une grande scalabilité et une haute disponibilité
description: Apprenez à déployer une application à l’aide d’Azure Kubernetes Service.
ms.date: 02/15/2019
ms.openlocfilehash: 0aa2f83fbf8f9a8815d65730002943cca748643d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "71182369"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="c444e-103">Déployer sur Azure Kubernetes Service (AKS)</span><span class="sxs-lookup"><span data-stu-id="c444e-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="c444e-104">Vous pouvez interagir avec AKS en utilisant votre système d’exploitation client préféré. Ici, nous vous montrons comment avec Microsoft Windows et une version incorporée d’Ubuntu Linux dans Windows, avec des commandes Bash.</span><span class="sxs-lookup"><span data-stu-id="c444e-104">You can interact with AKS using your preferred client operating system, here we show how to do it with Microsoft Windows and an embedded version of Ubuntu Linux in Windows, using Bash commands.</span></span>

<span data-ttu-id="c444e-105">Avant d’utiliser AKS, vous devez répondre aux prérequis suivants :</span><span class="sxs-lookup"><span data-stu-id="c444e-105">Prerequisites to have before using AKS are:</span></span>

- <span data-ttu-id="c444e-106">Ordinateur de développement Linux ou Mac</span><span class="sxs-lookup"><span data-stu-id="c444e-106">Linux or Mac development machine</span></span>
- <span data-ttu-id="c444e-107">Ordinateur de développement Windows</span><span class="sxs-lookup"><span data-stu-id="c444e-107">Windows development machine</span></span>
  - <span data-ttu-id="c444e-108">Mode Développeur activé sur Windows</span><span class="sxs-lookup"><span data-stu-id="c444e-108">Developer Mode enabled on Windows</span></span>
  - <span data-ttu-id="c444e-109">Sous-système Windows pour Linux</span><span class="sxs-lookup"><span data-stu-id="c444e-109">Windows Subsystem for Linux</span></span>
- <span data-ttu-id="c444e-110">Azure-CLI installé sur [Windows, Mac ou Linux](https://docs.microsoft.com/cli/azure/install-azure-cli)</span><span class="sxs-lookup"><span data-stu-id="c444e-110">Azure-CLI installed on [Windows, Mac or Linux](https://docs.microsoft.com/cli/azure/install-azure-cli)</span></span>

> [!NOTE]
> <span data-ttu-id="c444e-111">Pour trouver des informations complètes sur :</span><span class="sxs-lookup"><span data-stu-id="c444e-111">To find complete information about:</span></span>
>
> <span data-ttu-id="c444e-112">Azure-CLI : <https://docs.microsoft.com/cli/azure/index></span><span class="sxs-lookup"><span data-stu-id="c444e-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index></span></span>
>
> <span data-ttu-id="c444e-113">Sous-système Windows pour Linux : <https://docs.microsoft.com/windows/wsl/about></span><span class="sxs-lookup"><span data-stu-id="c444e-113">Windows Subsystem for Linux: <https://docs.microsoft.com/windows/wsl/about></span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="c444e-114">Créer l’environnement AKS dans Azure</span><span class="sxs-lookup"><span data-stu-id="c444e-114">Create the AKS environment in Azure</span></span>

<span data-ttu-id="c444e-115">Il existe plusieurs façons de créer l’environnement AKS.</span><span class="sxs-lookup"><span data-stu-id="c444e-115">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="c444e-116">Il est possible d’utiliser les commandes Azure-CLI ou le portail Azure.</span><span class="sxs-lookup"><span data-stu-id="c444e-116">It can be done by using Azure-CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="c444e-117">Vous trouverez ici quelques exemples utilisant Azure-CLI pour créer le cluster et le portail Azure pour examiner les résultats.</span><span class="sxs-lookup"><span data-stu-id="c444e-117">Here you can explore some examples using the Azure-CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="c444e-118">Vous devez aussi disposer de Kubectl et de Docker sur votre ordinateur de développement.</span><span class="sxs-lookup"><span data-stu-id="c444e-118">You also need to have Kubectl and Docker in your development machine.</span></span>  

## <a name="create-the-aks-cluster"></a><span data-ttu-id="c444e-119">Créer le cluster AKS</span><span class="sxs-lookup"><span data-stu-id="c444e-119">Create the AKS cluster</span></span>

<span data-ttu-id="c444e-120">Créez le cluster AKS à l’aide de cette commande :</span><span class="sxs-lookup"><span data-stu-id="c444e-120">Create the AKS cluster using this command:</span></span>

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

<span data-ttu-id="c444e-121">Une fois la tâche de création terminée, vous pouvez examiner le cluster AKS créé sur le portail Azure :</span><span class="sxs-lookup"><span data-stu-id="c444e-121">After the creation job finishes, you can see the AKS created in the Azure portal:</span></span>

<span data-ttu-id="c444e-122">Le groupe de ressources :</span><span class="sxs-lookup"><span data-stu-id="c444e-122">The resource group:</span></span>

![Vue du groupe de ressources Azure AKS dans le navigateur.](media/aks-resource-group-view.png)

<span data-ttu-id="c444e-124">**Figure 4-17**.</span><span class="sxs-lookup"><span data-stu-id="c444e-124">**Figure 4-17**.</span></span> <span data-ttu-id="c444e-125">Vue du groupe de ressources AKS dans Azure.</span><span class="sxs-lookup"><span data-stu-id="c444e-125">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="c444e-126">Le cluster AKS :</span><span class="sxs-lookup"><span data-stu-id="c444e-126">The AKS cluster:</span></span>

![Vue d’un groupe de ressources AKS dans le navigateur.](media/aks-cluster-view.png)

<span data-ttu-id="c444e-128">**Figure 4-18**.</span><span class="sxs-lookup"><span data-stu-id="c444e-128">**Figure 4-18**.</span></span> <span data-ttu-id="c444e-129">Vue d’AKS dans Azure.</span><span class="sxs-lookup"><span data-stu-id="c444e-129">AKS view from Azure.</span></span>

<span data-ttu-id="c444e-130">Vous pouvez aussi examiner le nœud créé en utilisant `Azure-CLI` et `Kubectl`.</span><span class="sxs-lookup"><span data-stu-id="c444e-130">You can also view the node created using `Azure-CLI` and `Kubectl`.</span></span>

<span data-ttu-id="c444e-131">Première étape : obtention des informations d’identification :</span><span class="sxs-lookup"><span data-stu-id="c444e-131">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Sortie de console de la commande ci-dessus : Fusionné "MsSampleK8Cluster comme contexte actuel dans /root/.kube/config.](media/get-credentials-command-result.png)

<span data-ttu-id="c444e-133">**Figure 4-19**.</span><span class="sxs-lookup"><span data-stu-id="c444e-133">**Figure 4-19**.</span></span> <span data-ttu-id="c444e-134">Résultat de la commande `aks get-credentials`.</span><span class="sxs-lookup"><span data-stu-id="c444e-134">`aks get-credentials` command result.</span></span>

<span data-ttu-id="c444e-135">Ensuite, obtention des nœuds à partir de Kubectl :</span><span class="sxs-lookup"><span data-stu-id="c444e-135">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![Sortie de la console de la commande ci-dessus: Liste des nœuds avec statut, âge (temps en cours d’exécution), et la version](media/kubectl-get-nodes-command-result.png)

<span data-ttu-id="c444e-137">**Figure 4-20**.</span><span class="sxs-lookup"><span data-stu-id="c444e-137">**Figure 4-20**.</span></span> <span data-ttu-id="c444e-138">Résultat de la commande `kubectl get nodes`.</span><span class="sxs-lookup"><span data-stu-id="c444e-138">`kubectl get nodes` command result.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c444e-139">[Suivant précédent](orchestrate-high-scalability-availability.md)
>[Next](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="c444e-139">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
