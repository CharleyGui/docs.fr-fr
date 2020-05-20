---
title: Déploiement d’eShopOnContainers sur Azure
description: Déploiement de l’application eShopOnContainers à l’aide du service Azure Kubernetes, Helm et DevSpaces.
ms.date: 05/13/2020
ms.openlocfilehash: 93a2848f095d7593e1e169f4a6c6c1818a76217d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614095"
---
# <a name="deploying-eshoponcontainers-to-azure"></a>Déploiement d’eShopOnContainers sur Azure

L’application eShopOnContainers peut être déployée sur une variété de plateformes Azure. L’approche recommandée consiste à déployer l’application sur Azure Kubernetes services (AKS). Helm, un outil de déploiement Kubernetes, est disponible pour réduire la complexité du déploiement. Si vous le souhaitez, les développeurs peuvent implémenter Azure Dev Spaces pour Kubernetes afin de simplifier leur processus de développement.

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Pour héberger eShop dans AKS, la première étape consiste à créer un cluster AKS. Pour ce faire, vous pouvez utiliser le Portail Azure, qui vous guidera tout au long des étapes requises. Vous pouvez également créer un cluster à partir de la Azure CLI, en veillant à activer la Access Control basée sur les rôles (RBAC) et le routage des applications. La documentation de eShopOnContainers décrit les étapes de création de votre propre cluster AKS. Une fois créé, vous pouvez accéder au cluster et le gérer à partir du tableau de bord Kubernetes.

Vous pouvez maintenant déployer l’application eShop sur le cluster en tirant parti de Helm et de la caisse.

## <a name="deploying-to-azure-kubernetes-service-using-helm"></a>Déploiement sur le service Azure Kubernetes à l’aide de Helm

Helm est un outil du gestionnaire de package d’application qui fonctionne directement avec Kubernetes. Il vous aide à définir, installer et mettre à niveau des applications Kubernetes. Bien que les applications simples puissent être déployées sur AKS avec des scripts CLI personnalisés ou des fichiers de déploiement simples, les applications complexes peuvent contenir de nombreux objets Kubernetes et tirer parti de Helm.

À l’aide de Helm, les applications incluent des fichiers de configuration textuels, appelés graphiques Helm, qui décrivent de façon déclarative l’application et la configuration dans les packages Helm. Les graphiques utilisent des fichiers au format YAML standard pour décrire un ensemble connexe de ressources Kubernetes. Elles sont gérées avec le code d’application qu’elles décrivent. Les graphiques Helm vont du plus simple au plus complexe selon les exigences de l’installation qu’ils décrivent.

Helm se compose d’un outil client de ligne de commande, qui consomme des graphiques Helm et lance des commandes sur un composant serveur nommé, jusqu’à ce que le soit. Jusqu’à la communication avec l’API Kubernetes pour garantir la bonne configuration de vos charges de travail en conteneur. Helm est géré par la Fondation Cloud-Native Computing.

Le fichier YAML suivant présente un modèle Helm :

```yaml
apiVersion: v1
kind: Service
metadata:
  name: {{ .Values.app.svc.marketing }}
  labels:
    app: {{ template "marketing-api.name" . }}
    chart: {{ template "marketing-api.chart" . }}
    release: {{ .Release.Name }}
    heritage: {{ .Release.Service }}
spec:
  type: {{ .Values.service.type }}
  ports:
    - port: {{ .Values.service.port }}
      targetPort: http
      protocol: TCP
      name: http
  selector:
    app: {{ template "marketing-api.name" . }}
    release: {{ .Release.Name }}
```

Notez comment le modèle décrit un ensemble dynamique de paires clé/valeur. Lorsque le modèle est appelé, les valeurs qui sont placées entre accolades sont extraites à partir d’autres fichiers de configuration basés sur YAML.

Vous trouverez les graphiques eShopOnContainers Helm dans le dossier/K8S/Helm. La figure 2-6 montre comment les différents composants de l’application sont organisés dans une structure de dossiers utilisée par Helm pour définir et gérer des déploiements.

![eShopOnContainers architecture de la ](./media/eshoponcontainers-helm-folder.png)
 **figure 2-6**. Dossier eShopOnContainers Helm.

Chaque composant individuel est installé à l’aide d’une `helm install` commande. eShop inclut un script « déployer tout » qui parcourt et installe les composants à l’aide de leurs graphiques Helm respectifs. Le résultat est un processus reproductible, avec version avec l’application dans le contrôle de code source, que tous les membres de l’équipe peuvent déployer sur un cluster AKS à l’aide d’une commande de script d’une ligne.

> Notez que la version 3 de Helm supprime officiellement le besoin du composant serveur de l’écran de veille. Vous trouverez plus d’informations sur cette amélioration [ici](https://medium.com/better-programming/why-is-tiller-missing-in-helm-3-2347c446714).

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

Les applications Cloud natives peuvent rapidement devenir volumineuses et complexes, ce qui nécessite des ressources de calcul importantes pour s’exécuter. Dans ces scénarios, l’ensemble de l’application ne peut pas être hébergé sur un ordinateur de développement (en particulier un ordinateur portable). Azure Dev Spaces est conçu pour résoudre ce problème à l’aide de AKS. Il permet aux développeurs de travailler avec une version locale de leurs services tout en hébergeant le reste de l’application dans un cluster de développement AKS.

Les développeurs partagent une instance en cours d’exécution (développement) dans un cluster AKS qui contient l’application en conteneur entière. Mais ils utilisent des espaces personnels configurés sur leur ordinateur pour développer localement leurs services. Lorsqu’ils sont prêts, ils testent de bout en bout dans le cluster AKS, sans répliquer les dépendances. Azure Dev Spaces fusionne le code à partir de l’ordinateur local avec les services dans AKS. Les membres de l’équipe peuvent voir comment leurs modifications se comporteront dans un environnement AKS réel. Les développeurs peuvent rapidement itérer et déboguer du code directement dans Kubernetes à l’aide de Visual Studio 2017 ou Visual Studio Code.

Dans la figure 2-7, vous pouvez voir que Developer Julie a déployé une version mise à jour du microservice Bikes dans son espace de développement. Elle est ensuite en mesure de tester ses modifications à l’aide d’une URL personnalisée commençant par le nom de son espace (susie.s.dev.myapp.eus.azds.io).

![eShopOnContainers architecture de la ](./media/azure-devspaces-one.png)
 **figure 2-7**. Developer Julie déploie sa propre version du microservice Bikes et le teste.

En même temps, le développeur John souhaite personnaliser le microservice de réservations et doit tester ses modifications. Il déploie ses modifications dans son propre espace de développement sans entrer en conflit avec les modifications apportées à Julie, comme illustré dans la figure 2-8. John teste ensuite ses modifications à l’aide de sa propre URL, précédée du nom de son espace (john.s.dev.myapp.eus.azds.io).

![eShopOnContainers architecture de la ](./media/azure-devspaces-two.png)
 **figure 2-8**. Le développeur John déploie sa propre version du microservice de réservations et le teste sans conflit avec d’autres développeurs.

À l’aide de Azure Dev Spaces, les équipes peuvent travailler directement avec AKS tout en modifiant, déployant et testant leurs modifications de manière indépendante. Cette approche réduit le besoin d’environnements hébergés dédiés distincts, car chaque développeur a son propre environnement AKS. Les développeurs peuvent travailler avec Azure Dev Spaces à l’aide de l’interface CLI ou lancer leur application pour Azure Dev Spaces directement à partir de Visual Studio. [En savoir plus sur le fonctionnement de Azure Dev Spaces et sur la configuration.](https://docs.microsoft.com/azure/dev-spaces/how-dev-spaces-works)

## <a name="azure-functions-and-logic-apps-serverless"></a>Azure Functions et Logic Apps (sans serveur)

L’exemple eShopOnContainers comprend la prise en charge du suivi des campagnes marketing en ligne. Une fonction Azure est utilisée pour suivre les détails d’une campagne marketing pour un ID de campagne donné. Au lieu de créer un microservice complet, une seule fonction Azure est plus simple et suffisante. Azure Functions avoir un modèle de génération et de déploiement simple, surtout lorsqu’il est configuré pour s’exécuter dans Kubernetes. Le déploiement de la fonction est un script à l’aide de modèles ARM (Azure Resource Manager) et du Azure CLI. Ce service de campagne n’est pas orienté client et appelle une seule opération, ce qui en fait un bon candidat pour Azure Functions. La fonction nécessite une configuration minimale, y compris des données de chaîne de connexion à la base de données et des paramètres d’URI de base d’image. Vous configurez Azure Functions dans le Portail Azure.

>[!div class="step-by-step"]
>[Précédent](map-eshoponcontainers-azure-services.md) 
> [Suivant](centralized-configuration.md)
