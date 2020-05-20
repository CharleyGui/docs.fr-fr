---
title: Combinaison de conteneurs et d’approches sans serveur pour les services Cloud natifs
description: Combinaison de conteneurs et de Kubernetes avec des approches sans serveur
ms.date: 05/13/2020
ms.openlocfilehash: 67eee89659026db06eb16ef6f1154ab6935725a4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614199"
---
# <a name="combining-containers-and-serverless-approaches"></a>Combinaison de conteneurs et d’approches serverless

Les applications Cloud natives implémentent généralement des services tirant parti des conteneurs et de l’orchestration. Il existe souvent des occasions d’exposer certains services de l’application en tant que Azure Functions. Toutefois, avec une application Cloud-Native déployée sur Kubernetes, il serait intéressant de tirer parti de Azure Functions au sein de ce même ensemble d’outils. Heureusement, vous pouvez encapsuler Azure Functions à l’intérieur de conteneurs d’ancrage et les déployer à l’aide des mêmes processus et outils que le reste de votre application basée sur Kubernetes.

## <a name="when-does-it-make-sense-to-use-containers-with-serverless"></a>Quand est-il judicieux d’utiliser des conteneurs sans serveur ?

Votre fonction Azure n’a aucune connaissance de la plateforme sur laquelle elle est déployée. Pour certains scénarios, vous pouvez avoir des exigences spécifiques et devez personnaliser l’environnement d’exécution de votre code de fonction. Vous aurez besoin d’une image personnalisée qui prend en charge les dépendances ou d’une configuration non prise en charge par l’image par défaut. Dans ces cas, il est logique de déployer votre fonction dans un conteneur d’ancrage personnalisé.

## <a name="when-should-you-avoid-using-containers-with-azure-functions"></a>Quand devez-vous éviter d’utiliser des conteneurs avec Azure Functions ?

Si vous souhaitez utiliser la facturation de la consommation, vous ne pourrez pas exécuter votre fonction dans un conteneur. De plus, si vous déployez votre fonction sur un cluster Kubernetes, vous ne bénéficierez plus de la mise à l’échelle intégrée fournie par Azure Functions. Vous devez utiliser les fonctionnalités de mise à l’échelle de Kubernetes, décrites précédemment dans ce chapitre.

## <a name="how-to-combine-serverless-and-docker-containers"></a>Comment combiner des conteneurs sans serveur et des conteneurs d’ancrage

Pour inclure dans un wrapper une fonction Azure dans un conteneur d’ancrage, installez le [Azure Functions Core Tools](https://github.com/Azure/azure-functions-core-tools) puis exécutez la commande suivante :

```console
func init ProjectName --worker-runtime dotnet --docker
```

Lorsque le projet est créé, il inclut un fichier dockerfile et le runtime du Worker configurés sur `dotnet` . À présent, vous pouvez créer et tester votre fonction localement. Générez et exécutez-le à l’aide des `docker build` `docker run` commandes et. Pour obtenir des instructions détaillées pour commencer à créer des Azure Functions avec la prise en charge de l’ancrage, consultez le didacticiel [créer une fonction sur Linux à l’aide d’une image personnalisée](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image) .

## <a name="how-to-combine-serverless-and-kubernetes-with-keda"></a>Comment combiner sans serveur et Kubernetes avec KEDA

Dans ce chapitre, vous avez vu que la plateforme Azure Functions est automatiquement mise à l’échelle pour répondre à la demande. Toutefois, lorsque vous déployez des fonctions en conteneur vers AKS, vous perdez la fonctionnalité de mise à l’échelle intégrée. L’Kubernetes de la récupération est [basée sur des événements (Keda)](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda). Il permet une mise à l’échelle automatique fine pour `event-driven Kubernetes workloads,` inclure des fonctions en conteneur.

KEDA fournit une fonctionnalité de mise à l’échelle pilotée par les événements au runtime des fonctions dans un conteneur d’ancrage. KEDA peut être mis à l’échelle à partir de zéro instance (quand aucun événement ne se produit) vers `n instances` , en fonction de la charge. Il permet la mise à l’échelle automatique en exposant des métriques personnalisées à l’échelle automatique Kubernetes (la barre verticale du Pod). L’utilisation de conteneurs Functions avec KEDA permet de répliquer des fonctionnalités de fonction serverless dans n’importe quel cluster Kubernetes.

Il est à noter que le projet KEDA est désormais géré par le Cloud Native Computing Foundation (CNCF).

>[!div class="step-by-step"]
>[Précédent](leverage-serverless-functions.md) 
> [Suivant](deploy-containers-azure.md)
