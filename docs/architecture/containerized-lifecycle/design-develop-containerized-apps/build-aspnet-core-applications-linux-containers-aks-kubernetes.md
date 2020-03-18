---
title: Créer des applications ASP.NET Core 2.2 déployées en tant que conteneurs Linux dans des clusters AKS/Kubernetes
description: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft
ms.date: 02/25/2019
ms.openlocfilehash: ab64a0423ceceb8285c159af276d6d97e12379d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70848756"
---
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a>Créer des applications ASP.NET Core 2.2 déployées en tant que conteneurs Linux dans un orchestrateur AKS/Kubernetes

Azure Kubernetes Service (AKS) correspond à des services d’orchestrations Kubernetes gérés par Azure qui simplifient la gestion et le déploiement de conteneurs.

Les principales fonctionnalités AKS sont les suivantes :

- Plan de contrôle hébergé par Azure
- Mises à niveau automatisées
- Réparation spontanée
- Mise à l’échelle configurable par l’utilisateur
- Expérience utilisateur plus simple pour les développeurs et les opérateurs de cluster

Les exemples suivants décrivent la création d’une application ASP.NET Core 2.2 qui s’exécute sur Linux et se déploie sur un cluster AKS dans Azure, tandis que le développement est effectué à l’aide de Visual Studio 2017.

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a>Création du projet ASP.NET Core 2.2 à l’aide de Visual Studio 2017

ASP.NET Core est une plateforme de développement généraliste tenue à jour par Microsoft et la communauté .NET sur GitHub. Cette multiplateforme prend en charge Windows, macOS et Linux. Elle peut être utilisée dans des scénarios d’appareil, de cloud et d’incorporation/IoT.

Cet exemple utilise un projet simple basé sur un modèle d’API web Visual Studio, si bien que vous n’avez pas besoin de connaissances supplémentaires. Vous devez uniquement créer le projet à l’aide d’un modèle standard qui inclut tous les éléments nécessaires pour exécuter un petit projet avec une API REST, à l’aide de la technologie ASP.NET Core 2.2.

![Ajoutez une nouvelle fenêtre de projet dans Visual Studio, en sélectionnant Application web ASP.NET Core.](media/create-aspnet-core-application.png)

**Figure 4-36**. Création d’une application ASP.NET Core

Pour créer l’exemple de projet dans Visual Studio, sélectionnez **File** > **New** > **Project**, sélectionnez les types de projet **Web** dans le volet gauche, **suivis de ASP.NET application Web de base.**

Visual Studio liste les modèles pour les projets web. Pour notre exemple, sélectionnez **API** pour créer une application API Web ASP.NET.

Vérifiez que vous avez sélectionné le framework ASP.NET Core 2.2. .NET Core 2.2, inclus dans la dernière version de Visual Studio 2017, est automatiquement installé et configuré pour vous lorsque vous installez Visual Studio 2017.

![Boîte de dialogue Visual Studio permettant de sélectionner le type Application web ASP.NET Core avec l’option API sélectionnée.](media/create-web-api-application.png)

**Figure 4-37**. Sélection du type de projet ASP.NET CORE 2.2 et API web

Si vous avez des versions antérieures de .NET Core, vous pouvez télécharger et installer la version 2.2 à partir de <https://dotnet.microsoft.com/download>.

Vous pouvez ajouter la prise en charge de Docker lors de la création du projet ou par la suite, de sorte à pouvoir « dockeriser » votre projet à tout moment. Pour ajouter le support Docker après la création du projet, cliquez à droite sur le nœud du projet dans Solution Explorer et **sélectionnez le** > support Add**Docker** sur le menu context.

![Option de menu contextuelle pour ajouter le support Docker à un projet existant : Cliquez à droite (sur le projet) > Ajouter > support Docker.](media/add-docker-support-to-project.png)

**Figure 4-38**. Ajout de la prise en charge de Docker à un projet existant

Pour terminer l’ajout de la prise en charge de Docker, vous pouvez choisir Windows ou Linux. Pour notre exemple, sélectionnez **Linux**, car AKS ne prend pas en charge les conteneurs Windows (depuis la fin 2018).

![Boîte de dialogue Option permettant de sélectionner le système d’exploitation cible pour Dockerfile.](media/select-linux-docker-support.png)

**Figure 4-39**. Sélection de conteneurs Linux

À l’issue de ces étapes simples, votre application ASP.NET Core 2.2 s’exécute sur un conteneur Linux.

Comme vous pouvez le voir, l’intégration entre Visual Studio 2017 et Docker est entièrement orientée vers la productivité du développeur.

Vous pouvez maintenant exécuter votre application avec la touche **F5** ou en utilisant le bouton **Lecture**.

Après avoir exécuté le projet, vous pouvez lister les images à l’aide de la commande `docker images`. Vous devez voir l’image `mssampleapplication` créée par le déploiement automatique de notre projet avec Visual Studio 2017.

```console
docker images
```

![Sortie de la console à partir de la commande d’images docker, montre une liste avec: Dépôt, Tag, Id Image, Créé (date), et La taille.](media/docker-images-command.png)

**Figure 4-40**. Affichage des images Docker

## <a name="register-the-solution-in-the-azure-container-registry"></a>Inscrire la solution dans Azure Container Registry

Chargez l’image dans un registre Docker, comme [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) ou Docker Hub, de sorte à pouvoir la déployer sur le cluster AKS de ce registre. Pour notre exemple, nous chargeons l’image dans Azure Container Registry.

### <a name="create-the-image-in-release-mode"></a>Créer l’image en mode Mise en production

Nous allons maintenant créer l’image en mode **Mise en production** en choisissant l’option **Mise en production**, comme illustré dans la figure 4-41, puis en exécutant l’application comme nous l’avons fait auparavant.

![Option de barre d’outils dans Visual Studio pour créer en mode Mise en production.](media/select-release-mode.png)

**Figure 4-41**. Sélection du mode Mise en production

Si vous exécutez la commande `docker image`, vous voyez deux images créées, une pour le mode `debug` et l’autre pour le mode `release`.

### <a name="create-a-new-tag-for-the-image"></a>Créer une balise pour l’image

Chaque image de conteneur doit être marquée avec le `loginServer` nom du registre. Cette balise est utilisée pour l’acheminement lors de l’envoi des images de conteneur dans un registre d’images.

Vous pouvez voir le nom `loginServer` à partir du portail Azure, en prenant les informations auprès d’Azure Container Registry.

![Affichage dans le navigateur du nom du registre de conteneurs Azure, dans le coin supérieur droit.](media/loginServer-name.png)

**Figure 4-42**. Affichage du nom du registre

Ou en exécutant la commande suivante :

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Sortie de console issue de la commande ci-dessus.](media/az-cli-loginServer-name.png)

**Figure 4-43**. Obtenir le nom du registre à l’aide de PowerShell

Dans les deux cas, vous obtenez le nom. Dans notre exemple, `mssampleacr.azurecr.io`.

Maintenant vous pouvez baliser l’image, en prenant la dernière (l’image de mise en production), avec la commande :

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Après avoir exécuté la commande `docker tag`, listez les images avec la commande `docker images`. L’image doit apparaître avec la nouvelle balise.

![Sortie de console issue de la commande docker images.](media/tagged-docker-images-list.png)

**Figure 4-44**. Vue des images balisées

### <a name="push-the-image-into-the-azure-acr"></a>Pousser (push) l’image vers Azure Container Registry

Connectez-vous à Azure Container Registry.

```console
az acr login --name mssampleacr
```

Poussez (push) l’image vers Azure Container Registry avec la commande suivante :

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Cette commande a besoin de temps pour charger les images, mais vous tient informé pendant le processus.

![La sortie de console issue de la commande docker push présente une barre de progression sous forme de caractères pour chaque couche.](media/uploading-image-to-acr.png)

**Figure 4-45**. Chargement de l’image dans Azure Container Registry

Vous pouvez voir ci-dessous le résultat que vous devez obtenir lorsque le processus est terminé :

![Sortie de console issue de la commande docker push terminée, montrant la totalité des couches ou nœuds.](media/uploading-docker-images-complete.png)

**Figure 4-46**. Affichage des nœuds

L’étape suivante consiste à déployer votre conteneur dans votre cluster AKS Kubernetes. Pour cela, vous avez besoin d’un fichier (**fichier de déploiement .yml**) qui contient ceci :

```yml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: mssamplesbook
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: mssample-kub-app
    spec:
      containers:
        - name: mssample-services-app
          image: mssampleacr.azurecr.io/mssampleaksapplication:v1
          ports:
            - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
    name: mssample-kub-app
spec:
  ports:
    - name: http-port
      port: 80
      targetPort: 80
  selector:
    app: mssample-kub-app
  type: LoadBalancer
```

> [!NOTE]
> Pour plus d’informations sur le déploiement avec Kubernetes, consultez : <https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

Vous êtes maintenant presque prêt à effectuer un déploiement en utilisant **Kubectl**, mais vous devez tout d’abord obtenir les informations d’identification pour le cluster AKS avec cette commande :

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Sortie de console de la commande ci-dessus: Fusionné "MSSampleK8Cluster comme contexte actuel dans /root/.kube/config](media/getting-aks-credentials.png)

**Figure 4-47**. Obtention des informations d’identification

Ensuite, utilisez la commande `kubectl create` pour lancer le déploiement.

```console
kubectl create -f mssample-deploy.yml
```

![Sortie de console issue de la commande ci-dessus : deployment "mssamplesbook" created. service "mssample-kub-app" created.](media/kubectl-create-command.png)

**Figure 4-48**. Déployer sur Kubernetes

Lorsque le déploiement est terminé, vous pouvez accéder à la console Kubernetes avec un proxy local auquel vous pouvez accéder temporairement avec cette commande :

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

Puis accédez à l’URL `http://127.0.0.1:8001`.

![Affichage dans le navigateur du tableau de bord Kubernetes, montrant les déploiements, les pods, les jeux de réplicas et les services.](media/kubernetes-cluster-information.png)

**Figure 4-49**. Afficher les informations de cluster Kubernetes

Votre application est maintenant déployée sur Azure, à l’aide d’un conteneur Linux et d’un cluster AKS Kubernetes. Vous pouvez accéder à votre application par le biais de l’adresse IP publique de votre service, que vous pouvez obtenir à partir du portail Azure.

> [!NOTE]
> Vous pouvez voir comment créer le cluster AKS pour cet exemple dans la section [**Déployer sur Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) de ce guide.

>[!div class="step-by-step"]
>[Suivant précédent](set-up-windows-containers-with-powershell.md)
>[Next](../docker-devops-workflow/index.md)
