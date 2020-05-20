---
title: Infrastructure as code
description: Adopter l’infrastructure en tant que code (IaC) avec des applications Cloud natives
ms.date: 05/13/2020
ms.openlocfilehash: cfc9e1f0b2733048d5921de5a0400998c282b1fa
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613952"
---
# <a name="infrastructure-as-code"></a><span data-ttu-id="e0c10-103">Infrastructure as code</span><span class="sxs-lookup"><span data-stu-id="e0c10-103">Infrastructure as code</span></span>

<span data-ttu-id="e0c10-104">Les systèmes Cloud natifs intègrent des microservices, des conteneurs et une conception de système moderne pour obtenir une vitesse et une agilité.</span><span class="sxs-lookup"><span data-stu-id="e0c10-104">Cloud-native systems embrace microservices, containers, and modern system design to achieve speed and agility.</span></span> <span data-ttu-id="e0c10-105">Ils fournissent des étapes de génération et de publication automatisées pour garantir un code cohérent et de qualité.</span><span class="sxs-lookup"><span data-stu-id="e0c10-105">They provide automated build and release stages to ensure consistent and quality code.</span></span> <span data-ttu-id="e0c10-106">Mais ce n’est qu’une partie de l’histoire.</span><span class="sxs-lookup"><span data-stu-id="e0c10-106">But, that's only part of the story.</span></span> <span data-ttu-id="e0c10-107">Comment approvisionner les environnements Cloud sur lesquels ces systèmes s’exécutent ?</span><span class="sxs-lookup"><span data-stu-id="e0c10-107">How do you provision the cloud environments upon which these systems run?</span></span>

<span data-ttu-id="e0c10-108">Les applications Cloud natives modernes adoptent la pratique d' [infrastructure en tant que code](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), ou `IaC` .</span><span class="sxs-lookup"><span data-stu-id="e0c10-108">Modern cloud-native applications embrace the widely accepted practice of [Infrastructure as Code](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), or `IaC`.</span></span>  <span data-ttu-id="e0c10-109">Avec IaC, vous automatisez l’approvisionnement de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="e0c10-109">With IaC, you automate platform provisioning.</span></span> <span data-ttu-id="e0c10-110">Vous appliquez essentiellement des pratiques de conception de logiciels, telles que le test et la gestion des versions, à vos pratiques DevOps.</span><span class="sxs-lookup"><span data-stu-id="e0c10-110">You essentially apply software engineering practices such as testing and versioning to your DevOps practices.</span></span> <span data-ttu-id="e0c10-111">Votre infrastructure et vos déploiements sont automatisés, cohérents et reproductibles.</span><span class="sxs-lookup"><span data-stu-id="e0c10-111">Your infrastructure and deployments are automated, consistent, and repeatable.</span></span> <span data-ttu-id="e0c10-112">Tout comme la livraison continue automatisée, le modèle traditionnel de déploiements manuels, l’infrastructure en tant que code (IaC) évolue dans le mode de gestion des environnements d’application.</span><span class="sxs-lookup"><span data-stu-id="e0c10-112">Just as continuous delivery automated the traditional model of manual deployments, Infrastructure as Code (IaC) is evolving how application environments are managed.</span></span>

<span data-ttu-id="e0c10-113">Des outils comme Azure Resource Manager (ARM), Terraform et l’interface de ligne de commande (CLI) Azure vous permettent de générer un script de façon déclarative de l’infrastructure cloud dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="e0c10-113">Tools like Azure Resource Manager (ARM), Terraform, and the Azure Command Line Interface (CLI) enable you to declaratively script the cloud infrastructure you require.</span></span>

## <a name="azure-resource-manager-templates"></a><span data-ttu-id="e0c10-114">Modèles Microsoft Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="e0c10-114">Azure Resource Manager templates</span></span>

<span data-ttu-id="e0c10-115">ARM est l’acronyme de [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/).</span><span class="sxs-lookup"><span data-stu-id="e0c10-115">ARM stands for [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/).</span></span> <span data-ttu-id="e0c10-116">Il s’agit d’un moteur d’approvisionnement d’API qui est intégré à Azure et exposé en tant que service API.</span><span class="sxs-lookup"><span data-stu-id="e0c10-116">It's an API provisioning engine that is built into Azure and exposed as an API service.</span></span> <span data-ttu-id="e0c10-117">ARM vous permet de déployer, mettre à jour, supprimer et gérer les ressources contenues dans le groupe de ressources Azure en une seule opération coordonnée.</span><span class="sxs-lookup"><span data-stu-id="e0c10-117">ARM enables you to deploy, update, delete, and manage the resources contained in Azure resource group in a single, coordinated operation.</span></span> <span data-ttu-id="e0c10-118">Vous fournissez au moteur un modèle JSON qui spécifie les ressources dont vous avez besoin et leur configuration.</span><span class="sxs-lookup"><span data-stu-id="e0c10-118">You provide the engine with a JSON-based template that specifies the resources you require and their configuration.</span></span> <span data-ttu-id="e0c10-119">ARM orchestre automatiquement le déploiement dans le bon ordre respectant les dépendances.</span><span class="sxs-lookup"><span data-stu-id="e0c10-119">ARM automatically orchestrates the deployment in the correct order respecting dependencies.</span></span> <span data-ttu-id="e0c10-120">Le moteur garantit idempotence.</span><span class="sxs-lookup"><span data-stu-id="e0c10-120">The engine ensures idempotency.</span></span> <span data-ttu-id="e0c10-121">Si une ressource souhaitée existe déjà avec la même configuration, l’approvisionnement sera ignoré.</span><span class="sxs-lookup"><span data-stu-id="e0c10-121">If a desired resource already exists with the same configuration, provisioning will be ignored.</span></span>

<span data-ttu-id="e0c10-122">Les modèles Azure Resource Manager sont un langage JSON qui vous aide à définir diverses ressources dans Azure.</span><span class="sxs-lookup"><span data-stu-id="e0c10-122">Azure Resource Manager templates are a JSON-based language for defining various resources in Azure.</span></span> <span data-ttu-id="e0c10-123">Le schéma de base ressemble à ce qui suit : figure 10-14.</span><span class="sxs-lookup"><span data-stu-id="e0c10-123">The basic schema looks something like Figure 10-14.</span></span>

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

<span data-ttu-id="e0c10-124">**Figure 10-14** -schéma d’un modèle de gestionnaire des ressources</span><span class="sxs-lookup"><span data-stu-id="e0c10-124">**Figure 10-14** - The schema for a Resource Manager template</span></span>

<span data-ttu-id="e0c10-125">Dans ce modèle, il est possible de définir un conteneur de stockage à l’intérieur de la section des ressources, comme suit :</span><span class="sxs-lookup"><span data-stu-id="e0c10-125">Within this template, one might define a storage container inside the resources section like so:</span></span>

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

<span data-ttu-id="e0c10-126">**Figure 10-15** : exemple de compte de stockage défini dans un modèle de gestionnaire des ressources</span><span class="sxs-lookup"><span data-stu-id="e0c10-126">**Figure 10-15** - An example of a storage account defined in a Resource Manager template</span></span>

<span data-ttu-id="e0c10-127">Un modèle ARM peut être paramétré avec des informations de configuration et d’environnement dynamiques.</span><span class="sxs-lookup"><span data-stu-id="e0c10-127">An ARM template can be parameterized with dynamic environment and configuration information.</span></span> <span data-ttu-id="e0c10-128">Cela lui permet d’être réutilisé pour définir différents environnements, tels que le développement, l’assurance qualité ou la production.</span><span class="sxs-lookup"><span data-stu-id="e0c10-128">Doing so enables it to be reused to define different environments, such as development, QA, or production.</span></span> <span data-ttu-id="e0c10-129">Normalement, le modèle crée toutes les ressources dans un seul groupe de ressources Azure.</span><span class="sxs-lookup"><span data-stu-id="e0c10-129">Normally, the template creates all resources within a single Azure resource group.</span></span> <span data-ttu-id="e0c10-130">Il est possible de définir plusieurs groupes de ressources dans un seul modèle de Gestionnaire des ressources, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e0c10-130">It's possible to define multiple resource groups in a single Resource Manager template, if needed.</span></span> <span data-ttu-id="e0c10-131">Vous pouvez supprimer toutes les ressources d’un environnement en supprimant le groupe de ressources lui-même.</span><span class="sxs-lookup"><span data-stu-id="e0c10-131">You can delete all resources in an environment by deleting the resource group itself.</span></span> <span data-ttu-id="e0c10-132">L’analyse des coûts peut également être exécutée au niveau du groupe de ressources, ce qui permet de connaître rapidement le coût de chaque environnement.</span><span class="sxs-lookup"><span data-stu-id="e0c10-132">Cost analysis can also be run at the resource group level, allowing for quick accounting of how much each environment is costing.</span></span>

<span data-ttu-id="e0c10-133">Un grand nombre d’exemples ou de modèles ARM sont disponibles dans le projet de [modèles de démarrage rapide Azure](https://github.com/Azure/azure-quickstart-templates) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="e0c10-133">There are many examples or ARM templates available in the [Azure Quickstart Templates](https://github.com/Azure/azure-quickstart-templates) project on GitHub.</span></span> <span data-ttu-id="e0c10-134">Ils peuvent accélérer la création d’un nouveau modèle ou la modification d’un modèle existant.</span><span class="sxs-lookup"><span data-stu-id="e0c10-134">They can help accelerate creating a new template or modifying an existing one.</span></span>

<span data-ttu-id="e0c10-135">Gestionnaire des ressources modèles peuvent être exécutés de nombreuses façons.</span><span class="sxs-lookup"><span data-stu-id="e0c10-135">Resource Manager templates can be run in many of ways.</span></span> <span data-ttu-id="e0c10-136">La méthode la plus simple consiste peut-être à les coller simplement dans le Portail Azure.</span><span class="sxs-lookup"><span data-stu-id="e0c10-136">Perhaps the simplest way is to simply paste them into the Azure portal.</span></span> <span data-ttu-id="e0c10-137">Pour les déploiements expérimentaux, cette méthode peut être rapide.</span><span class="sxs-lookup"><span data-stu-id="e0c10-137">For experimental deployments, this method can be quick.</span></span> <span data-ttu-id="e0c10-138">Ils peuvent également être exécutés dans le cadre d’un processus de génération ou de publication dans Azure DevOps.</span><span class="sxs-lookup"><span data-stu-id="e0c10-138">They can also be run as part of a build or release process in Azure DevOps.</span></span> <span data-ttu-id="e0c10-139">Il existe des tâches qui vont tirer parti des connexions dans Azure pour exécuter les modèles.</span><span class="sxs-lookup"><span data-stu-id="e0c10-139">There are tasks that will leverage connections into Azure to run the templates.</span></span> <span data-ttu-id="e0c10-140">Les modifications apportées aux modèles de Gestionnaire des ressources sont appliquées de façon incrémentielle, ce qui signifie que pour ajouter une nouvelle ressource, vous devez simplement l’ajouter au modèle.</span><span class="sxs-lookup"><span data-stu-id="e0c10-140">Changes to Resource Manager templates are applied incrementally, meaning that to add a new resource requires just adding it to the template.</span></span> <span data-ttu-id="e0c10-141">Les outils rapprochent les différences entre les ressources actuelles et celles définies dans le modèle.</span><span class="sxs-lookup"><span data-stu-id="e0c10-141">The tooling will reconcile differences between the current resources and those defined in the template.</span></span> <span data-ttu-id="e0c10-142">Les ressources seront ensuite créées ou modifiées afin qu’elles correspondent à ce qui est défini dans le modèle.</span><span class="sxs-lookup"><span data-stu-id="e0c10-142">Resources will then be created or altered so they match what is defined in the template.</span></span>  

## <a name="terraform"></a><span data-ttu-id="e0c10-143">Terraform</span><span class="sxs-lookup"><span data-stu-id="e0c10-143">Terraform</span></span>

<span data-ttu-id="e0c10-144">Les applications Cloud natives sont souvent construites pour être `cloud agnostic` .</span><span class="sxs-lookup"><span data-stu-id="e0c10-144">Cloud-native applications are often constructed to be `cloud agnostic`.</span></span> <span data-ttu-id="e0c10-145">Par conséquent, l’application n’est pas étroitement couplée à un fournisseur de Cloud particulier et peut être déployée sur n’importe quel cloud public.</span><span class="sxs-lookup"><span data-stu-id="e0c10-145">Being so means the application isn't tightly coupled to a particular cloud vendor and can be deployed to any public cloud.</span></span>

<span data-ttu-id="e0c10-146">[Terraform](https://www.terraform.io/) est un outil de création de modèles commercial qui peut approvisionner des applications Cloud natives sur tous les principaux acteurs du Cloud : Azure, Google Cloud Platform, AWS et AliCloud.</span><span class="sxs-lookup"><span data-stu-id="e0c10-146">[Terraform](https://www.terraform.io/) is commercial templating tool that can provision cloud-native applications across all the major cloud players: Azure, Google Cloud Platform, AWS, and AliCloud.</span></span> <span data-ttu-id="e0c10-147">Au lieu d’utiliser JSON comme langage de définition de modèle, il utilise le YAML légèrement plus succinct.</span><span class="sxs-lookup"><span data-stu-id="e0c10-147">Instead of using JSON as the template definition language, it uses the slightly more terse YAML.</span></span>

<span data-ttu-id="e0c10-148">Un exemple de fichier Terraform qui fait la même chose que le précédent Gestionnaire des ressources modèle (figure 10-15) est illustré dans la figure 10-16 :</span><span class="sxs-lookup"><span data-stu-id="e0c10-148">An example Terraform file that does the same as the previous Resource Manager template (Figure 10-15) is shown in Figure 10-16:</span></span>

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

<span data-ttu-id="e0c10-149">**Figure 10-16** -exemple de modèle de gestionnaire des ressources</span><span class="sxs-lookup"><span data-stu-id="e0c10-149">**Figure 10-16** - An example of a Resource Manager template</span></span>

<span data-ttu-id="e0c10-150">Terraform fournit également des messages d’erreur intuitifs pour les modèles de problème.</span><span class="sxs-lookup"><span data-stu-id="e0c10-150">Terraform also provides intuitive error messages for problem templates.</span></span> <span data-ttu-id="e0c10-151">Il y a également une tâche de validation pratique qui peut être utilisée dans la phase de génération pour intercepter les erreurs de modèle plus tôt.</span><span class="sxs-lookup"><span data-stu-id="e0c10-151">There's also a handy validate task that can be used in the build phase to catch template errors early.</span></span>

<span data-ttu-id="e0c10-152">Comme pour les modèles Gestionnaire des ressources, les outils en ligne de commande sont disponibles pour déployer des modèles Terraform.</span><span class="sxs-lookup"><span data-stu-id="e0c10-152">As with Resource Manager templates, command-line tools are available to deploy Terraform templates.</span></span> <span data-ttu-id="e0c10-153">Il existe également des tâches créées par la Communauté dans Azure Pipelines qui peuvent valider et appliquer des modèles Terraform.</span><span class="sxs-lookup"><span data-stu-id="e0c10-153">There are also community-created tasks in Azure Pipelines that can validate and apply Terraform templates.</span></span>

<span data-ttu-id="e0c10-154">Parfois, les modèles Terraform et ARM génèrent des valeurs significatives, telles qu’une chaîne de connexion à une base de données nouvellement créée.</span><span class="sxs-lookup"><span data-stu-id="e0c10-154">Sometimes Terraform and ARM templates output meaningful values, such as a connection string to a newly created database.</span></span> <span data-ttu-id="e0c10-155">Ces informations peuvent être capturées dans le pipeline de build et utilisées dans les tâches suivantes.</span><span class="sxs-lookup"><span data-stu-id="e0c10-155">This information can be captured in the build pipeline and used in subsequent tasks.</span></span>

## <a name="azure-cli-scripts-and-tasks"></a><span data-ttu-id="e0c10-156">Azure CLI des scripts et des tâches</span><span class="sxs-lookup"><span data-stu-id="e0c10-156">Azure CLI Scripts and Tasks</span></span>

<span data-ttu-id="e0c10-157">Enfin, vous pouvez tirer parti de [Azure CLI](https://docs.microsoft.com/cli/azure/) pour générer un script de façon déclarative de votre infrastructure en nuage.</span><span class="sxs-lookup"><span data-stu-id="e0c10-157">Finally, you can leverage [Azure CLI](https://docs.microsoft.com/cli/azure/) to declaratively script your cloud infrastructure.</span></span> <span data-ttu-id="e0c10-158">Azure CLI scripts peuvent être créés, trouvés et partagés pour approvisionner et configurer presque n’importe quelle ressource Azure.</span><span class="sxs-lookup"><span data-stu-id="e0c10-158">Azure CLI scripts can be created, found, and shared to provision and configure almost any Azure resource.</span></span> <span data-ttu-id="e0c10-159">L’interface CLI est simple à utiliser avec une courbe d’apprentissage doucement.</span><span class="sxs-lookup"><span data-stu-id="e0c10-159">The CLI is simple to use with a gentle learning curve.</span></span> <span data-ttu-id="e0c10-160">Les scripts sont exécutés dans PowerShell ou bash.</span><span class="sxs-lookup"><span data-stu-id="e0c10-160">Scripts are executed within either PowerShell or Bash.</span></span> <span data-ttu-id="e0c10-161">Ils sont également faciles à déboguer, en particulier en cas de comparaison avec les modèles ARM.</span><span class="sxs-lookup"><span data-stu-id="e0c10-161">They're also straightforward to debug, especially when compared with ARM templates.</span></span>

<span data-ttu-id="e0c10-162">Azure CLI scripts fonctionnent bien lorsque vous devez détruire et redéployer votre infrastructure.</span><span class="sxs-lookup"><span data-stu-id="e0c10-162">Azure CLI scripts work well when you need to tear down and redeploy your infrastructure.</span></span> <span data-ttu-id="e0c10-163">La mise à jour d’un environnement existant peut être délicate.</span><span class="sxs-lookup"><span data-stu-id="e0c10-163">Updating an existing environment can be tricky.</span></span> <span data-ttu-id="e0c10-164">De nombreuses commandes CLI ne sont pas idempotent.</span><span class="sxs-lookup"><span data-stu-id="e0c10-164">Many CLI commands aren't idempotent.</span></span> <span data-ttu-id="e0c10-165">Cela signifie qu’ils recréent la ressource chaque fois qu’ils sont exécutés, même si la ressource existe déjà.</span><span class="sxs-lookup"><span data-stu-id="e0c10-165">That means they'll recreate the resource each time they're run, even if the resource already exists.</span></span> <span data-ttu-id="e0c10-166">Il est toujours possible d’ajouter du code qui vérifie l’existence de chaque ressource avant de la créer.</span><span class="sxs-lookup"><span data-stu-id="e0c10-166">It's always possible to add code that checks for the existence of each resource before creating it.</span></span> <span data-ttu-id="e0c10-167">Toutefois, votre script peut devenir encombré et difficile à gérer.</span><span class="sxs-lookup"><span data-stu-id="e0c10-167">But, doing so, your script can become bloated and difficult to manage.</span></span>

<span data-ttu-id="e0c10-168">Ces scripts peuvent également être incorporés dans les pipelines Azure DevOps en tant que `Azure CLI tasks` .</span><span class="sxs-lookup"><span data-stu-id="e0c10-168">These scripts can also be embedded in Azure DevOps pipelines as `Azure CLI tasks`.</span></span> <span data-ttu-id="e0c10-169">L’exécution du pipeline appelle le script.</span><span class="sxs-lookup"><span data-stu-id="e0c10-169">Executing the pipeline invokes the script.</span></span>

<span data-ttu-id="e0c10-170">La figure 10-17 montre un extrait de code YAML qui répertorie la version de Azure CLI et les détails de l’abonnement.</span><span class="sxs-lookup"><span data-stu-id="e0c10-170">Figure 10-17 shows a YAML snippet that lists the version of Azure CLI and the details of the subscription.</span></span> <span data-ttu-id="e0c10-171">Notez comment Azure CLI commandes sont incluses dans un script inline.</span><span class="sxs-lookup"><span data-stu-id="e0c10-171">Note how Azure CLI commands are included in an inline script.</span></span>

```yaml
- task: AzureCLI@2
  displayName: Azure CLI
  inputs:
    azureSubscription: <Name of the Azure Resource Manager service connection>
    scriptType: ps
    scriptLocation: inlineScript
    inlineScript: |
      az --version
      az account show
```

<span data-ttu-id="e0c10-172">**Figure 10-17** -script Azure CLI</span><span class="sxs-lookup"><span data-stu-id="e0c10-172">**Figure 10-17** - Azure CLI script</span></span>

<span data-ttu-id="e0c10-173">Dans l’article [qu’est-ce que l’infrastructure en tant que code](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), l’auteur Sam Guckenheimer décrit comment, les équipes qui implémentent IaC peuvent fournir rapidement et à grande échelle des environnements stables.</span><span class="sxs-lookup"><span data-stu-id="e0c10-173">In the article, [What is Infrastructure as Code](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), Author Sam Guckenheimer describes how, "Teams who implement IaC can deliver stable environments rapidly and at scale.</span></span> <span data-ttu-id="e0c10-174">Les équipes évitent la configuration manuelle des environnements et appliquent la cohérence en représentant l’état souhaité de leurs environnements via du code.</span><span class="sxs-lookup"><span data-stu-id="e0c10-174">Teams avoid manual configuration of environments and enforce consistency by representing the desired state of their environments via code.</span></span> <span data-ttu-id="e0c10-175">Les déploiements d’infrastructure avec IaC sont reproductibles et évitent les problèmes d’exécution dus à une dérive de la configuration ou à des dépendances manquantes.</span><span class="sxs-lookup"><span data-stu-id="e0c10-175">Infrastructure deployments with IaC are repeatable and prevent runtime issues caused by configuration drift or missing dependencies.</span></span> <span data-ttu-id="e0c10-176">Les équipes DevOps peuvent collaborer avec un ensemble unifié de pratiques et d’outils pour fournir des applications et leur infrastructure de prise en charge rapidement, de manière fiable et à grande échelle.»</span><span class="sxs-lookup"><span data-stu-id="e0c10-176">DevOps teams can work together with a unified set of practices and tools to deliver applications and their supporting infrastructure rapidly, reliably, and at scale."</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e0c10-177">[Précédent](feature-flags.md) 
> [Suivant](application-bundles.md)</span><span class="sxs-lookup"><span data-stu-id="e0c10-177">[Previous](feature-flags.md)
[Next](application-bundles.md)</span></span>
