---
title: Orchestration des microservices et des applications à plusieurs conteneurs pour une grande scalabilité et une haute disponibilité
description: Apprenez à déployer une application à l’aide d’Azure Kubernetes Service.
ms.date: 08/06/2020
ms.openlocfilehash: b4deb9906e0fece7fb611b6988df576e8b07fe46
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916105"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="5fb1d-103">Déployer sur Azure Kubernetes Service (AKS)</span><span class="sxs-lookup"><span data-stu-id="5fb1d-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="5fb1d-104">Vous pouvez interagir avec AKS à l’aide de votre système d’exploitation client préféré (Windows, macOS ou Linux) avec l’interface de ligne de commande Azure (Azure CLI) installée.</span><span class="sxs-lookup"><span data-stu-id="5fb1d-104">You can interact with AKS using your preferred client operating system (Windows, macOS, or Linux) with Azure command-line interface(Azure CLI) installed.</span></span> <span data-ttu-id="5fb1d-105">Pour plus d’informations, consultez Azure CLI Guide de [documentation](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest) et d' [installation](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) pour les environnements disponibles.</span><span class="sxs-lookup"><span data-stu-id="5fb1d-105">For more details, refer [Azure CLI documentation](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest) and [Installation guide](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) for the available environments.</span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="5fb1d-106">Créer l’environnement AKS dans Azure</span><span class="sxs-lookup"><span data-stu-id="5fb1d-106">Create the AKS environment in Azure</span></span>

<span data-ttu-id="5fb1d-107">Il existe plusieurs façons de créer l’environnement AKS.</span><span class="sxs-lookup"><span data-stu-id="5fb1d-107">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="5fb1d-108">Vous pouvez le faire à l’aide des commandes Azure CLI ou à l’aide de l’Portail Azure.</span><span class="sxs-lookup"><span data-stu-id="5fb1d-108">It can be done by using Azure CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="5fb1d-109">Ici, vous pouvez explorer des exemples à l’aide de la Azure CLI pour créer le cluster et le Portail Azure pour passer en revue les résultats.</span><span class="sxs-lookup"><span data-stu-id="5fb1d-109">Here you can explore some examples using the Azure CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="5fb1d-110">Vous devez aussi disposer de Kubectl et de Docker sur votre ordinateur de développement.</span><span class="sxs-lookup"><span data-stu-id="5fb1d-110">You also need to have Kubectl and Docker in your development machine.</span></span>

## <a name="create-the-aks-cluster"></a><span data-ttu-id="5fb1d-111">Créer le cluster AKS</span><span class="sxs-lookup"><span data-stu-id="5fb1d-111">Create the AKS cluster</span></span>

<span data-ttu-id="5fb1d-112">Créez le cluster AKS à l’aide de cette commande (le groupe de ressources doit exister) :</span><span class="sxs-lookup"><span data-stu-id="5fb1d-112">Create the AKS cluster using this command (the resource group must exist):</span></span>

```console
az aks create --resource-group explore-docker-aks-rg --name explore-docker-aks --node-vm-size Standard_B2s --node-count 1 --generate-ssh-keys --location westeurope
```

> [!NOTE]
> <span data-ttu-id="5fb1d-113">Les `--node-vm-size` `--node-count` valeurs des paramètres et sont suffisantes pour une application d’exemple/développement.</span><span class="sxs-lookup"><span data-stu-id="5fb1d-113">The `--node-vm-size` and `--node-count` parameter values are good enough for a sample/dev application.</span></span>

<span data-ttu-id="5fb1d-114">Une fois le travail de création terminé, vous pouvez voir :</span><span class="sxs-lookup"><span data-stu-id="5fb1d-114">After the creation job finishes, you can see:</span></span>

- <span data-ttu-id="5fb1d-115">Cluster AKS créé dans le groupe de ressources initial</span><span class="sxs-lookup"><span data-stu-id="5fb1d-115">The AKS cluster created in the initial resource group</span></span>
- <span data-ttu-id="5fb1d-116">Nouveau groupe de ressources associé, contenant les ressources associées au cluster AKS, comme indiqué dans les images suivantes.</span><span class="sxs-lookup"><span data-stu-id="5fb1d-116">A new, related resource group, containing the resources related to the AKS cluster, as show in the following images.</span></span>

<span data-ttu-id="5fb1d-117">Le groupe de ressources initial, avec le cluster AKS :</span><span class="sxs-lookup"><span data-stu-id="5fb1d-117">The initial resource group, with the AKS cluster:</span></span>

![Vue d’un groupe de ressources AKS dans le navigateur.](media/deploy-azure-kubernetes-service/aks-cluster-view.png)

<span data-ttu-id="5fb1d-119">**Figure 4-17**.</span><span class="sxs-lookup"><span data-stu-id="5fb1d-119">**Figure 4-17**.</span></span> <span data-ttu-id="5fb1d-120">Vue du groupe de ressources AKS dans Azure.</span><span class="sxs-lookup"><span data-stu-id="5fb1d-120">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="5fb1d-121">Groupe de ressources de cluster AKS :</span><span class="sxs-lookup"><span data-stu-id="5fb1d-121">The AKS cluster resource group:</span></span>

![Vue du groupe de ressources Azure AKS dans le navigateur.](media/deploy-azure-kubernetes-service/aks-resource-group-view.png)

<span data-ttu-id="5fb1d-123">**Figure 4-18**.</span><span class="sxs-lookup"><span data-stu-id="5fb1d-123">**Figure 4-18**.</span></span> <span data-ttu-id="5fb1d-124">Vue d’AKS dans Azure.</span><span class="sxs-lookup"><span data-stu-id="5fb1d-124">AKS view from Azure.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5fb1d-125">En général, vous ne devez pas modifier les ressources dans le groupe de ressources de cluster AKS.</span><span class="sxs-lookup"><span data-stu-id="5fb1d-125">In general, you shouldn't need to modify the resources in the AKS cluster resource group.</span></span> <span data-ttu-id="5fb1d-126">Par exemple, le groupe de ressources est supprimé lorsque vous supprimez le cluster AKS.</span><span class="sxs-lookup"><span data-stu-id="5fb1d-126">For example, the resource group is deleted when you delete the AKS cluster.</span></span>

<span data-ttu-id="5fb1d-127">Vous pouvez aussi examiner le nœud créé en utilisant `Azure CLI` et `Kubectl`.</span><span class="sxs-lookup"><span data-stu-id="5fb1d-127">You can also view the node created using `Azure CLI` and `Kubectl`.</span></span>

<span data-ttu-id="5fb1d-128">Première étape : obtention des informations d’identification :</span><span class="sxs-lookup"><span data-stu-id="5fb1d-128">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![Sortie de la console à partir de la commande ci-dessus : fusionnée « explore-docker-AKS » comme contexte actuel dans/Home/Miguel/.Kube/config.](media/deploy-azure-kubernetes-service/get-credentials-command-result.png)

<span data-ttu-id="5fb1d-130">**Figure 4-19**.</span><span class="sxs-lookup"><span data-stu-id="5fb1d-130">**Figure 4-19**.</span></span> <span data-ttu-id="5fb1d-131">Résultat de la commande `aks get-credentials`.</span><span class="sxs-lookup"><span data-stu-id="5fb1d-131">`aks get-credentials` command result.</span></span>

<span data-ttu-id="5fb1d-132">Ensuite, obtention des nœuds à partir de Kubectl :</span><span class="sxs-lookup"><span data-stu-id="5fb1d-132">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![Sortie de la console à partir de la commande ci-dessus : liste des nœuds dont l’État, l’âge (heure d’exécution) et la version](media/deploy-azure-kubernetes-service/kubectl-get-nodes-command-result.png)

<span data-ttu-id="5fb1d-134">**Figure 4-20**.</span><span class="sxs-lookup"><span data-stu-id="5fb1d-134">**Figure 4-20**.</span></span> <span data-ttu-id="5fb1d-135">Résultat de la commande `kubectl get nodes`.</span><span class="sxs-lookup"><span data-stu-id="5fb1d-135">`kubectl get nodes` command result.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="5fb1d-136">[Précédent](orchestrate-high-scalability-availability.md) 
>  [Suivant](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="5fb1d-136">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
