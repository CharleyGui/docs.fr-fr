---
title: Modèles de communication cloud natifs
description: En savoir plus sur les problèmes de communication de service clés dans les applications Cloud natives
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 3d678df44b5fef68427846e59f446b7408795625
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614212"
---
# <a name="cloud-native-communication-patterns"></a>Modèles de communication cloud natifs

Lors de la construction d’un système Cloud natif, la communication devient une décision de conception significative. Comment une application cliente frontale communique-t-elle avec un microservice principal ? Comment les microservices back-end communiquent-ils entre eux ? Quels sont les principes, les modèles et les meilleures pratiques à prendre en compte lors de l’implémentation de la communication dans des applications natives Cloud ?

## <a name="communication-considerations"></a>Considérations relatives à la communication

Dans une application monolithique, la communication est simple. Les modules de code s’exécutent dans le même espace exécutable (processus) sur un serveur. Cette approche peut offrir des avantages en termes de performances, car tous les éléments s’exécutent dans la mémoire partagée, mais génère un code étroitement couplé qui devient difficile à gérer, à faire évoluer et à mettre à l’échelle.

Les systèmes Cloud natifs implémentent une architecture basée sur des microservices avec de nombreux microservices indépendants. Chaque microservice s’exécute dans un processus distinct et s’exécute généralement à l’intérieur d’un conteneur déployé sur un *cluster*.

Un cluster regroupe un pool de machines virtuelles ensemble pour former un environnement hautement disponible. Ils sont gérés à l’aide d’un outil d’orchestration, qui est chargé de déployer et de gérer les microservices en conteneur. La figure 4-1 illustre un cluster [Kubernetes](https://kubernetes.io) déployé dans le Cloud Azure avec les [services Azure Kubernetes](https://docs.microsoft.com/azure/aks/intro-kubernetes)entièrement gérés.

![Un cluster Kubernetes dans Azure](./media/kubernetes-cluster-in-azure.png)

**Figure 4-1**. Un cluster Kubernetes dans Azure

Au sein du cluster, les microservices communiquent entre eux via des API et des technologies de messagerie.

Bien qu’elles offrent de nombreux avantages, les microservices ne sont pas gratuits. Les appels de méthode in-process locaux entre les composants sont désormais remplacés par des appels réseau. Chaque microservice doit communiquer via un protocole réseau, ce qui augmente la complexité de votre système :

- La congestion du réseau, la latence et les défaillances temporaires sont une préoccupation constante.

- La résilience (c’est-à-dire les nouvelles tentatives de demandes ayant échoué) est essentielle.

- Certains appels doivent être [idempotent](https://www.restapitutorial.com/lessons/idempotency.html) comme pour conserver un état cohérent.

- Chaque microservice doit authentifier et autoriser les appels.

- Chaque message doit être sérialisé, puis désérialisé, ce qui peut être coûteux.

- Le chiffrement/déchiffrement des messages devient important.

L’ouvrage [.net microservices : architecture pour les applications .net en conteneur](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook), disponible gratuitement auprès de Microsoft, fournit une couverture approfondie des modèles de communication pour les applications de microservices. Dans ce chapitre, nous fournissons une vue d’ensemble détaillée de ces modèles, ainsi que des options d’implémentation disponibles dans le Cloud Azure.

Dans ce chapitre, nous allons commencer par traiter la communication entre les applications frontales et les microservices back-end. Nous examinerons ensuite les microservices principaux qui communiquent entre eux. Nous allons explorer les technologies de communication gRPC et up. Enfin, nous allons découvrir de nouveaux modèles de communication novateurs à l’aide de la technologie service Mesh. Nous verrons également comment le Cloud Azure fournit différents types de *services de stockage* pour prendre en charge la communication Native Cloud.

>[!div class="step-by-step"]
>[Précédent](other-deployment-options.md) 
> [Suivant](front-end-communication.md)
