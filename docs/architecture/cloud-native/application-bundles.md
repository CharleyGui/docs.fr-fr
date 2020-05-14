---
title: Bundles d’applications cloud natives
description: Architecture des applications .NET natives Cloud pour Azure | Lots d’applications Cloud natives
ms.date: 05/12/2020
ms.openlocfilehash: c16a9cba1fe31e025532ba98d644114a319bb9de
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395491"
---
# <a name="cloud-native-application-bundles"></a>Bundles d’applications cloud natives

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Une propriété clé des applications Cloud natives est qu’elles tirent parti des fonctionnalités du Cloud pour accélérer le développement. Cette conception signifie souvent qu’une application complète utilise différents types de technologies. Les applications peuvent être livrées dans des conteneurs dockers, certains services peuvent utiliser Azure Functions, tandis que d’autres parties peuvent s’exécuter directement sur des machines virtuelles allouées sur des serveurs métalliques de grande taille avec l’accélération GPU matérielle. Deux applications Cloud natives ne sont pas identiques. il est donc difficile de fournir un mécanisme unique pour les expédier.

Les conteneurs de l’ancrage peuvent s’exécuter sur Kubernetes à l’aide d’un graphique Helm pour le déploiement. Le Azure Functions peut être alloué à l’aide de modèles Terraform. Enfin, les machines virtuelles peuvent être allouées à l’aide de Terraform mais intégrées à l’aide de Ansible. Il s’agit d’un ensemble de technologies et il n’existe aucun moyen de les empaqueter dans un package raisonnable. Jusqu'à maintenant.

Les offres CNABs (Cloud application native Group) sont un effort conjoint d’un certain nombre d’entreprises à l’esprit de la Communauté, telles que Microsoft, Dockr et HashiCorp, afin de développer une spécification pour empaqueter des applications distribuées.

L’effort a été annoncé en décembre de 2018. il reste donc un peu de travail à faire pour exposer l’effort à la communauté supérieure. Toutefois, il existe déjà une [spécification ouverte](https://github.com/deislabs/cnab-spec) et une implémentation de référence appelée [marin](https://duffle.sh/). Cet outil, qui a été écrit en déplacement, est un effort conjoint entre l’organe d’accueil et Microsoft.

Les CNABs peuvent contenir différents types de technologies d’installation. Cela permet aux éléments tels que les graphiques Helm, les modèles Terraform et les règles Ansible de coexister dans le même package. Une fois générés, les packages sont autonomes et portables ; elles peuvent être installées à partir d’une clé USB.  Les packages sont signés par chiffrement pour s’assurer qu’ils proviennent du tiers qu’ils revendiquent.

Le cœur d’un CNAB est un fichier appelé `bundle.json` . Ce fichier définit le contenu du bundle, qu’il s’agisse d’images Terraform ou autres. La figure 11-9 définit un CNAB qui appelle des Terraform. Notez, cependant, qu’il définit en fait une image d’appel qui est utilisée pour appeler Terraform. Lorsqu’il est empaqueté, le fichier de l’ancrage situé dans le répertoire *CNAB* est intégré à une image de l’ancrage, qui sera inclus dans le bundle. Le fait d’avoir des Terraform installés à l’intérieur d’un conteneur de station d’accueil dans le bundle signifie que les utilisateurs n’ont pas besoin d’installer Terraform sur leur ordinateur pour exécuter le regroupement.

```json
{
    "name": "terraform",
    "version": "0.1.0",
    "schemaVersion": "v1.0.0-WD",
    "parameters": {
        "backend": {
            "type": "boolean",
            "defaultValue": false,
            "destination": {
                "env": "TF_VAR_backend"
            }
        }
    },
    "invocationImages": [
        {
        "imageType": "docker",
        "image": "cnab/terraform:latest"
        }
    ],
    "credentials": {
        "tenant_id": {
            "env": "TF_VAR_tenant_id"
        },
        "client_id": {
            "env": "TF_VAR_client_id"
        },
        "client_secret": {
            "env": "TF_VAR_client_secret"
        },
        "subscription_id": {
            "env": "TF_VAR_subscription_id"
        },
        "ssh_authorized_key": {
            "env": "TF_VAR_ssh_authorized_key"
        }
    },
    "actions": {
        "status": {
            "modifies": true
        }
    }
}
```

**Figure 10-18** : exemple de fichier Terraform

`bundle.json`Définit également un ensemble de paramètres qui sont passés dans le Terraform. Le paramétrage du Bundle permet une installation dans différents environnements.

Le format CNAB est également flexible, ce qui lui permet d’être utilisé sur n’importe quel Cloud. Il peut même être utilisé avec des solutions locales telles que [OpenStack](https://www.openstack.org/).

## <a name="devops-decisions"></a>Décisions DevOps

Il y a tellement de nombreux outils exceptionnels dans l’espace DevOps ces journées et encore plus fantastiques de livres et de documents sur la manière de mener à bien. Un livre favori pour la prise en main du parcours DevOps est [le projet Phoenix](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), qui suit la transformation d’une société fictive de NoOps en DevOps. Une chose est pour certains : DevOps n’est plus un « joli à avoir » lors du déploiement d’applications natives du Cloud. Elle est obligatoire et doit être planifiée et Resource au début de tout projet.

## <a name="references"></a>Références

- [Azure DevOps](https://azure.microsoft.com/services/devops/)
- [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/)
- [Terraform](https://www.terraform.io/)
- [Azure CLI](https://docs.microsoft.com/cli/azure/)

>[!div class="step-by-step"]
>[Précédent](infrastructure-as-code.md) 
> [Suivant](summary.md)
