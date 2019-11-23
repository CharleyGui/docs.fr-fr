---
title: Déploiement d’eShopOnContainers sur Azure
description: Déploiement de l’application eShopOnContainers à l’aide du service Azure Kubernetes, Helm et DevSpaces.
ms.date: 06/30/2019
ms.openlocfilehash: 21033cc904dc595193c69f3452ce2522740f8ff6
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183272"
---
# <a name="deploying-eshoponcontainers-to-azure"></a>Déploiement d’eShopOnContainers sur Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

La logique de prise en charge de l’application eShopOnContainers peut être prise en charge par Azure à l’aide d’un large éventail de services. L’approche recommandée consiste à exploiter Kubernetes à l’aide d’Azure Kubernetes service (AKS). Cela peut être combiné avec le déploiement Helm pour garantir une configuration d’infrastructure facilement répétée. Les développeurs peuvent éventuellement tirer parti de Azure Dev Spaces pour Kubernetes dans le cadre de leur processus de développement. Une autre option consiste à héberger les fonctionnalités de l’application à l’aide de fonctionnalités sans serveur Azure comme Azure Functions et Azure Logic Apps.

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Si vous souhaitez héberger l’application eShopOnContainers dans votre propre cluster AKS, la première étape consiste à créer votre cluster. Vous pouvez le faire à l’aide de la Portail Azure, qui vous guidera tout au long des étapes nécessaires, ou vous pouvez utiliser le Azure CLI, en veillant à activer l’Access Control basé sur les rôles (RBAC) et le routage des applications. La documentation de eShopOnContainers décrit les étapes nécessaires à la création de votre propre cluster AKS. Une fois le cluster créé, vous devez activer l’accès au tableau de bord Kubernetes, à partir duquel vous devez être en mesure d’accéder au tableau de bord Kubernetes pour gérer le cluster.

Une fois que le cluster a été créé et configuré, vous pouvez y déployer l’application à l’aide de Helm et de l’écran de veille.

## <a name="deploying-to-azure-kubernetes-service-using-helm"></a>Déploiement sur le service Azure Kubernetes à l’aide de Helm

Les déploiements de base sur AKS peuvent utiliser des scripts CLI personnalisés ou des fichiers de déploiement simples, mais des applications plus complexes doivent utiliser un outil de gestion des dépendances comme Helm. Helm est géré par la Fondation informatique Native Cloud et vous aide à définir, installer et mettre à niveau des applications Kubernetes. Helm se compose d’un client de ligne de commande, Helm, qui utilise des graphiques Helm et un composant in-cluster, jusqu’à présent. Les graphiques Helm utilisent des fichiers au format YAML standard pour décrire un ensemble connexe de ressources Kubernetes et sont généralement associés à une version parallèle à l’application qu’ils décrivent. Les graphiques Helm vont du plus simple au plus complexe selon les exigences de l’installation qu’ils décrivent.

Vous trouverez les graphiques eShopOnContainers Helm dans le dossier/K8S/Helm. La figure 2-6 montre comment les différents composants de l’application sont organisés dans une structure de dossiers utilisée par Helm pour définir et gérer des déploiements.

![architecture eShopOnContainers](./media/eshoponcontainers-helm-folder.png)
**Figure 2-6**. Dossier eShopOnContainers Helm.

Chaque composant individuel est installé à l’aide d’une commande `helm install`. Ces commandes sont facilement scriptées, et eShopOnContainers fournit un script « déployer tout » qui parcourt les différents composants et les installe à l’aide de leurs graphiques Helm respectifs. Le résultat est un processus reproductible, avec version avec l’application dans le contrôle de code source, que tous les membres de l’équipe peuvent déployer sur un cluster AKS à l’aide d’une commande de script d’une ligne. En particulier lorsqu’il est associé à Azure Dev Spaces, cela permet aux développeurs de diagnostiquer et de tester facilement leurs modifications individuelles sur leurs applications Cloud natives basées sur des microservices.

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

Azure Dev Spaces aide les développeurs individuels à héberger leur propre version unique de clusters AKS dans Azure pendant le développement. Cela réduit la configuration requise de l’ordinateur local et permet aux membres de l’équipe de voir rapidement comment leurs modifications se comporteront dans un environnement AKS réel. Azure Dev Spaces offre une interface CLI permettant aux développeurs de gérer leurs espaces de développement et de les déployer dans un espace de développement enfant spécifique en fonction des besoins. Chaque espace de développement enfant est référencé à l’aide d’un sous-domaine d’URL unique, ce qui permet des déploiements côte à côte de clusters modifiés, de sorte que les développeurs individuels puissent éviter les conflits entre les travaux en cours. Dans la figure 2-7, vous pouvez voir comment Developer Julie a déployé sa propre version du microservice Bikes dans son espace de développement. Elle est ensuite en mesure de tester ses modifications à l’aide d’une URL personnalisée commençant par le nom de son espace (susie.s.dev.myapp.eus.azds.io).

![architecture eShopOnContainers](./media/azure-devspaces-one.png)
**Figure 2-7**. Developer Julie déploie sa propre version du microservice Bikes et le teste.

En même temps, le développeur John souhaite personnaliser le microservice de réservations et doit tester ses modifications. Il peut déployer ses modifications dans son propre espace de développement sans conflit avec les modifications apportées à Julie, comme illustré dans la figure 2-8. Il peut tester ses modifications à l’aide de sa propre URL, qui est précédée du nom de son espace (john.s.dev.myapp.eus.azds.io).

![architecture eShopOnContainers](./media/azure-devspaces-two.png)
**Figure 2-8**. Le développeur John déploie sa propre version du microservice de réservations et le teste sans conflit avec d’autres développeurs.

À l’aide de Azure Dev Spaces, les équipes peuvent travailler directement avec AKS tout en modifiant, déployant et testant leurs modifications de manière indépendante. Cette approche réduit le besoin d’environnements hébergés dédiés distincts, car chaque développeur a son propre environnement AKS. Les développeurs peuvent travailler avec Azure Dev Spaces à l’aide de l’interface CLI ou lancer leur application pour Azure Dev Spaces directement à partir de Visual Studio. [En savoir plus sur le fonctionnement de Azure Dev Spaces et sur la configuration.](https://docs.microsoft.com/azure/dev-spaces/how-dev-spaces-works)

## <a name="azure-functions-and-logic-apps-serverless"></a>Azure Functions et Logic Apps (sans serveur)

L’exemple eShopOnContainers comprend la prise en charge du suivi des campagnes marketing en ligne. Une fonction Azure est utilisée pour extraire les détails d’une campagne marketing pour un ID de campagne donné. Au lieu de créer une application ASP.NET Core complète à cet effet, un seul point de terminaison Azure Function est plus simple et suffisant. Les Azure Functions ont un modèle de génération et de déploiement bien plus simple que les applications ASP.NET Core complètes, en particulier lorsqu’elles sont configurées pour s’exécuter dans Kubernetes. Le déploiement de la fonction est un script à l’aide de modèles ARM (Azure Resource Manager) et du Azure CLI. Le microservice détails de la campagne n’est pas orienté client et n’a pas les mêmes exigences que le magasin en ligne, ce qui en fait un bon candidat pour la Azure Functions. La fonction nécessite une configuration pour fonctionner correctement, comme les données de chaîne de connexion à la base de données et les paramètres d’URI de base d’image. Vous configurez Azure Functions dans le portail Azure.

## <a name="references"></a>Références

- [eShopOnContainers : créer un cluster Kubernetes dans AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Deploy-to-Azure-Kubernetes-Service-(AKS)#create-kubernetes-cluster-in-aks)
- [eShopOnContainers : Azure Dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Azure-Dev-Spaces)
- [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/about)

>[!div class="step-by-step"]
>[Précédent](map-eshoponcontainers-azure-services.md)
>[Suivant](centralized-configuration.md)
