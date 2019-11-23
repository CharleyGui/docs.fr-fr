---
title: Combinaison de conteneurs et d’approches serverless
description: Combinaison de conteneurs et de Kubernetes avec des approches sans serveur
ms.date: 06/30/2019
ms.openlocfilehash: 58aff43adbdd2e629370cc685f32c7b61c25f85e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183433"
---
# <a name="combining-containers-and-serverless-approaches"></a>Combinaison de conteneurs et d’approches serverless

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Souvent, les applications basées sur des microservices s’appuient fortement sur les conteneurs, l’orchestration et le transfert de messages pour la communication entre les nœuds. Cette messagerie est une tâche idéale pour Azure Functions, mais avec le reste de l’application configurée et déployée à l’aide de Kubernetes et des outils associés, il serait agréable de pouvoir tirer parti des Azure Functions au sein de ce même ensemble d’outils. Heureusement, vous pouvez encapsuler Azure Functions dans des conteneurs d’ancrage et les déployer en utilisant les mêmes processus et outils que le reste de votre application basée sur Kubernetes.

## <a name="when-does-it-make-sense-to-use-containers-with-serverless"></a>Quand est-il judicieux d’utiliser des conteneurs sans serveur ?

Par défaut, vos fonctions sans serveur n’ont aucune connaissance de la plateforme sur laquelle elles s’exécuteront. Toutefois, dans certains cas, vous pouvez avoir des exigences spécifiques qui vous permettent de personnaliser l’image conteneur dans laquelle votre code s’exécutera. Vous pouvez utiliser une image personnalisée, car votre fonction s’appuie sur une version de langage spécifique ou présente des dépendances ou des exigences de configuration qui ne sont pas prises en charge par l’image par défaut. Dans ces cas, il peut être judicieux de personnaliser votre propre conteneur et de déployer votre fonction dans un conteneur d’ancrage personnalisé.

## <a name="when-should-you-avoid-using-containers-with-azure-functions"></a>Quand devez-vous éviter d’utiliser des conteneurs avec Azure Functions ?

Si vous vous attendez à bénéficier de la facturation du plan de consommation pour votre fonction, vous ne pourrez pas le faire si vous utilisez votre propre conteneur. En outre, si vous allez au-delà de l’utilisation d’un conteneur d’ancrage et que vous déployez vos fonctions sur votre propre cluster Kubernetes, vous ne bénéficierez plus de la mise à l’échelle intégrée fournie par Azure Functions. Vous devez utiliser les fonctionnalités de mise à l’échelle de Kubernetes, décrites ci-dessous.

## <a name="how-to-combine-serverless-and-docker-containers"></a>Comment combiner des conteneurs sans serveur et des conteneurs d’ancrage

Pour inclure dans un wrapper une fonction Azure dans un conteneur d’ancrage, installez le Azure Functions Core Tools puis exécutez la commande suivante :

```console
func init ProjectName --docker
```

Choisissez le runtime de travail de votre choix parmi les options suivantes :

- `dotnet` (C#)
- `node` (JavaScript)
- `python`

Lorsque le projet est créé, il inclut un fichier dockerfile. À présent, vous pouvez créer et tester votre fonction localement. Générez et exécutez-le à l’aide des commandes `docker build` et `docker run`. Pour obtenir des instructions détaillées pour commencer à créer des Azure Functions avec la prise en charge de l’ancrage, consultez le didacticiel [créer une fonction sur Linux à l’aide d’une image personnalisée](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image) .

## <a name="how-to-combine-serverless-and-kubernetes-with-keda"></a>Comment combiner sans serveur et Kubernetes avec KEDA

Azure Functions est mis à l’échelle automatiquement pour répondre à la demande en fonction du taux d’événements ciblant une fonction donnée. En outre, vous pouvez tirer parti de Kubernetes pour héberger vos fonctions et utiliser la mise à l’échelle automatique pilotée par les événements basée sur Kubernetes, ou KEDA. Quand aucun événement ne se produit, KEDA peut passer à 0 instance, puis, en réponse aux événements, il peut augmenter le nombre de conteneurs pour répondre à la demande à l’aide de son adapteur automatique Pod horizontal. [En savoir plus sur la mise à l’échelle d’Azure Functions avec Keda](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda).

## <a name="references"></a>Références

- [Exécuter Azure Functions dans un conteneur d’ancrage](https://markheath.net/post/azure-functions-docker)
- [Créer une fonction sur Linux à l’aide d’une image personnalisée](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)
- [Azure Functions avec la mise à l’échelle automatique pilotée par les événements Kubernetes](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda)

>[!div class="step-by-step"]
>[Précédent](leverage-serverless-functions.md)
>[Suivant](deploy-containers-azure.md)
