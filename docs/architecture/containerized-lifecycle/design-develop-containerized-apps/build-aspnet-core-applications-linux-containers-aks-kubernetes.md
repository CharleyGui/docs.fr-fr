---
title: Créer des applications ASP.NET Core déployées en tant que conteneurs Linux dans des clusters AKS/Kubernetes
description: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft
ms.date: 08/06/2020
ms.openlocfilehash: 4b04e5d56c73918c665ad6e2825205870aac9606
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916454"
---
# <a name="build-aspnet-core-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a>Créez ASP.NET Core applications déployées en tant que conteneurs Linux dans un AKS/Kubernetes Orchestrator

Azure Kubernetes Service (AKS) correspond à des services d’orchestrations Kubernetes gérés par Azure qui simplifient la gestion et le déploiement de conteneurs.

Les principales fonctionnalités AKS sont les suivantes :

- Plan de contrôle hébergé par Azure
- Mises à niveau automatisées
- Autoréparation
- Mise à l’échelle configurable par l’utilisateur
- Expérience utilisateur plus simple pour les développeurs et les opérateurs de cluster.

Les exemples suivants explorent la création d’une application ASP.NET Core 3,1 qui s’exécute sur Linux et est déployée sur un cluster AKS dans Azure, tandis que le développement s’effectue à l’aide de Visual Studio 2019.

## <a name="creating-the-aspnet-core-project-using-visual-studio-2019"></a>Création du projet ASP.NET Core à l’aide de Visual Studio 2019

ASP.NET Core est une plateforme de développement généraliste tenue à jour par Microsoft et la communauté .NET sur GitHub. Cette multiplateforme prend en charge Windows, macOS et Linux. Elle peut être utilisée dans des scénarios d’appareil, de cloud et d’incorporation/IoT.

Cet exemple utilise deux projets simples basés sur des modèles Visual Studio. vous n’avez donc pas besoin de connaissances supplémentaires pour créer l’exemple. Vous devez uniquement créer le projet à l’aide d’un modèle standard qui comprend tous les éléments pour exécuter un petit projet avec une API REST et une application Web avec les pages Razor, à l’aide de la technologie ASP.NET Core 3,1.

![Ajoutez une nouvelle fenêtre de projet dans Visual Studio, en sélectionnant Application web ASP.NET Core.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-aspnet-core-application.png)

**Figure 4-35**. Création d’une application Web ASP.NET Core dans Visual Studio 2019.

Pour créer l’exemple de projet dans Visual Studio, sélectionnez **fichier**  >  **nouveau**  >  **projet**, sélectionnez le type de projet **Web** , puis le modèle d' **application Web ASP.net Core** . Vous pouvez également rechercher le modèle si vous en avez besoin.

Entrez ensuite le nom et l’emplacement de l’application, comme indiqué dans l’image suivante.

![Entrez le nom et l’emplacement du projet.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/enter-project-name-and-location.png)

**Figure 4-36**. Entrez le nom et l’emplacement du projet dans Visual Studio 2019.

Vérifiez que vous avez sélectionné ASP.NET Core 3,1 comme Framework. .NET Core 3,1 est inclus dans la dernière version de Visual Studio 2019 et est automatiquement installé et configuré lorsque vous installez Visual Studio.

![Boîte de dialogue Visual Studio permettant de sélectionner le type Application web ASP.NET Core avec l’option API sélectionnée.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-web-api-application.png)

**Figure 4-37**. Sélection de ASP.NET CORE 3,1 et du type de projet d’API Web

Notez que la prise en charge de l’ancrage n’est pas activée pour l’instant. pour l’afficher, vous pouvez le faire après la création du projet.

Si vous disposez d’une version antérieure de .NET Core, vous pouvez télécharger et installer la version 3,1 à partir de <https://dotnet.microsoft.com/download> .

Pour vous montrer que vous pouvez « Dockeriser » votre projet à tout moment, vous allez ajouter la prise en charge de l’ancrage maintenant. Cliquez avec le bouton droit sur le nœud du projet dans Explorateur de solutions puis sélectionnez **Ajouter**  >  la**prise en charge** de l’ancrage dans le menu contextuel.

![Option de menu contextuel pour ajouter la prise en charge de l’ancrage à un projet existant : cliquez avec le bouton droit (sur le projet) > ajoutez > prise en charge de l’ancrage.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-docker-support-to-project.png)

**Figure 4-38**. Ajout de la prise en charge de l’ancrage à un projet existant

Pour terminer l’ajout de la prise en charge de Docker, vous pouvez choisir Windows ou Linux. Dans ce cas, sélectionnez **Linux**.

![Boîte de dialogue Option permettant de sélectionner le système d’exploitation cible pour Dockerfile.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-linux-docker-support.png)

**Figure 4-39**. Sélection de conteneurs Linux

Avec ces étapes simples, votre application ASP.NET Core 3,1 s’exécute sur un conteneur Linux.

De la même façon, vous pouvez également ajouter un projet **webapp** très simple (figure 4-40) pour consommer le point de terminaison de l’API Web, bien que les détails ne soient pas abordés ici.

Après cela, vous ajoutez la prise en charge d’Orchestrator pour votre projet **WebApi** , comme illustré ci-dessous, dans l’image 4-40.

![Ajout de la prise en charge d’Orchestrator au projet WebApi](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-orchestrator-support.png)

**Figure 4-40**. Ajout de la prise en charge d’Orchestrator au projet *WebApi* .

Quand vous choisissez l' `Docker Compose` option, ce qui convient pour le développement local, Visual Studio ajoute le projet dockr-compose, avec les fichiers dockr-compose, comme indiqué dans l’image 4-41.

![Dockr-compose ajouté à la solution](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-compose-project-in-visual-studio.png)

**Figure 4-41**. Ajout de la prise en charge d’Orchestrator au projet *WebApi* .

Les fichiers initiaux ajoutés sont similaires à ceux-ci :

`docker-compose.yml`

```yml
version: "3.4"

services:
  webapi:
    image: ${DOCKER_REGISTRY-}webapi
    build:
      context: .
      dockerfile: WebApi/Dockerfile

  webapp:
    image: ${DOCKER_REGISTRY-}webapp
    build:
      context: .
      dockerfile: WebApp/Dockerfile
```

`docker-compose.override.yml`

```yml
version: "3.4"

services:
  webapi:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=https://+:443;http://+:80
    ports:
      - "80"
      - "443"
    volumes:
      - ${APPDATA}/Microsoft/UserSecrets:/root/.microsoft/usersecrets:ro
      - ${APPDATA}/ASP.NET/Https:/root/.aspnet/https:ro
  webapp:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=https://+:443;http://+:80
    ports:
      - "80"
      - "443"
    volumes:
      - ${APPDATA}/Microsoft/UserSecrets:/root/.microsoft/usersecrets:ro
      - ${APPDATA}/ASP.NET/Https:/root/.aspnet/https:ro
```

Pour que votre application s’exécute avec Docker Compose vous devez simplement apporter quelques ajustements à`docker-compose.override.yml`

```yml
services:
  webapi:
    #...
    ports:
      - "51080:80"
      - "51443:443"
    #...
  webapp:
    environment:
      #...
      - WebApiBaseAddress=http://webapi
    ports:
      - "50080:80"
      - "50443:443"
    #...
```

Vous pouvez maintenant exécuter votre application avec la touche **F5** , ou en utilisant le bouton de **lecture** , ou la touche **CTRL + F5** , en sélectionnant le projet dockr-compose, comme illustré dans l’image 4-42.

![Exécution du projet dockr-compose avec Visual Studio](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/running-docker-compose-with-visual-studio.png)

**Figure 4-42**. Ajout de la prise en charge d’Orchestrator au projet *WebApi* .

Lors de l’exécution de l’application dockr-compose comme expliqué, vous disposez des éléments suivants :

1. Images générées et conteneurs créés en fonction du fichier dockr-compose.
2. Le navigateur est ouvert à l’adresse configurée dans la boîte de dialogue Propriétés du `docker-compose` projet.
3. La fenêtre de **conteneur** s’ouvre (dans Visual Studio 2019 version 16,4 et versions ultérieures).
4. Prise en charge du débogueur pour tous les projets de la solution, comme illustré dans les images suivantes.

Navigateur ouvert :

![Affichage du navigateur avec l’application Web en cours d’exécution](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/browser-opened.png)

**Figure 4-43**. Fenêtre de navigateur avec une application exécutée sur plusieurs conteneurs.

Fenêtre conteneurs :

![Fenêtre « conteneurs » de Visual Studio](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/visual-studio-containers-window.png)

**Figure 4-44**. Fenêtre « conteneurs » de Visual Studio

La fenêtre **conteneurs** vous permet d’afficher les conteneurs en cours d’exécution, de parcourir les images disponibles, d’afficher les variables d’environnement, les journaux et les mappages de port, d’inspecter le système de fichiers, d’attacher un débogueur ou d’ouvrir une fenêtre de terminal à l’intérieur de l’environnement de conteneur.

Comme vous pouvez le voir, l’intégration entre Visual Studio 2019 et docker est entièrement orientée vers la productivité du développeur.

Bien entendu, vous pouvez également répertorier les images à l’aide de la `docker images` commande. Vous devez voir les `webapi` `webapp` images et avec les `dev` balises créées par le déploiement automatique de notre projet avec Visual Studio 2019.

```console
docker images
```

![La sortie de console de la commande dockers images affiche une liste avec : dépôt, étiquette, ID d’image, créé (date) et taille.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-images-command.png)

**Figure 4-45**. Affichage des images Docker

## <a name="register-the-solution-in-an-azure-container-registry-acr"></a>Inscrire la solution dans une Azure Container Registry (ACR)

Vous pouvez télécharger les images vers le [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/), mais vous pouvez également utiliser le hub d’ancrage ou tout autre registre, afin que les images puissent être déployées sur le cluster AKS à partir de ce registre.

### <a name="create-an-acr-instance"></a>Créer une instance ACR

Exécutez la commande suivante à partir de la commande **AZ CLI**:

```powershell
az acr create --name exploredocker --resource-group explore-docker-aks-rg --sku basic --admin-enabled
```

### <a name="create-the-image-in-release-mode"></a>Créer l’image en mode Mise en production

Vous allez maintenant créer l’image en mode de **mise** en production (prêt pour la production) en passant à la **version Release**, comme illustré dans la figure 4-46, et en exécutant l’application comme vous l’avez fait précédemment.

![Option de barre d’outils dans Visual Studio pour créer en mode Mise en production.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-release-mode.png)

**Figure 4-46**. Sélection du mode Mise en production

Si vous exécutez la `docker images` commande, vous verrez les deux images créées, une pour `debug` (**dev**) et l’autre pour le `release` mode (le**plus récent**).

### <a name="create-a-new-tag-for-the-image"></a>Créer une balise pour l’image

Chaque image de conteneur doit être marquée avec le `loginServer` nom du registre. Cette balise est utilisée pour l’acheminement lors de l’envoi des images de conteneur dans un registre d’images.

Vous pouvez voir le nom `loginServer` à partir du portail Azure, en prenant les informations auprès d’Azure Container Registry.

![Affichage dans le navigateur du nom du registre de conteneurs Azure, dans le coin supérieur droit.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/loginServer-name.png)

**Figure 4-47**. Affichage du nom du registre

Ou en exécutant la commande suivante :

```console
az acr list --resource-group <resource-group-name> --query "[].{acrLoginServer:loginServer}" --output table
```

![Sortie de console issue de la commande ci-dessus.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/az-cli-loginServer-name.png)

**Figure 4-48**. Obtient le nom du Registre à l’aide de la **commande AZ CLI**

Dans les deux cas, vous obtenez le nom. Dans notre exemple, `exploredocker.azurecr.io`.

Maintenant vous pouvez baliser l’image, en prenant la dernière (l’image de mise en production), avec la commande :

```console
docker tag <image-name>:latest <login-server-name>/<image-name>:v1
```

Après avoir exécuté la commande `docker tag`, listez les images avec la commande `docker images`. L’image doit apparaître avec la nouvelle balise.

![Sortie de console issue de la commande docker images.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/tagged-docker-images-list.png)

**Figure 4-49**. Vue des images balisées

### <a name="push-the-image-into-the-azure-acr"></a>Pousser (push) l’image vers Azure Container Registry

Connectez-vous à Azure Container Registry.

```console
az acr login --name exploredocker
```

Poussez (push) l’image vers Azure Container Registry avec la commande suivante :

```console
docker push <login-server-name>/<image-name>:v1
```

Cette commande a besoin de temps pour charger les images, mais vous tient informé pendant le processus. Dans l’image suivante, vous pouvez voir la sortie d’une image terminée et une autre en cours.

![Sortie de la console à partir de la commande dockr push.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/uploading-docker-images-complete.png)

**Figure 4-50**. Sortie de la console à partir de la commande Push.

Pour déployer votre application à conteneurs multiples dans votre cluster AKS, vous avez besoin de certains `.yaml` fichiers manifeste qui possèdent la plupart des propriétés extraites des `docker-compose.yml` `docker-compose.override.yml` fichiers et.

#### `deploy-webapi.yml`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapi
  labels:
    app: weather-forecast
spec:
  replicas: 1
  selector:
    matchLabels:
      service: webapi
  template:
    metadata:
      labels:
        app: weather-forecast
        service: webapi
    spec:
      containers:
        - name: webapi
          image: exploredocker.azurecr.io/webapi:v1
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 80
              protocol: TCP
          env:
            - name: ASPNETCORE_URLS
              value: http://+:80
---
apiVersion: v1
kind: Service
metadata:
  name: webapi
  labels:
    app: weather-forecast
    service: webapi
spec:
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    service: webapi
```

#### `deploy-webapp.yml`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp
  labels:
    app: weather-forecast
spec:
  replicas: 1
  selector:
    matchLabels:
      service: webapp
  template:
    metadata:
      labels:
        app: weather-forecast
        service: webapp
    spec:
      containers:
        - name: webapp
          image: exploredocker.azurecr.io/webapp:v1
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 80
              protocol: TCP
          env:
            - name: ASPNETCORE_URLS
              value: http://+:80
            - name: WebApiBaseAddress
              value: http://webapi
---
apiVersion: v1
kind: Service
metadata:
  name: webapp
  labels:
    app: weather-forecast
    service: webapp
spec:
  type: LoadBalancer
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    service: webapp
```

> [!NOTE]
> Les `.yml` fichiers précédents activent uniquement les `HTTP` ports, à l’aide du `ASPNETCORE_URLS` paramètre, pour éviter les problèmes liés au certificat manquant dans l’exemple d’application.

> [!TIP]
> Vous pouvez voir comment créer le cluster AKS pour cet exemple dans la section [**Déployer sur Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) de ce guide.

Maintenant, vous êtes presque prêt à déployer à l’aide de **kubectl**, mais vous devez d’abord récupérer les informations d’identification du cluster AKS avec cette commande :

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![Sortie de la console à partir de la commande ci-dessus : fusionnée « explore-docker-AKS » comme contexte actuel dans C:\Users\Miguel.kube\config](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/getting-aks-credentials.png)

**Figure 4-51**. Obtention des informations d’identification de AKS dans l’environnement kubectl.

Vous devez également autoriser le cluster AKS à extraire des images à partir du ACR, à l’aide de la commande suivante :

```console
az aks update --name explore-docker-aks --resource-group explore-docker-aks-rg --attach-acr exploredocker
```

La commande précédente peut prendre quelques minutes. Ensuite, utilisez la `kubectl apply` commande pour lancer les déploiements, puis `kubectl get all` consultez la liste des objets du cluster.

```console
kubectl apply -f deploy-webapi.yml
kubectl apply -f deploy-webapp.yml

kubectl get all
```

![Sortie de la console à partir des commandes ci-dessus : déploiements appliqués. services créés.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubectl-apply-command.png)

**Figure 4-52**. Déploiement sur Kubernetes

Vous devrez attendre un certain temps jusqu’à ce que l’équilibrage de charge récupère l’adresse IP externe, en vérifiant `kubectl get services` , puis l’application doit être disponible à cette adresse, comme indiqué dans l’image suivante :

![Vue du navigateur de l’application déployée sur AKS](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/aks-deployed-application.png)

**Figure 4-53**. Déploiement sur Kubernetes

Une fois le déploiement terminé, vous pouvez accéder à l' [interface utilisateur Web Kubernetes](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) avec un proxy local, à l’aide d’un tunnel SSH.

Tout d’abord, vous devez créer un ClusterRoleBinding avec la commande suivante :

```console
kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

Puis cette commande pour démarrer le proxy :

```console
az aks browse --resource-group exploredocker-aks-rg --name explore-docker-aks
```

Une fenêtre de navigateur doit ouvrir à l' `http://127.0.0.1:8001` aide d’une vue similaire à celle-ci :

![Affichage dans le navigateur du tableau de bord Kubernetes, montrant les déploiements, les pods, les jeux de réplicas et les services.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubernetes-cluster-information.png)

**Figure 4-54**. Afficher les informations de cluster Kubernetes

Vous disposez à présent de votre application ASP.NET Core, en cours d’exécution dans des conteneurs Linux, et déployée sur un cluster AKS sur Azure.

> [!NOTE]
> Pour plus d’informations sur le déploiement avec Kubernetes, consultez : <https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

> [!div class="step-by-step"]
> [Précédent](set-up-windows-containers-with-powershell.md) 
>  [Suivant](../docker-devops-workflow/index.md)
