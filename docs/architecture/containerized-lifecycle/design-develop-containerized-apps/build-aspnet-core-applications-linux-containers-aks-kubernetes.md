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
# <a name="build-aspnet-core-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="0edda-103">Créez ASP.NET Core applications déployées en tant que conteneurs Linux dans un AKS/Kubernetes Orchestrator</span><span class="sxs-lookup"><span data-stu-id="0edda-103">Build ASP.NET Core applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="0edda-104">Azure Kubernetes Service (AKS) correspond à des services d’orchestrations Kubernetes gérés par Azure qui simplifient la gestion et le déploiement de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="0edda-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="0edda-105">Les principales fonctionnalités AKS sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0edda-105">AKS main features are:</span></span>

- <span data-ttu-id="0edda-106">Plan de contrôle hébergé par Azure</span><span class="sxs-lookup"><span data-stu-id="0edda-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="0edda-107">Mises à niveau automatisées</span><span class="sxs-lookup"><span data-stu-id="0edda-107">Automated upgrades</span></span>
- <span data-ttu-id="0edda-108">Autoréparation</span><span class="sxs-lookup"><span data-stu-id="0edda-108">Self-healing</span></span>
- <span data-ttu-id="0edda-109">Mise à l’échelle configurable par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="0edda-109">User-configurable scaling</span></span>
- <span data-ttu-id="0edda-110">Expérience utilisateur plus simple pour les développeurs et les opérateurs de cluster.</span><span class="sxs-lookup"><span data-stu-id="0edda-110">Simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="0edda-111">Les exemples suivants explorent la création d’une application ASP.NET Core 3,1 qui s’exécute sur Linux et est déployée sur un cluster AKS dans Azure, tandis que le développement s’effectue à l’aide de Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="0edda-111">The following examples explore the creation of an ASP.NET Core 3.1 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2019.</span></span>

## <a name="creating-the-aspnet-core-project-using-visual-studio-2019"></a><span data-ttu-id="0edda-112">Création du projet ASP.NET Core à l’aide de Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="0edda-112">Creating the ASP.NET Core Project using Visual Studio 2019</span></span>

<span data-ttu-id="0edda-113">ASP.NET Core est une plateforme de développement généraliste tenue à jour par Microsoft et la communauté .NET sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="0edda-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="0edda-114">Cette multiplateforme prend en charge Windows, macOS et Linux. Elle peut être utilisée dans des scénarios d’appareil, de cloud et d’incorporation/IoT.</span><span class="sxs-lookup"><span data-stu-id="0edda-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="0edda-115">Cet exemple utilise deux projets simples basés sur des modèles Visual Studio. vous n’avez donc pas besoin de connaissances supplémentaires pour créer l’exemple.</span><span class="sxs-lookup"><span data-stu-id="0edda-115">This example uses a couple of simple projects based on Visual Studio templates, so you don't need much additional knowledge to create the sample.</span></span> <span data-ttu-id="0edda-116">Vous devez uniquement créer le projet à l’aide d’un modèle standard qui comprend tous les éléments pour exécuter un petit projet avec une API REST et une application Web avec les pages Razor, à l’aide de la technologie ASP.NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="0edda-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API and a Web App with Razor pages, using ASP.NET Core 3.1 technology.</span></span>

![Ajoutez une nouvelle fenêtre de projet dans Visual Studio, en sélectionnant Application web ASP.NET Core.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-aspnet-core-application.png)

<span data-ttu-id="0edda-118">**Figure 4-35**.</span><span class="sxs-lookup"><span data-stu-id="0edda-118">**Figure 4-35**.</span></span> <span data-ttu-id="0edda-119">Création d’une application Web ASP.NET Core dans Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="0edda-119">Creating an ASP.NET Core Web Application in Visual Studio 2019.</span></span>

<span data-ttu-id="0edda-120">Pour créer l’exemple de projet dans Visual Studio, sélectionnez **fichier**  >  **nouveau**  >  **projet**, sélectionnez le type de projet **Web** , puis le modèle d' **application Web ASP.net Core** .</span><span class="sxs-lookup"><span data-stu-id="0edda-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project type and then the **ASP.NET Core Web Application** template.</span></span> <span data-ttu-id="0edda-121">Vous pouvez également rechercher le modèle si vous en avez besoin.</span><span class="sxs-lookup"><span data-stu-id="0edda-121">You can also search for the template if you need it.</span></span>

<span data-ttu-id="0edda-122">Entrez ensuite le nom et l’emplacement de l’application, comme indiqué dans l’image suivante.</span><span class="sxs-lookup"><span data-stu-id="0edda-122">Then enter the application name and location as shown in the next image.</span></span>

![Entrez le nom et l’emplacement du projet.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/enter-project-name-and-location.png)

<span data-ttu-id="0edda-124">**Figure 4-36**.</span><span class="sxs-lookup"><span data-stu-id="0edda-124">**Figure 4-36**.</span></span> <span data-ttu-id="0edda-125">Entrez le nom et l’emplacement du projet dans Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="0edda-125">Enter the project name and location in Visual Studio 2019.</span></span>

<span data-ttu-id="0edda-126">Vérifiez que vous avez sélectionné ASP.NET Core 3,1 comme Framework.</span><span class="sxs-lookup"><span data-stu-id="0edda-126">Verify that you've selected ASP.NET Core 3.1 as the framework.</span></span> <span data-ttu-id="0edda-127">.NET Core 3,1 est inclus dans la dernière version de Visual Studio 2019 et est automatiquement installé et configuré lorsque vous installez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0edda-127">.NET Core 3.1 is included in the latest release of Visual Studio 2019 and is automatically installed and configured for you when you install Visual Studio.</span></span>

![Boîte de dialogue Visual Studio permettant de sélectionner le type Application web ASP.NET Core avec l’option API sélectionnée.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-web-api-application.png)

<span data-ttu-id="0edda-129">**Figure 4-37**.</span><span class="sxs-lookup"><span data-stu-id="0edda-129">**Figure 4-37**.</span></span> <span data-ttu-id="0edda-130">Sélection de ASP.NET CORE 3,1 et du type de projet d’API Web</span><span class="sxs-lookup"><span data-stu-id="0edda-130">Selecting ASP.NET CORE 3.1 and Web API project type</span></span>

<span data-ttu-id="0edda-131">Notez que la prise en charge de l’ancrage n’est pas activée pour l’instant. pour l’afficher, vous pouvez le faire après la création du projet.</span><span class="sxs-lookup"><span data-stu-id="0edda-131">Notice Docker support is not enabled now, just to show it can be done after project creation.</span></span>

<span data-ttu-id="0edda-132">Si vous disposez d’une version antérieure de .NET Core, vous pouvez télécharger et installer la version 3,1 à partir de <https://dotnet.microsoft.com/download> .</span><span class="sxs-lookup"><span data-stu-id="0edda-132">If you have any previous version of .NET Core, you can download and install the 3.1 version from <https://dotnet.microsoft.com/download>.</span></span>

<span data-ttu-id="0edda-133">Pour vous montrer que vous pouvez « Dockeriser » votre projet à tout moment, vous allez ajouter la prise en charge de l’ancrage maintenant.</span><span class="sxs-lookup"><span data-stu-id="0edda-133">To show you can "Dockerize" your project at any time, you'll add Docker support now.</span></span> <span data-ttu-id="0edda-134">Cliquez avec le bouton droit sur le nœud du projet dans Explorateur de solutions puis sélectionnez **Ajouter**  >  la**prise en charge** de l’ancrage dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="0edda-134">So right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![Option de menu contextuel pour ajouter la prise en charge de l’ancrage à un projet existant : cliquez avec le bouton droit (sur le projet) > ajoutez > prise en charge de l’ancrage.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-docker-support-to-project.png)

<span data-ttu-id="0edda-136">**Figure 4-38**.</span><span class="sxs-lookup"><span data-stu-id="0edda-136">**Figure 4-38**.</span></span> <span data-ttu-id="0edda-137">Ajout de la prise en charge de l’ancrage à un projet existant</span><span class="sxs-lookup"><span data-stu-id="0edda-137">Adding Docker support to an existing project</span></span>

<span data-ttu-id="0edda-138">Pour terminer l’ajout de la prise en charge de Docker, vous pouvez choisir Windows ou Linux.</span><span class="sxs-lookup"><span data-stu-id="0edda-138">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="0edda-139">Dans ce cas, sélectionnez **Linux**.</span><span class="sxs-lookup"><span data-stu-id="0edda-139">In this case, select **Linux**.</span></span>

![Boîte de dialogue Option permettant de sélectionner le système d’exploitation cible pour Dockerfile.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-linux-docker-support.png)

<span data-ttu-id="0edda-141">**Figure 4-39**.</span><span class="sxs-lookup"><span data-stu-id="0edda-141">**Figure 4-39**.</span></span> <span data-ttu-id="0edda-142">Sélection de conteneurs Linux</span><span class="sxs-lookup"><span data-stu-id="0edda-142">Selecting Linux containers.</span></span>

<span data-ttu-id="0edda-143">Avec ces étapes simples, votre application ASP.NET Core 3,1 s’exécute sur un conteneur Linux.</span><span class="sxs-lookup"><span data-stu-id="0edda-143">With these simple steps, you have your ASP.NET Core 3.1 application running on a Linux container.</span></span>

<span data-ttu-id="0edda-144">De la même façon, vous pouvez également ajouter un projet **webapp** très simple (figure 4-40) pour consommer le point de terminaison de l’API Web, bien que les détails ne soient pas abordés ici.</span><span class="sxs-lookup"><span data-stu-id="0edda-144">In a similar way, you can also add a very simple **WebApp** project (Figure 4-40) to consume the web API endpoint, although the details are not discussed here.</span></span>

<span data-ttu-id="0edda-145">Après cela, vous ajoutez la prise en charge d’Orchestrator pour votre projet **WebApi** , comme illustré ci-dessous, dans l’image 4-40.</span><span class="sxs-lookup"><span data-stu-id="0edda-145">After that, you add orchestrator support for your **WebApi** project as shown next, in image 4-40.</span></span>

![Ajout de la prise en charge d’Orchestrator au projet WebApi](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-orchestrator-support.png)

<span data-ttu-id="0edda-147">**Figure 4-40**.</span><span class="sxs-lookup"><span data-stu-id="0edda-147">**Figure 4-40**.</span></span> <span data-ttu-id="0edda-148">Ajout de la prise en charge d’Orchestrator au projet *WebApi* .</span><span class="sxs-lookup"><span data-stu-id="0edda-148">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="0edda-149">Quand vous choisissez l' `Docker Compose` option, ce qui convient pour le développement local, Visual Studio ajoute le projet dockr-compose, avec les fichiers dockr-compose, comme indiqué dans l’image 4-41.</span><span class="sxs-lookup"><span data-stu-id="0edda-149">When you choose the `Docker Compose` option, which is fine for local development, Visual Studio adds the docker-compose project, with the docker-compose files as shown in image 4-41.</span></span>

![Dockr-compose ajouté à la solution](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-compose-project-in-visual-studio.png)

<span data-ttu-id="0edda-151">**Figure 4-41**.</span><span class="sxs-lookup"><span data-stu-id="0edda-151">**Figure 4-41**.</span></span> <span data-ttu-id="0edda-152">Ajout de la prise en charge d’Orchestrator au projet *WebApi* .</span><span class="sxs-lookup"><span data-stu-id="0edda-152">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="0edda-153">Les fichiers initiaux ajoutés sont similaires à ceux-ci :</span><span class="sxs-lookup"><span data-stu-id="0edda-153">The initial files added are similar to these ones:</span></span>

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

<span data-ttu-id="0edda-154">Pour que votre application s’exécute avec Docker Compose vous devez simplement apporter quelques ajustements à`docker-compose.override.yml`</span><span class="sxs-lookup"><span data-stu-id="0edda-154">To have you app running with Docker Compose you just have to make a few tweaks to `docker-compose.override.yml`</span></span>

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

<span data-ttu-id="0edda-155">Vous pouvez maintenant exécuter votre application avec la touche **F5** , ou en utilisant le bouton de **lecture** , ou la touche **CTRL + F5** , en sélectionnant le projet dockr-compose, comme illustré dans l’image 4-42.</span><span class="sxs-lookup"><span data-stu-id="0edda-155">Now you can run your application with **F5** key, or by using the **Play** button, or the **Ctrl+F5** key, selecting the docker-compose project, as shown in image 4-42.</span></span>

![Exécution du projet dockr-compose avec Visual Studio](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/running-docker-compose-with-visual-studio.png)

<span data-ttu-id="0edda-157">**Figure 4-42**.</span><span class="sxs-lookup"><span data-stu-id="0edda-157">**Figure 4-42**.</span></span> <span data-ttu-id="0edda-158">Ajout de la prise en charge d’Orchestrator au projet *WebApi* .</span><span class="sxs-lookup"><span data-stu-id="0edda-158">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="0edda-159">Lors de l’exécution de l’application dockr-compose comme expliqué, vous disposez des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="0edda-159">When running the docker-compose application as explained, you get:</span></span>

1. <span data-ttu-id="0edda-160">Images générées et conteneurs créés en fonction du fichier dockr-compose.</span><span class="sxs-lookup"><span data-stu-id="0edda-160">The images built and containers created as per the docker-compose file.</span></span>
2. <span data-ttu-id="0edda-161">Le navigateur est ouvert à l’adresse configurée dans la boîte de dialogue Propriétés du `docker-compose` projet.</span><span class="sxs-lookup"><span data-stu-id="0edda-161">The browser open in the address configured in the "Properties" dialog for the `docker-compose` project.</span></span>
3. <span data-ttu-id="0edda-162">La fenêtre de **conteneur** s’ouvre (dans Visual Studio 2019 version 16,4 et versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="0edda-162">The **Container** window open (in Visual Studio 2019 version 16.4 and later).</span></span>
4. <span data-ttu-id="0edda-163">Prise en charge du débogueur pour tous les projets de la solution, comme illustré dans les images suivantes.</span><span class="sxs-lookup"><span data-stu-id="0edda-163">Debugger support for all projects in the solution, as shown in the following images.</span></span>

<span data-ttu-id="0edda-164">Navigateur ouvert :</span><span class="sxs-lookup"><span data-stu-id="0edda-164">Browser opened:</span></span>

![Affichage du navigateur avec l’application Web en cours d’exécution](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/browser-opened.png)

<span data-ttu-id="0edda-166">**Figure 4-43**.</span><span class="sxs-lookup"><span data-stu-id="0edda-166">**Figure 4-43**.</span></span> <span data-ttu-id="0edda-167">Fenêtre de navigateur avec une application exécutée sur plusieurs conteneurs.</span><span class="sxs-lookup"><span data-stu-id="0edda-167">Browser window with an application running on multiple containers.</span></span>

<span data-ttu-id="0edda-168">Fenêtre conteneurs :</span><span class="sxs-lookup"><span data-stu-id="0edda-168">Containers window:</span></span>

![Fenêtre « conteneurs » de Visual Studio](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/visual-studio-containers-window.png)

<span data-ttu-id="0edda-170">**Figure 4-44**.</span><span class="sxs-lookup"><span data-stu-id="0edda-170">**Figure 4-44**.</span></span> <span data-ttu-id="0edda-171">Fenêtre « conteneurs » de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0edda-171">Visual Studio "Containers" window</span></span>

<span data-ttu-id="0edda-172">La fenêtre **conteneurs** vous permet d’afficher les conteneurs en cours d’exécution, de parcourir les images disponibles, d’afficher les variables d’environnement, les journaux et les mappages de port, d’inspecter le système de fichiers, d’attacher un débogueur ou d’ouvrir une fenêtre de terminal à l’intérieur de l’environnement de conteneur.</span><span class="sxs-lookup"><span data-stu-id="0edda-172">The **Containers** window lets you view running containers, browse available images, view environment variables, logs, and port mappings, inspect the filesystem, attach a debugger, or open a terminal window inside the container environment.</span></span>

<span data-ttu-id="0edda-173">Comme vous pouvez le voir, l’intégration entre Visual Studio 2019 et docker est entièrement orientée vers la productivité du développeur.</span><span class="sxs-lookup"><span data-stu-id="0edda-173">As you can see, the integration between Visual Studio 2019 and Docker is completely oriented to the developer's productivity.</span></span>

<span data-ttu-id="0edda-174">Bien entendu, vous pouvez également répertorier les images à l’aide de la `docker images` commande.</span><span class="sxs-lookup"><span data-stu-id="0edda-174">Of course, you can also list the images using the `docker images` command.</span></span> <span data-ttu-id="0edda-175">Vous devez voir les `webapi` `webapp` images et avec les `dev` balises créées par le déploiement automatique de notre projet avec Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="0edda-175">You should see the `webapi` and `webapp` images with the `dev` tags created by the automatic deployment of our project with Visual Studio 2019.</span></span>

```console
docker images
```

![La sortie de console de la commande dockers images affiche une liste avec : dépôt, étiquette, ID d’image, créé (date) et taille.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-images-command.png)

<span data-ttu-id="0edda-177">**Figure 4-45**.</span><span class="sxs-lookup"><span data-stu-id="0edda-177">**Figure 4-45**.</span></span> <span data-ttu-id="0edda-178">Affichage des images Docker</span><span class="sxs-lookup"><span data-stu-id="0edda-178">View of Docker images</span></span>

## <a name="register-the-solution-in-an-azure-container-registry-acr"></a><span data-ttu-id="0edda-179">Inscrire la solution dans une Azure Container Registry (ACR)</span><span class="sxs-lookup"><span data-stu-id="0edda-179">Register the Solution in an Azure Container Registry (ACR)</span></span>

<span data-ttu-id="0edda-180">Vous pouvez télécharger les images vers le [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/), mais vous pouvez également utiliser le hub d’ancrage ou tout autre registre, afin que les images puissent être déployées sur le cluster AKS à partir de ce registre.</span><span class="sxs-lookup"><span data-stu-id="0edda-180">You can upload the images to the [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/), but you could also use Docker Hub or any other registry, so the images can be deployed to the AKS cluster from that registry.</span></span>

### <a name="create-an-acr-instance"></a><span data-ttu-id="0edda-181">Créer une instance ACR</span><span class="sxs-lookup"><span data-stu-id="0edda-181">Create an ACR instance</span></span>

<span data-ttu-id="0edda-182">Exécutez la commande suivante à partir de la commande **AZ CLI**:</span><span class="sxs-lookup"><span data-stu-id="0edda-182">Run the following command from the **az cli**:</span></span>

```powershell
az acr create --name exploredocker --resource-group explore-docker-aks-rg --sku basic --admin-enabled
```

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="0edda-183">Créer l’image en mode Mise en production</span><span class="sxs-lookup"><span data-stu-id="0edda-183">Create the image in Release mode</span></span>

<span data-ttu-id="0edda-184">Vous allez maintenant créer l’image en mode de **mise** en production (prêt pour la production) en passant à la **version Release**, comme illustré dans la figure 4-46, et en exécutant l’application comme vous l’avez fait précédemment.</span><span class="sxs-lookup"><span data-stu-id="0edda-184">You'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-46, and running the application as you did before.</span></span>

![Option de barre d’outils dans Visual Studio pour créer en mode Mise en production.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-release-mode.png)

<span data-ttu-id="0edda-186">**Figure 4-46**.</span><span class="sxs-lookup"><span data-stu-id="0edda-186">**Figure 4-46**.</span></span> <span data-ttu-id="0edda-187">Sélection du mode Mise en production</span><span class="sxs-lookup"><span data-stu-id="0edda-187">Selecting Release Mode</span></span>

<span data-ttu-id="0edda-188">Si vous exécutez la `docker images` commande, vous verrez les deux images créées, une pour `debug` (**dev**) et l’autre pour le `release` mode (le**plus récent**).</span><span class="sxs-lookup"><span data-stu-id="0edda-188">If you execute the `docker images` command, you'll see both images created, one for `debug` (**dev**) and the other for `release` (**latest**) mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="0edda-189">Créer une balise pour l’image</span><span class="sxs-lookup"><span data-stu-id="0edda-189">Create a new Tag for the Image</span></span>

<span data-ttu-id="0edda-190">Chaque image de conteneur doit être marquée avec le `loginServer` nom du registre.</span><span class="sxs-lookup"><span data-stu-id="0edda-190">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="0edda-191">Cette balise est utilisée pour l’acheminement lors de l’envoi des images de conteneur dans un registre d’images.</span><span class="sxs-lookup"><span data-stu-id="0edda-191">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="0edda-192">Vous pouvez voir le nom `loginServer` à partir du portail Azure, en prenant les informations auprès d’Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="0edda-192">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Affichage dans le navigateur du nom du registre de conteneurs Azure, dans le coin supérieur droit.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/loginServer-name.png)

<span data-ttu-id="0edda-194">**Figure 4-47**.</span><span class="sxs-lookup"><span data-stu-id="0edda-194">**Figure 4-47**.</span></span> <span data-ttu-id="0edda-195">Affichage du nom du registre</span><span class="sxs-lookup"><span data-stu-id="0edda-195">View of the name of the Registry</span></span>

<span data-ttu-id="0edda-196">Ou en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="0edda-196">Or by running the following command:</span></span>

```console
az acr list --resource-group <resource-group-name> --query "[].{acrLoginServer:loginServer}" --output table
```

![Sortie de console issue de la commande ci-dessus.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/az-cli-loginServer-name.png)

<span data-ttu-id="0edda-198">**Figure 4-48**.</span><span class="sxs-lookup"><span data-stu-id="0edda-198">**Figure 4-48**.</span></span> <span data-ttu-id="0edda-199">Obtient le nom du Registre à l’aide de la **commande AZ CLI**</span><span class="sxs-lookup"><span data-stu-id="0edda-199">Get the name of the registry using **az cli**</span></span>

<span data-ttu-id="0edda-200">Dans les deux cas, vous obtenez le nom.</span><span class="sxs-lookup"><span data-stu-id="0edda-200">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="0edda-201">Dans notre exemple, `exploredocker.azurecr.io`.</span><span class="sxs-lookup"><span data-stu-id="0edda-201">In our example, `exploredocker.azurecr.io`.</span></span>

<span data-ttu-id="0edda-202">Maintenant vous pouvez baliser l’image, en prenant la dernière (l’image de mise en production), avec la commande :</span><span class="sxs-lookup"><span data-stu-id="0edda-202">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag <image-name>:latest <login-server-name>/<image-name>:v1
```

<span data-ttu-id="0edda-203">Après avoir exécuté la commande `docker tag`, listez les images avec la commande `docker images`. L’image doit apparaître avec la nouvelle balise.</span><span class="sxs-lookup"><span data-stu-id="0edda-203">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![Sortie de console issue de la commande docker images.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/tagged-docker-images-list.png)

<span data-ttu-id="0edda-205">**Figure 4-49**.</span><span class="sxs-lookup"><span data-stu-id="0edda-205">**Figure 4-49**.</span></span> <span data-ttu-id="0edda-206">Vue des images balisées</span><span class="sxs-lookup"><span data-stu-id="0edda-206">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="0edda-207">Pousser (push) l’image vers Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="0edda-207">Push the image into the Azure ACR</span></span>

<span data-ttu-id="0edda-208">Connectez-vous à Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="0edda-208">Log in to the Azure Container Registry</span></span>

```console
az acr login --name exploredocker
```

<span data-ttu-id="0edda-209">Poussez (push) l’image vers Azure Container Registry avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="0edda-209">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push <login-server-name>/<image-name>:v1
```

<span data-ttu-id="0edda-210">Cette commande a besoin de temps pour charger les images, mais vous tient informé pendant le processus.</span><span class="sxs-lookup"><span data-stu-id="0edda-210">This command takes a while uploading the images but gives you feedback in the process.</span></span> <span data-ttu-id="0edda-211">Dans l’image suivante, vous pouvez voir la sortie d’une image terminée et une autre en cours.</span><span class="sxs-lookup"><span data-stu-id="0edda-211">In the following image you can see the output from one image completed and another in progress.</span></span>

![Sortie de la console à partir de la commande dockr push.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/uploading-docker-images-complete.png)

<span data-ttu-id="0edda-213">**Figure 4-50**.</span><span class="sxs-lookup"><span data-stu-id="0edda-213">**Figure 4-50**.</span></span> <span data-ttu-id="0edda-214">Sortie de la console à partir de la commande Push.</span><span class="sxs-lookup"><span data-stu-id="0edda-214">Console output from the push command.</span></span>

<span data-ttu-id="0edda-215">Pour déployer votre application à conteneurs multiples dans votre cluster AKS, vous avez besoin de certains `.yaml` fichiers manifeste qui possèdent la plupart des propriétés extraites des `docker-compose.yml` `docker-compose.override.yml` fichiers et.</span><span class="sxs-lookup"><span data-stu-id="0edda-215">To deploy your multi-container app into your AKS cluster you need some manifest `.yaml` files that have, most of the properties taken from the `docker-compose.yml` and `docker-compose.override.yml` files.</span></span>

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
> <span data-ttu-id="0edda-216">Les `.yml` fichiers précédents activent uniquement les `HTTP` ports, à l’aide du `ASPNETCORE_URLS` paramètre, pour éviter les problèmes liés au certificat manquant dans l’exemple d’application.</span><span class="sxs-lookup"><span data-stu-id="0edda-216">The previous `.yml` files only enable the `HTTP` ports, using the `ASPNETCORE_URLS` parameter, to avoid issues with the missing certificate in the sample app.</span></span>

> [!TIP]
> <span data-ttu-id="0edda-217">Vous pouvez voir comment créer le cluster AKS pour cet exemple dans la section [**Déployer sur Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) de ce guide.</span><span class="sxs-lookup"><span data-stu-id="0edda-217">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

<span data-ttu-id="0edda-218">Maintenant, vous êtes presque prêt à déployer à l’aide de **kubectl**, mais vous devez d’abord récupérer les informations d’identification du cluster AKS avec cette commande :</span><span class="sxs-lookup"><span data-stu-id="0edda-218">Now you're almost ready to deploy using **kubectl**, but first you must get the credentials from the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![Sortie de la console à partir de la commande ci-dessus : fusionnée « explore-docker-AKS » comme contexte actuel dans C:\Users\Miguel.kube\config](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/getting-aks-credentials.png)

<span data-ttu-id="0edda-220">**Figure 4-51**.</span><span class="sxs-lookup"><span data-stu-id="0edda-220">**Figure 4-51**.</span></span> <span data-ttu-id="0edda-221">Obtention des informations d’identification de AKS dans l’environnement kubectl.</span><span class="sxs-lookup"><span data-stu-id="0edda-221">Getting credentials from AKS into the kubectl environment.</span></span>

<span data-ttu-id="0edda-222">Vous devez également autoriser le cluster AKS à extraire des images à partir du ACR, à l’aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="0edda-222">You also have to allow the AKS cluster to pull images from the ACR, using this command:</span></span>

```console
az aks update --name explore-docker-aks --resource-group explore-docker-aks-rg --attach-acr exploredocker
```

<span data-ttu-id="0edda-223">La commande précédente peut prendre quelques minutes.</span><span class="sxs-lookup"><span data-stu-id="0edda-223">The previous command might take a couple of minutes to complete.</span></span> <span data-ttu-id="0edda-224">Ensuite, utilisez la `kubectl apply` commande pour lancer les déploiements, puis `kubectl get all` consultez la liste des objets du cluster.</span><span class="sxs-lookup"><span data-stu-id="0edda-224">Then, use the `kubectl apply` command to launch the deployments, and then `kubectl get all` get list the cluster objects.</span></span>

```console
kubectl apply -f deploy-webapi.yml
kubectl apply -f deploy-webapp.yml

kubectl get all
```

![Sortie de la console à partir des commandes ci-dessus : déploiements appliqués.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubectl-apply-command.png)

<span data-ttu-id="0edda-227">**Figure 4-52**.</span><span class="sxs-lookup"><span data-stu-id="0edda-227">**Figure 4-52**.</span></span> <span data-ttu-id="0edda-228">Déploiement sur Kubernetes</span><span class="sxs-lookup"><span data-stu-id="0edda-228">Deployment to Kubernetes</span></span>

<span data-ttu-id="0edda-229">Vous devrez attendre un certain temps jusqu’à ce que l’équilibrage de charge récupère l’adresse IP externe, en vérifiant `kubectl get services` , puis l’application doit être disponible à cette adresse, comme indiqué dans l’image suivante :</span><span class="sxs-lookup"><span data-stu-id="0edda-229">You'll have to wait a while until the load balancer gets the external IP, checking with `kubectl get services`, and then the application should be available at that address, as shown in the next image:</span></span>

![Vue du navigateur de l’application déployée sur AKS](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/aks-deployed-application.png)

<span data-ttu-id="0edda-231">**Figure 4-53**.</span><span class="sxs-lookup"><span data-stu-id="0edda-231">**Figure 4-53**.</span></span> <span data-ttu-id="0edda-232">Déploiement sur Kubernetes</span><span class="sxs-lookup"><span data-stu-id="0edda-232">Deployment to Kubernetes</span></span>

<span data-ttu-id="0edda-233">Une fois le déploiement terminé, vous pouvez accéder à l' [interface utilisateur Web Kubernetes](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) avec un proxy local, à l’aide d’un tunnel SSH.</span><span class="sxs-lookup"><span data-stu-id="0edda-233">When the deployment completes, you can access the [Kubernetes Web UI](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) with a local proxy, using an ssh tunnel.</span></span>

<span data-ttu-id="0edda-234">Tout d’abord, vous devez créer un ClusterRoleBinding avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="0edda-234">First you must create a ClusterRoleBinding with the following command:</span></span>

```console
kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

<span data-ttu-id="0edda-235">Puis cette commande pour démarrer le proxy :</span><span class="sxs-lookup"><span data-stu-id="0edda-235">And then this command to start the proxy:</span></span>

```console
az aks browse --resource-group exploredocker-aks-rg --name explore-docker-aks
```

<span data-ttu-id="0edda-236">Une fenêtre de navigateur doit ouvrir à l' `http://127.0.0.1:8001` aide d’une vue similaire à celle-ci :</span><span class="sxs-lookup"><span data-stu-id="0edda-236">A browser window should open at `http://127.0.0.1:8001` with a view similar to this one:</span></span>

![Affichage dans le navigateur du tableau de bord Kubernetes, montrant les déploiements, les pods, les jeux de réplicas et les services.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubernetes-cluster-information.png)

<span data-ttu-id="0edda-238">**Figure 4-54**.</span><span class="sxs-lookup"><span data-stu-id="0edda-238">**Figure 4-54**.</span></span> <span data-ttu-id="0edda-239">Afficher les informations de cluster Kubernetes</span><span class="sxs-lookup"><span data-stu-id="0edda-239">View Kubernetes cluster information</span></span>

<span data-ttu-id="0edda-240">Vous disposez à présent de votre application ASP.NET Core, en cours d’exécution dans des conteneurs Linux, et déployée sur un cluster AKS sur Azure.</span><span class="sxs-lookup"><span data-stu-id="0edda-240">Now you have your ASP.NET Core application, running in Linux containers, and deployed to an AKS cluster on Azure.</span></span>

> [!NOTE]
> <span data-ttu-id="0edda-241">Pour plus d’informations sur le déploiement avec Kubernetes, consultez : <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="0edda-241">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="0edda-242">[Précédent](set-up-windows-containers-with-powershell.md) 
>  [Suivant](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="0edda-242">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
