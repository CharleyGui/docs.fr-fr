---
title: Infrastructure en tant que code
description: Architecture des applications .NET natives Cloud pour Azure | Infrastructure en tant que code
ms.date: 06/30/2019
ms.openlocfilehash: 3957da68ac28774f899f49fb181a29c2435902f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087246"
---
# <a name="infrastructure-as-code"></a><span data-ttu-id="57cc9-103">Infrastructure en tant que code</span><span class="sxs-lookup"><span data-stu-id="57cc9-103">Infrastructure as code</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="57cc9-104">Les applications Cloud natives ont tendance à utiliser toutes sortes de composants PaaS (Platform as a service) fantastiques.</span><span class="sxs-lookup"><span data-stu-id="57cc9-104">Cloud-native applications tend to make use of all sorts of fantastic platform as a service (PaaS) components.</span></span> <span data-ttu-id="57cc9-105">Sur une plateforme Cloud comme Azure, ces composants peuvent inclure des éléments tels que le stockage, les Service Bus et le service Signalr.</span><span class="sxs-lookup"><span data-stu-id="57cc9-105">On a cloud platform like Azure, these components might include things like storage, Service Bus, and the SignalR service.</span></span> <span data-ttu-id="57cc9-106">À mesure que les applications deviennent plus compliquées, le nombre de ces services en cours d’utilisation est susceptible de croître.</span><span class="sxs-lookup"><span data-stu-id="57cc9-106">As applications become more complicated, the number of these services in use is likely to grow.</span></span> <span data-ttu-id="57cc9-107">À l’instar de la façon dont la livraison continue a enfreint le modèle traditionnel de déploiement dans un environnement manuellement, le rythme de modification rapide a également enfreint le modèle de gestion des environnements par un groupe informatique centralisé.</span><span class="sxs-lookup"><span data-stu-id="57cc9-107">Just as how continuous delivery broke the traditional model of deploying to an environment manually, the rapid pace of change also broke the model of having a centralized IT group manage environments.</span></span>

<span data-ttu-id="57cc9-108">Les environnements de construction peuvent et doivent également être automatisés.</span><span class="sxs-lookup"><span data-stu-id="57cc9-108">Building environments can, and should, also be automated.</span></span> <span data-ttu-id="57cc9-109">Il existe un large éventail d’outils bien pensés qui peuvent faciliter le processus.</span><span class="sxs-lookup"><span data-stu-id="57cc9-109">There's a wide range of well thought out tools that can make the process easy.</span></span>

## <a name="azure-resource-manager-templates"></a><span data-ttu-id="57cc9-110">Modèles de Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="57cc9-110">Azure Resource Manager templates</span></span>

<span data-ttu-id="57cc9-111">Les modèles Azure Resource Manager sont un langage JSON qui vous aide à définir diverses ressources dans Azure.</span><span class="sxs-lookup"><span data-stu-id="57cc9-111">Azure Resource Manager templates are a JSON-based language for defining various resources in Azure.</span></span> <span data-ttu-id="57cc9-112">Le schéma de base ressemble à ce qui suit : figure 11-10.</span><span class="sxs-lookup"><span data-stu-id="57cc9-112">The basic schema looks something like Figure 11-10.</span></span>

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
  "contentVersion": "",
  "apiProfile": "",
  "parameters": {  },
  "variables": {  },
  "functions": [  ],
  "resources": [  ],
  "outputs": {  }
}
```

<span data-ttu-id="57cc9-113">**Figure 11-10** -schéma d’un modèle de gestionnaire des ressources</span><span class="sxs-lookup"><span data-stu-id="57cc9-113">**Figure 11-10** - The schema for a Resource Manager template</span></span>

<span data-ttu-id="57cc9-114">Dans ce modèle, il est possible de définir un conteneur de stockage à l’intérieur de la section des ressources, comme suit :</span><span class="sxs-lookup"><span data-stu-id="57cc9-114">Within this template, one might define a storage container inside the resources section like so:</span></span>

```json
"resources": [
    {
      "type": "Microsoft.Storage/storageAccounts",
      "name": "[variables('storageAccountName')]",
      "location": "[parameters('location')]",
      "apiVersion": "2018-07-01",
      "sku": {
        "name": "[parameters('storageAccountType')]"
      },
      "kind": "StorageV2",
      "properties": {}
    }
  ],
```

<span data-ttu-id="57cc9-115">**Figure 11-11** : exemple de compte de stockage défini dans un modèle de gestionnaire des ressources</span><span class="sxs-lookup"><span data-stu-id="57cc9-115">**Figure 11-11** - An example of a storage account defined in a Resource Manager template</span></span>

<span data-ttu-id="57cc9-116">Les modèles peuvent être paramétrables afin qu’un modèle puisse être réutilisé avec différents paramètres pour définir les environnements de développement, d’assurance qualité et de production.</span><span class="sxs-lookup"><span data-stu-id="57cc9-116">The templates can be parameterized so that one template can be reused with different settings to define development, QA, and production environments.</span></span> <span data-ttu-id="57cc9-117">Cela permet d’éviter les surprises lors de la migration vers un environnement plus élevé configuré différemment des environnements inférieurs.</span><span class="sxs-lookup"><span data-stu-id="57cc9-117">This helps eliminate surprises when migrating to a higher environment that is set up differently from the lower environments.</span></span> <span data-ttu-id="57cc9-118">Les ressources définies dans un modèle sont généralement toutes créées au sein d’un même groupe de ressources sur Azure (il est possible de définir plusieurs groupes de ressources dans un seul modèle de Gestionnaire des ressources, mais inhabituel).</span><span class="sxs-lookup"><span data-stu-id="57cc9-118">The resources defined in a template are typically all created within a single resource group on Azure (it's possible to define multiple resource groups in a single Resource Manager template but unusual).</span></span> <span data-ttu-id="57cc9-119">Il est ainsi très facile de supprimer un environnement en supprimant simplement le groupe de ressources dans son ensemble.</span><span class="sxs-lookup"><span data-stu-id="57cc9-119">This makes it very easy to delete an environment by just deleting the resource group as a whole.</span></span> <span data-ttu-id="57cc9-120">L’analyse des coûts peut également être exécutée au niveau du groupe de ressources, ce qui permet de connaître rapidement le coût de chaque environnement.</span><span class="sxs-lookup"><span data-stu-id="57cc9-120">Cost analysis can also be run at the resource group level, allowing for quick accounting of how much each environment is costing.</span></span>

<span data-ttu-id="57cc9-121">Il existe de nombreux exemples de modèles définis dans le projet de [modèles de démarrage rapide Azure](https://github.com/Azure/azure-quickstart-templates) sur GitHub qui vont créer un pied lorsque vous démarrez sur un nouveau modèle ou que vous l’ajoutez à un modèle existant.</span><span class="sxs-lookup"><span data-stu-id="57cc9-121">There are many example templates defined in the [Azure Quickstart Templates](https://github.com/Azure/azure-quickstart-templates) project on GitHub that will give a leg up when starting on a new template or adding to an existing one.</span></span>

<span data-ttu-id="57cc9-122">Gestionnaire des ressources modèles peuvent être exécutés de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="57cc9-122">Resource Manager templates can be run in a variety of ways.</span></span> <span data-ttu-id="57cc9-123">La méthode la plus simple consiste peut-être à les coller simplement dans le Portail Azure.</span><span class="sxs-lookup"><span data-stu-id="57cc9-123">Perhaps the simplest way is to simply paste them into the Azure portal.</span></span> <span data-ttu-id="57cc9-124">Pour les déploiements expérimentaux, cette méthode peut être très rapide.</span><span class="sxs-lookup"><span data-stu-id="57cc9-124">For experimental deployments, this method can be very quick.</span></span> <span data-ttu-id="57cc9-125">Ils peuvent également être exécutés dans le cadre d’un processus de génération ou de publication dans Azure DevOps.</span><span class="sxs-lookup"><span data-stu-id="57cc9-125">They can also be run as part of a build or release process in Azure DevOps.</span></span> <span data-ttu-id="57cc9-126">Il existe des tâches qui vont tirer parti des connexions dans Azure pour exécuter les modèles.</span><span class="sxs-lookup"><span data-stu-id="57cc9-126">There are tasks that will leverage connections into Azure to run the templates.</span></span> <span data-ttu-id="57cc9-127">Les modifications apportées aux modèles de Gestionnaire des ressources sont appliquées de façon incrémentielle, ce qui signifie que pour ajouter une nouvelle ressource, vous devez simplement l’ajouter au modèle.</span><span class="sxs-lookup"><span data-stu-id="57cc9-127">Changes to Resource Manager templates are applied incrementally, meaning that to add a new resource requires just adding it to the template.</span></span> <span data-ttu-id="57cc9-128">Les outils gèrent la comparaison entre le groupe de ressources actuel et le groupe de ressources souhaité défini dans le modèle.</span><span class="sxs-lookup"><span data-stu-id="57cc9-128">The tooling will handle diffing the current resource group with the desired resource group defined in the template.</span></span> <span data-ttu-id="57cc9-129">Les ressources seront ensuite créées ou modifiées afin qu’elles correspondent à ce qui est défini dans le modèle.</span><span class="sxs-lookup"><span data-stu-id="57cc9-129">Resources will then be created or altered so they match what is defined in the template.</span></span>  

## <a name="terraform"></a><span data-ttu-id="57cc9-130">Terraform</span><span class="sxs-lookup"><span data-stu-id="57cc9-130">Terraform</span></span>

<span data-ttu-id="57cc9-131">L’un des inconvénients des modèles Gestionnaire des ressources est qu’ils sont spécifiques au Cloud Azure.</span><span class="sxs-lookup"><span data-stu-id="57cc9-131">A perceived disadvantage of Resource Manager templates is that they are specific to the Azure cloud.</span></span> <span data-ttu-id="57cc9-132">Il est rare de créer des applications qui incluent des ressources provenant de plusieurs Clouds, mais dans les cas où l’entreprise s’appuie sur une disponibilité spectaculaire, le coût de la prise en charge de plusieurs Clouds peut être utile.</span><span class="sxs-lookup"><span data-stu-id="57cc9-132">It's unusual to create applications that include resources from more than one cloud, but in cases where the business relies on spectacular uptime, the cost of supporting multiple clouds might be worthwhile.</span></span> <span data-ttu-id="57cc9-133">Si un langage de création de modèles pouvait être utilisé dans tous les Clouds, cela permettrait également aux développeurs d’être plus portables.</span><span class="sxs-lookup"><span data-stu-id="57cc9-133">If there were one templating language that could be used across every cloud, then it would also allow for developer skills to be much more portable.</span></span>

<span data-ttu-id="57cc9-134">Il existe plusieurs technologies qui font cela !</span><span class="sxs-lookup"><span data-stu-id="57cc9-134">Several technologies exist which do just that!</span></span> <span data-ttu-id="57cc9-135">L’offre la plus mature dans cet espace est appelée [Terraform](https://www.terraform.io/).</span><span class="sxs-lookup"><span data-stu-id="57cc9-135">The most mature offering in that space is known as [Terraform](https://www.terraform.io/).</span></span> <span data-ttu-id="57cc9-136">Terraform prend en charge tous les principaux lecteurs Cloud tels qu’Azure, Google Cloud Platform, AWS et AliCloud, et prend également en charge des dizaines de joueurs mineurs tels que Heroku et DigitalOcean.</span><span class="sxs-lookup"><span data-stu-id="57cc9-136">Terraform supports every major cloud player such as Azure, Google Cloud Platform, AWS, and AliCloud, and it also supports dozens of minor players such as Heroku and DigitalOcean.</span></span> <span data-ttu-id="57cc9-137">Au lieu d’utiliser JSON comme langage de définition de modèle, il utilise le YAML légèrement plus succinct.</span><span class="sxs-lookup"><span data-stu-id="57cc9-137">Instead of using JSON as the template definition language, it uses the slightly more terse YAML.</span></span>

<span data-ttu-id="57cc9-138">Un exemple de fichier Terraform qui fait la même chose que le précédent Gestionnaire des ressources modèle (figure 11-11) est illustré dans la figure 11-12 :</span><span class="sxs-lookup"><span data-stu-id="57cc9-138">An example Terraform file that does the same as the previous Resource Manager template (Figure 11-11) is shown in Figure 11-12:</span></span>

```terraform
provider "azurerm" {
  version = "=1.28.0"
}

resource "azurerm_resource_group" "test" {
  name     = "production"
  location = "West US"
}

resource "azurerm_storage_account" "testsa" {
  name                     = "${var.storageAccountName}"
  resource_group_name      = "${azurerm_resource_group.testrg.name}"
  location                 = "${var.region}"
  account_tier             = "${var.tier}"
  account_replication_type = "${var.replicationType}"

}
```

<span data-ttu-id="57cc9-139">**Figure 11-12** -exemple de modèle de gestionnaire des ressources</span><span class="sxs-lookup"><span data-stu-id="57cc9-139">**Figure 11-12** - An example of a Resource Manager template</span></span>

<span data-ttu-id="57cc9-140">Terraform est un meilleur travail qui consiste à fournir des messages d’erreur sensibles lorsqu’une ressource ne peut pas être déployée en raison d’une erreur dans le modèle.</span><span class="sxs-lookup"><span data-stu-id="57cc9-140">Terraform does a better job of providing sensible error messages when a resource can't be deployed because of an error in the template.</span></span> <span data-ttu-id="57cc9-141">Il s’agit d’une zone dans laquelle Gestionnaire des ressources modèles présentent des défis permanents.</span><span class="sxs-lookup"><span data-stu-id="57cc9-141">This is an area where Resource Manager templates have some ongoing challenges.</span></span> <span data-ttu-id="57cc9-142">Il y a également une tâche de validation très pratique qui peut être utilisée dans la phase de génération pour intercepter les erreurs de modèle rapidement.</span><span class="sxs-lookup"><span data-stu-id="57cc9-142">There's also a very handy validate task that can be used in the build phase to catch template errors early.</span></span>

<span data-ttu-id="57cc9-143">Comme pour les modèles Gestionnaire des ressources, il existe des outils en ligne de commande qui peuvent être utilisés pour déployer des modèles Terraform.</span><span class="sxs-lookup"><span data-stu-id="57cc9-143">As with Resource Manager templates, there are command-line tools that can be used to deploy Terraform templates.</span></span> <span data-ttu-id="57cc9-144">Il existe également des tâches créées par la Communauté dans Azure Pipelines qui peuvent valider et appliquer des modèles Terraform.</span><span class="sxs-lookup"><span data-stu-id="57cc9-144">There are also community-created tasks in Azure Pipelines that can validate and apply Terraform templates.</span></span>

<span data-ttu-id="57cc9-145">Dans le cas où le modèle Terraform ou Gestionnaire des ressources génère des valeurs intéressantes telles que la chaîne de connexion à une base de données nouvellement créée, elles peuvent être capturées dans le pipeline de génération et utilisées dans les tâches suivantes.</span><span class="sxs-lookup"><span data-stu-id="57cc9-145">In the event that the Terraform or Resource Manager template outputs interesting values such as the connection string to a newly created database they can be captured in the build pipeline and used in subsequent tasks.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="57cc9-146">[Précédent](devops.md)
>[Suivant](application-bundles.md)</span><span class="sxs-lookup"><span data-stu-id="57cc9-146">[Previous](devops.md)
[Next](application-bundles.md)</span></span>
