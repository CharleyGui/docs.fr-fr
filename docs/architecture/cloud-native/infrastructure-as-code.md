---
title: Infrastructure en tant que code
description: Architecture des applications .NET natives Cloud pour Azure | Infrastructure en tant que code
ms.date: 06/30/2019
ms.openlocfilehash: e395db28bdeff785251b91ed643f9920873d26e8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183013"
---
# <a name="infrastructure-as-code"></a>Infrastructure en tant que code

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Les applications Cloud natives ont tendance à utiliser toutes sortes de composants PaaS (Platform as a service) fantastiques. Sur une plateforme Cloud comme Azure, ces composants peuvent inclure des éléments tels que le stockage, les Service Bus et le service Signalr. À mesure que les applications deviennent plus compliquées, le nombre de ces services en cours d’utilisation est susceptible de croître. À l’instar de la façon dont la livraison continue a enfreint le modèle traditionnel de déploiement dans un environnement manuellement, le rythme de modification rapide a également enfreint le modèle de gestion des environnements par un groupe informatique centralisé.

Les environnements de construction peuvent et doivent également être automatisés. Il existe un large éventail d’outils bien pensés qui peuvent faciliter le processus.

## <a name="azure-resource-manager-templates"></a>Modèles de Azure Resource Manager

Les modèles Azure Resource Manager sont un langage JSON qui vous aide à définir diverses ressources dans Azure. Le schéma de base ressemble à ce qui suit : figure 11-10.

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

**Figure 11-10** -schéma d’un modèle de gestionnaire des ressources

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

**Figure 11-11** : exemple de compte de stockage défini dans un modèle de gestionnaire des ressources

Les modèles peuvent être paramétrables afin qu’un modèle puisse être réutilisé avec différents paramètres pour définir les environnements de développement, d’assurance qualité et de production. Cela permet d’éviter les surprises lors de la migration vers un environnement plus élevé configuré différemment des environnements inférieurs. Les ressources définies dans un modèle sont généralement toutes créées au sein d’un même groupe de ressources sur Azure (il est possible de définir plusieurs groupes de ressources dans un seul modèle de Gestionnaire des ressources, mais inhabituel). Il est ainsi très facile de supprimer un environnement en supprimant simplement le groupe de ressources dans son ensemble. L’analyse des coûts peut également être exécutée au niveau du groupe de ressources, ce qui permet de connaître rapidement le coût de chaque environnement.

Il existe de nombreux exemples de modèles définis dans le projet de [modèles de démarrage rapide Azure](https://github.com/Azure/azure-quickstart-templates) sur GitHub qui vont créer un pied lorsque vous démarrez sur un nouveau modèle ou que vous l’ajoutez à un modèle existant.

Gestionnaire des ressources modèles peuvent être exécutés de différentes façons. La méthode la plus simple consiste peut-être à les coller simplement dans le Portail Azure. Pour les déploiements expérimentaux, cette méthode peut être très rapide. Ils peuvent également être exécutés dans le cadre d’un processus de génération ou de publication dans Azure DevOps. Il existe des tâches qui vont tirer parti des connexions dans Azure pour exécuter les modèles. Les modifications apportées aux modèles de Gestionnaire des ressources sont appliquées de façon incrémentielle, ce qui signifie que pour ajouter une nouvelle ressource, vous devez simplement l’ajouter au modèle. Les outils gèrent la comparaison entre le groupe de ressources actuel et le groupe de ressources souhaité défini dans le modèle. Les ressources seront ensuite créées ou modifiées afin qu’elles correspondent à ce qui est défini dans le modèle.  

## <a name="terraform"></a>Terraform

L’un des inconvénients des modèles Gestionnaire des ressources est qu’ils sont spécifiques au Cloud Azure. Il est rare de créer des applications qui incluent des ressources provenant de plusieurs Clouds, mais dans les cas où l’entreprise s’appuie sur une disponibilité spectaculaire, le coût de la prise en charge de plusieurs Clouds peut être utile. Si un langage de création de modèles pouvait être utilisé dans tous les Clouds, cela permettrait également aux développeurs d’être plus portables.

Il existe plusieurs technologies qui font cela ! L’offre la plus mature dans cet espace est appelée [Terraform](https://www.terraform.io/). Terraform prend en charge tous les principaux lecteurs Cloud tels qu’Azure, Google Cloud Platform, AWS et AliCloud, et prend également en charge des dizaines de joueurs mineurs tels que Heroku et DigitalOcean. Au lieu d’utiliser JSON comme langage de définition de modèle, il utilise le YAML légèrement plus succinct. 

Un exemple de fichier Terraform qui fait la même chose que le précédent Gestionnaire des ressources modèle (figure 11-11) est illustré dans la figure 11-12 :

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

**Figure 11-12** -exemple de modèle de gestionnaire des ressources

Terraform est un meilleur travail qui consiste à fournir des messages d’erreur sensibles lorsqu’une ressource ne peut pas être déployée en raison d’une erreur dans le modèle. Il s’agit d’une zone dans laquelle Gestionnaire des ressources modèles présentent des défis permanents. Il y a également une tâche de validation très pratique qui peut être utilisée dans la phase de génération pour intercepter les erreurs de modèle rapidement.

Comme pour les modèles Gestionnaire des ressources, il existe des outils en ligne de commande qui peuvent être utilisés pour déployer des modèles Terraform. Il existe également des tâches créées par la Communauté dans Azure Pipelines qui peuvent valider et appliquer des modèles Terraform.

Dans le cas où le modèle Terraform ou Gestionnaire des ressources génère des valeurs intéressantes telles que la chaîne de connexion à une base de données nouvellement créée, elles peuvent être capturées dans le pipeline de génération et utilisées dans les tâches suivantes.

>[!div class="step-by-step"]
>[Précédent](devops.md)
>[Suivant](application-bundles.md)
