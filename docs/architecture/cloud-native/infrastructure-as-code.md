---
title: Infrastructure as code
description: Adopter l’infrastructure en tant que code (IaC) avec des applications Cloud natives
ms.date: 05/13/2020
ms.openlocfilehash: d130705e19e0d3d7a9e15c73f4758a22ee8ecd43
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163737"
---
# <a name="infrastructure-as-code"></a>Infrastructure as code

Les systèmes Cloud natifs intègrent des microservices, des conteneurs et une conception de système moderne pour obtenir une vitesse et une agilité. Ils fournissent des étapes de génération et de publication automatisées pour garantir un code cohérent et de qualité. Mais ce n’est qu’une partie de l’histoire. Comment approvisionner les environnements Cloud sur lesquels ces systèmes s’exécutent ?

Les applications Cloud natives modernes adoptent la pratique d' [infrastructure en tant que code](/azure/devops/learn/what-is-infrastructure-as-code), ou `IaC` .  Avec IaC, vous automatisez l’approvisionnement de la plateforme. Vous appliquez essentiellement des pratiques de conception de logiciels, telles que le test et la gestion des versions, à vos pratiques DevOps. Votre infrastructure et vos déploiements sont automatisés, cohérents et reproductibles. Tout comme la livraison continue automatisée, le modèle traditionnel de déploiements manuels, l’infrastructure en tant que code (IaC) évolue dans le mode de gestion des environnements d’application.

Des outils comme Azure Resource Manager (ARM), Terraform et l’interface de ligne de commande (CLI) Azure vous permettent de générer un script de façon déclarative de l’infrastructure cloud dont vous avez besoin.

## <a name="azure-resource-manager-templates"></a>Modèles Microsoft Azure Resource Manager

ARM est l’acronyme de [Azure Resource Manager](/azure/azure-resource-manager/management/overview). Il s’agit d’un moteur d’approvisionnement d’API qui est intégré à Azure et exposé en tant que service API. ARM vous permet de déployer, mettre à jour, supprimer et gérer les ressources contenues dans le groupe de ressources Azure en une seule opération coordonnée. Vous fournissez au moteur un modèle JSON qui spécifie les ressources dont vous avez besoin et leur configuration. ARM orchestre automatiquement le déploiement dans le bon ordre respectant les dépendances. Le moteur garantit idempotence. Si une ressource souhaitée existe déjà avec la même configuration, l’approvisionnement sera ignoré.

Les modèles Azure Resource Manager sont un langage JSON qui vous aide à définir diverses ressources dans Azure. Le schéma de base ressemble à ce qui suit : figure 10-14.

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

**Figure 10-14** -schéma d’un modèle de gestionnaire des ressources

Dans ce modèle, il est possible de définir un conteneur de stockage à l’intérieur de la section des ressources, comme suit :

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

**Figure 10-15** : exemple de compte de stockage défini dans un modèle de gestionnaire des ressources

Un modèle ARM peut être paramétré avec des informations de configuration et d’environnement dynamiques. Cela lui permet d’être réutilisé pour définir différents environnements, tels que le développement, l’assurance qualité ou la production. Normalement, le modèle crée toutes les ressources dans un seul groupe de ressources Azure. Il est possible de définir plusieurs groupes de ressources dans un seul modèle de Gestionnaire des ressources, si nécessaire. Vous pouvez supprimer toutes les ressources d’un environnement en supprimant le groupe de ressources lui-même. L’analyse des coûts peut également être exécutée au niveau du groupe de ressources, ce qui permet de connaître rapidement le coût de chaque environnement.

Un grand nombre d’exemples ou de modèles ARM sont disponibles dans le projet de [modèles de démarrage rapide Azure](https://github.com/Azure/azure-quickstart-templates) sur GitHub. Ils peuvent accélérer la création d’un nouveau modèle ou la modification d’un modèle existant.

Gestionnaire des ressources modèles peuvent être exécutés de nombreuses façons. La méthode la plus simple consiste peut-être à les coller simplement dans le Portail Azure. Pour les déploiements expérimentaux, cette méthode peut être rapide. Ils peuvent également être exécutés dans le cadre d’un processus de génération ou de publication dans Azure DevOps. Il existe des tâches qui vont tirer parti des connexions dans Azure pour exécuter les modèles. Les modifications apportées aux modèles de Gestionnaire des ressources sont appliquées de façon incrémentielle, ce qui signifie que pour ajouter une nouvelle ressource, vous devez simplement l’ajouter au modèle. Les outils rapprochent les différences entre les ressources actuelles et celles définies dans le modèle. Les ressources seront ensuite créées ou modifiées afin qu’elles correspondent à ce qui est défini dans le modèle.  

## <a name="terraform"></a>Terraform

Les applications Cloud natives sont souvent construites pour être `cloud agnostic` . Par conséquent, l’application n’est pas étroitement couplée à un fournisseur de Cloud particulier et peut être déployée sur n’importe quel cloud public.

[Terraform](https://www.terraform.io/) est un outil de création de modèles commercial qui peut approvisionner des applications Cloud natives sur tous les principaux acteurs du Cloud : Azure, Google Cloud Platform, AWS et AliCloud. Au lieu d’utiliser JSON comme langage de définition de modèle, il utilise le YAML légèrement plus succinct.

Un exemple de fichier Terraform qui fait la même chose que le précédent Gestionnaire des ressources modèle (figure 10-15) est illustré dans la figure 10-16 :

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

**Figure 10-16** -exemple de modèle de gestionnaire des ressources

Terraform fournit également des messages d’erreur intuitifs pour les modèles de problème. Il y a également une tâche de validation pratique qui peut être utilisée dans la phase de génération pour intercepter les erreurs de modèle plus tôt.

Comme pour les modèles Gestionnaire des ressources, les outils en ligne de commande sont disponibles pour déployer des modèles Terraform. Il existe également des tâches créées par la Communauté dans Azure Pipelines qui peuvent valider et appliquer des modèles Terraform.

Parfois, les modèles Terraform et ARM génèrent des valeurs significatives, telles qu’une chaîne de connexion à une base de données nouvellement créée. Ces informations peuvent être capturées dans le pipeline de build et utilisées dans les tâches suivantes.

## <a name="azure-cli-scripts-and-tasks"></a>Azure CLI des scripts et des tâches

Enfin, vous pouvez tirer parti de [Azure CLI](/cli/azure/) pour générer un script de façon déclarative de votre infrastructure en nuage. Azure CLI scripts peuvent être créés, trouvés et partagés pour approvisionner et configurer presque n’importe quelle ressource Azure. L’interface CLI est simple à utiliser avec une courbe d’apprentissage doucement. Les scripts sont exécutés dans PowerShell ou bash. Ils sont également faciles à déboguer, en particulier en cas de comparaison avec les modèles ARM.

Azure CLI scripts fonctionnent bien lorsque vous devez détruire et redéployer votre infrastructure. La mise à jour d’un environnement existant peut être délicate. De nombreuses commandes CLI ne sont pas idempotent. Cela signifie qu’ils recréent la ressource chaque fois qu’ils sont exécutés, même si la ressource existe déjà. Il est toujours possible d’ajouter du code qui vérifie l’existence de chaque ressource avant de la créer. Toutefois, votre script peut devenir encombré et difficile à gérer.

Ces scripts peuvent également être incorporés dans les pipelines Azure DevOps en tant que `Azure CLI tasks` . L’exécution du pipeline appelle le script.

La figure 10-17 montre un extrait de code YAML qui répertorie la version de Azure CLI et les détails de l’abonnement. Notez comment Azure CLI commandes sont incluses dans un script inline.

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

**Figure 10-17** -script Azure CLI

Dans l’article [qu’est-ce que l’infrastructure en tant que code](/azure/devops/learn/what-is-infrastructure-as-code), l’auteur Sam Guckenheimer décrit comment, les équipes qui implémentent IaC peuvent fournir rapidement et à grande échelle des environnements stables. Les équipes évitent la configuration manuelle des environnements et appliquent la cohérence en représentant l’état souhaité de leurs environnements via du code. Les déploiements d’infrastructure avec IaC sont reproductibles et évitent les problèmes d’exécution dus à une dérive de la configuration ou à des dépendances manquantes. Les équipes DevOps peuvent collaborer avec un ensemble unifié de pratiques et d’outils pour fournir des applications et leur infrastructure de prise en charge rapidement, de manière fiable et à grande échelle.»

>[!div class="step-by-step"]
>[Précédent](feature-flags.md) 
> [Suivant](application-bundles.md)
