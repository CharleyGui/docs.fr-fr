---
title: Créer des applications ASP.NET Core déployées en tant que conteneurs Linux dans des clusters AKS/Kubernetes
description: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft
ms.date: 01/06/2021
ms.openlocfilehash: 7a8f8272ab2faabd0398aeeb2039b6f034b4dedb
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970624"
---
# <a name="build-aspnet-core-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="9c944-103">Créez ASP.NET Core applications déployées en tant que conteneurs Linux dans un AKS/Kubernetes Orchestrator</span><span class="sxs-lookup"><span data-stu-id="9c944-103">Build ASP.NET Core applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="9c944-104">Azure Kubernetes Service (AKS) correspond à des services d’orchestrations Kubernetes gérés par Azure qui simplifient la gestion et le déploiement de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="9c944-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="9c944-105">Les principales fonctionnalités AKS sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="9c944-105">AKS main features are:</span></span>

- <span data-ttu-id="9c944-106">Plan de contrôle hébergé par Azure</span><span class="sxs-lookup"><span data-stu-id="9c944-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="9c944-107">Mises à niveau automatisées</span><span class="sxs-lookup"><span data-stu-id="9c944-107">Automated upgrades</span></span>
- <span data-ttu-id="9c944-108">Autoréparation</span><span class="sxs-lookup"><span data-stu-id="9c944-108">Self-healing</span></span>
- <span data-ttu-id="9c944-109">Mise à l’échelle configurable par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="9c944-109">User-configurable scaling</span></span>
- <span data-ttu-id="9c944-110">Expérience utilisateur plus simple pour les développeurs et les opérateurs de cluster.</span><span class="sxs-lookup"><span data-stu-id="9c944-110">Simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="9c944-111">Les exemples suivants explorent la création d’une application ASP.NET Core 5,0 qui s’exécute sur Linux et est déployée sur un cluster AKS dans Azure, tandis que le développement s’effectue à l’aide de Visual Studio 2019 version 16,8.</span><span class="sxs-lookup"><span data-stu-id="9c944-111">The following examples explore the creation of an ASP.NET Core 5.0 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2019 version 16.8.</span></span>

## <a name="creating-the-aspnet-core-project-using-visual-studio-2019"></a><span data-ttu-id="9c944-112">Création du projet ASP.NET Core à l’aide de Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="9c944-112">Creating the ASP.NET Core Project using Visual Studio 2019</span></span>

<span data-ttu-id="9c944-113">ASP.NET Core est une plateforme de développement généraliste tenue à jour par Microsoft et la communauté .NET sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="9c944-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="9c944-114">Cette multiplateforme prend en charge Windows, macOS et Linux. Elle peut être utilisée dans des scénarios d’appareil, de cloud et d’incorporation/IoT.</span><span class="sxs-lookup"><span data-stu-id="9c944-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="9c944-115">Cet exemple utilise deux projets simples basés sur des modèles Visual Studio. vous n’avez donc pas besoin de connaissances supplémentaires pour créer l’exemple.</span><span class="sxs-lookup"><span data-stu-id="9c944-115">This example uses a couple of simple projects based on Visual Studio templates, so you don't need much additional knowledge to create the sample.</span></span> <span data-ttu-id="9c944-116">Vous devez uniquement créer le projet à l’aide d’un modèle standard qui comprend tous les éléments pour exécuter un petit projet avec une API REST et une application Web avec les pages Razor, à l’aide de la technologie ASP.NET Core 5,0.</span><span class="sxs-lookup"><span data-stu-id="9c944-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API and a Web App with Razor pages, using ASP.NET Core 5.0 technology.</span></span>

![Ajoutez une nouvelle fenêtre de projet dans Visual Studio, en sélectionnant Application web ASP.NET Core.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-aspnet-core-application.png)

<span data-ttu-id="9c944-118">**Figure 4-35**.</span><span class="sxs-lookup"><span data-stu-id="9c944-118">**Figure 4-35**.</span></span> <span data-ttu-id="9c944-119">Création d’une application Web ASP.NET Core dans Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="9c944-119">Creating an ASP.NET Core Web Application in Visual Studio 2019.</span></span>

<span data-ttu-id="9c944-120">Pour créer l’exemple de projet dans Visual Studio, sélectionnez **fichier**  >  **nouveau**  >  **projet**, sélectionnez le type de projet **Web** , puis le modèle d' **application Web ASP.net Core** .</span><span class="sxs-lookup"><span data-stu-id="9c944-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project type and then the **ASP.NET Core Web Application** template.</span></span> <span data-ttu-id="9c944-121">Vous pouvez également rechercher le modèle si vous en avez besoin.</span><span class="sxs-lookup"><span data-stu-id="9c944-121">You can also search for the template if you need it.</span></span>

<span data-ttu-id="9c944-122">Entrez ensuite le nom et l’emplacement de l’application, comme indiqué dans l’image suivante.</span><span class="sxs-lookup"><span data-stu-id="9c944-122">Then enter the application name and location as shown in the next image.</span></span>

![Entrez le nom et l’emplacement du projet.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/enter-project-name-and-location.png)

<span data-ttu-id="9c944-124">**Figure 4-36**.</span><span class="sxs-lookup"><span data-stu-id="9c944-124">**Figure 4-36**.</span></span> <span data-ttu-id="9c944-125">Entrez le nom et l’emplacement du projet dans Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="9c944-125">Enter the project name and location in Visual Studio 2019.</span></span>

<span data-ttu-id="9c944-126">Vérifiez que vous avez sélectionné ASP.NET Core 5,0 comme Framework.</span><span class="sxs-lookup"><span data-stu-id="9c944-126">Verify that you've selected ASP.NET Core 5.0 as the framework.</span></span> <span data-ttu-id="9c944-127">.NET 5,0 est inclus dans la dernière version de Visual Studio 2019 et est automatiquement installé et configuré lorsque vous installez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9c944-127">.NET 5.0 is included in the latest release of Visual Studio 2019 and is automatically installed and configured for you when you install Visual Studio.</span></span>

![Boîte de dialogue Visual Studio permettant de sélectionner le type Application web ASP.NET Core avec l’option API sélectionnée.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-web-api-application.png)

<span data-ttu-id="9c944-129">**Figure 4-37**.</span><span class="sxs-lookup"><span data-stu-id="9c944-129">**Figure 4-37**.</span></span> <span data-ttu-id="9c944-130">Sélection de ASP.NET CORE 5,0 et du type de projet d’API Web</span><span class="sxs-lookup"><span data-stu-id="9c944-130">Selecting ASP.NET CORE 5.0 and Web API project type</span></span>

<span data-ttu-id="9c944-131">Notez que la prise en charge de l’ancrage n’est pas activée pour l’instant. pour l’afficher, vous pouvez le faire après la création du projet.</span><span class="sxs-lookup"><span data-stu-id="9c944-131">Notice Docker support is not enabled now, just to show it can be done after project creation.</span></span>

<span data-ttu-id="9c944-132">Si vous disposez d’une version antérieure de .NET Core, vous pouvez télécharger et installer la version 3,1 à partir de <https://dotnet.microsoft.com/download> .</span><span class="sxs-lookup"><span data-stu-id="9c944-132">If you have any previous version of .NET Core, you can download and install the 3.1 version from <https://dotnet.microsoft.com/download>.</span></span>

<span data-ttu-id="9c944-133">Pour vous montrer que vous pouvez « Dockeriser » votre projet à tout moment, vous allez ajouter la prise en charge de l’ancrage maintenant.</span><span class="sxs-lookup"><span data-stu-id="9c944-133">To show you can "Dockerize" your project at any time, you'll add Docker support now.</span></span> <span data-ttu-id="9c944-134">Cliquez avec le bouton droit sur le nœud du projet dans Explorateur de solutions puis sélectionnez **Ajouter**  >  la **prise en charge** de l’ancrage dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="9c944-134">So right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![Option de menu contextuel pour ajouter la prise en charge de l’ancrage à un projet existant : cliquez avec le bouton droit (sur le projet) > ajoutez > prise en charge de l’ancrage.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-docker-support-to-project.png)

<span data-ttu-id="9c944-136">**Figure 4-38**.</span><span class="sxs-lookup"><span data-stu-id="9c944-136">**Figure 4-38**.</span></span> <span data-ttu-id="9c944-137">Ajout de la prise en charge de l’ancrage à un projet existant</span><span class="sxs-lookup"><span data-stu-id="9c944-137">Adding Docker support to an existing project</span></span>

<span data-ttu-id="9c944-138">Pour terminer l’ajout de la prise en charge de Docker, vous pouvez choisir Windows ou Linux.</span><span class="sxs-lookup"><span data-stu-id="9c944-138">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="9c944-139">Dans ce cas, sélectionnez **Linux**.</span><span class="sxs-lookup"><span data-stu-id="9c944-139">In this case, select **Linux**.</span></span>

![Boîte de dialogue Option permettant de sélectionner le système d’exploitation cible pour Dockerfile.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-linux-docker-support.png)

<span data-ttu-id="9c944-141">**Figure 4-39**.</span><span class="sxs-lookup"><span data-stu-id="9c944-141">**Figure 4-39**.</span></span> <span data-ttu-id="9c944-142">Sélection de conteneurs Linux</span><span class="sxs-lookup"><span data-stu-id="9c944-142">Selecting Linux containers.</span></span>

<span data-ttu-id="9c944-143">Avec ces étapes simples, votre application ASP.NET Core 5,0 s’exécute sur un conteneur Linux.</span><span class="sxs-lookup"><span data-stu-id="9c944-143">With these simple steps, you have your ASP.NET Core 5.0 application running on a Linux container.</span></span>

<span data-ttu-id="9c944-144">De la même façon, vous pouvez également ajouter un projet **webapp** très simple (figure 4-40) pour consommer le point de terminaison de l’API Web, bien que les détails ne soient pas abordés ici.</span><span class="sxs-lookup"><span data-stu-id="9c944-144">In a similar way, you can also add a very simple **WebApp** project (Figure 4-40) to consume the web API endpoint, although the details are not discussed here.</span></span>

<span data-ttu-id="9c944-145">Après cela, vous ajoutez la prise en charge d’Orchestrator pour votre projet **WebApi** , comme illustré ci-dessous, dans l’image 4-40.</span><span class="sxs-lookup"><span data-stu-id="9c944-145">After that, you add orchestrator support for your **WebApi** project as shown next, in image 4-40.</span></span>

![Ajout de la prise en charge d’Orchestrator au projet WebApi](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-orchestrator-support.png)

<span data-ttu-id="9c944-147">**Figure 4-40**.</span><span class="sxs-lookup"><span data-stu-id="9c944-147">**Figure 4-40**.</span></span> <span data-ttu-id="9c944-148">Ajout de la prise en charge d’Orchestrator au projet *WebApi* .</span><span class="sxs-lookup"><span data-stu-id="9c944-148">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="9c944-149">Quand vous choisissez l' `Docker Compose` option, ce qui convient pour le développement local, Visual Studio ajoute le projet dockr-compose, avec les fichiers dockr-compose, comme indiqué dans l’image 4-41.</span><span class="sxs-lookup"><span data-stu-id="9c944-149">When you choose the `Docker Compose` option, which is fine for local development, Visual Studio adds the docker-compose project, with the docker-compose files as shown in image 4-41.</span></span>

![Dockr-compose ajouté à la solution](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-compose-project-in-visual-studio.png)

<span data-ttu-id="9c944-151">**Figure 4-41**.</span><span class="sxs-lookup"><span data-stu-id="9c944-151">**Figure 4-41**.</span></span> <span data-ttu-id="9c944-152">Ajout de la prise en charge d’Orchestrator au projet *WebApi* .</span><span class="sxs-lookup"><span data-stu-id="9c944-152">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="9c944-153">Les fichiers initiaux ajoutés sont similaires à ceux-ci :</span><span class="sxs-lookup"><span data-stu-id="9c944-153">The initial files added are similar to these ones:</span></span>

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

<span data-ttu-id="9c944-154">Pour que votre application s’exécute avec Docker Compose vous devez simplement apporter quelques ajustements à `docker-compose.override.yml`</span><span class="sxs-lookup"><span data-stu-id="9c944-154">To have you app running with Docker Compose you just have to make a few tweaks to `docker-compose.override.yml`</span></span>

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

<span data-ttu-id="9c944-155">Vous pouvez maintenant exécuter votre application à l’aide de la touche **F5** , du bouton de **lecture** ou de la touche **CTRL + F5** , en sélectionnant le projet dockr-compose, comme illustré dans l’image 4-42.</span><span class="sxs-lookup"><span data-stu-id="9c944-155">Now you can run your application with the **F5** key, or by using the **Play** button, or the **Ctrl+F5** key, selecting the docker-compose project, as shown in image 4-42.</span></span>

![Exécution du projet dockr-compose avec Visual Studio](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/running-docker-compose-with-visual-studio.png)

<span data-ttu-id="9c944-157">**Figure 4-42**.</span><span class="sxs-lookup"><span data-stu-id="9c944-157">**Figure 4-42**.</span></span> <span data-ttu-id="9c944-158">Ajout de la prise en charge d’Orchestrator au projet *WebApi* .</span><span class="sxs-lookup"><span data-stu-id="9c944-158">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="9c944-159">Lors de l’exécution de l’application dockr-compose comme expliqué, vous disposez des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="9c944-159">When running the docker-compose application as explained, you get:</span></span>

1. <span data-ttu-id="9c944-160">Images générées et conteneurs créés en fonction du fichier dockr-compose.</span><span class="sxs-lookup"><span data-stu-id="9c944-160">The images built and containers created as per the docker-compose file.</span></span>
2. <span data-ttu-id="9c944-161">Le navigateur est ouvert à l’adresse configurée dans la boîte de dialogue Propriétés du `docker-compose` projet.</span><span class="sxs-lookup"><span data-stu-id="9c944-161">The browser open in the address configured in the "Properties" dialog for the `docker-compose` project.</span></span>
3. <span data-ttu-id="9c944-162">La fenêtre de **conteneur** s’ouvre (dans Visual Studio 2019 version 16,4 et versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="9c944-162">The **Container** window open (in Visual Studio 2019 version 16.4 and later).</span></span>
4. <span data-ttu-id="9c944-163">Prise en charge du débogueur pour tous les projets de la solution, comme illustré dans les images suivantes.</span><span class="sxs-lookup"><span data-stu-id="9c944-163">Debugger support for all projects in the solution, as shown in the following images.</span></span>

<span data-ttu-id="9c944-164">Navigateur ouvert :</span><span class="sxs-lookup"><span data-stu-id="9c944-164">Browser opened:</span></span>

![Affichage du navigateur avec l’application Web en cours d’exécution](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/browser-opened.png)

<span data-ttu-id="9c944-166">**Figure 4-43**.</span><span class="sxs-lookup"><span data-stu-id="9c944-166">**Figure 4-43**.</span></span> <span data-ttu-id="9c944-167">Fenêtre de navigateur avec une application exécutée sur plusieurs conteneurs.</span><span class="sxs-lookup"><span data-stu-id="9c944-167">Browser window with an application running on multiple containers.</span></span>

<span data-ttu-id="9c944-168">Fenêtre conteneurs :</span><span class="sxs-lookup"><span data-stu-id="9c944-168">Containers window:</span></span>

![Fenêtre « conteneurs » de Visual Studio](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/visual-studio-containers-window.png)

<span data-ttu-id="9c944-170">**Figure 4-44**.</span><span class="sxs-lookup"><span data-stu-id="9c944-170">**Figure 4-44**.</span></span> <span data-ttu-id="9c944-171">Fenêtre « conteneurs » de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9c944-171">Visual Studio "Containers" window</span></span>

<span data-ttu-id="9c944-172">La fenêtre **conteneurs** vous permet d’afficher les conteneurs en cours d’exécution, de parcourir les images disponibles, d’afficher les variables d’environnement, les journaux et les mappages de port, d’inspecter le système de fichiers, d’attacher un débogueur ou d’ouvrir une fenêtre de terminal à l’intérieur de l’environnement de conteneur.</span><span class="sxs-lookup"><span data-stu-id="9c944-172">The **Containers** window lets you view running containers, browse available images, view environment variables, logs, and port mappings, inspect the filesystem, attach a debugger, or open a terminal window inside the container environment.</span></span>

<span data-ttu-id="9c944-173">Comme vous pouvez le voir, l’intégration entre Visual Studio 2019 et docker est entièrement orientée vers la productivité du développeur.</span><span class="sxs-lookup"><span data-stu-id="9c944-173">As you can see, the integration between Visual Studio 2019 and Docker is completely oriented to the developer's productivity.</span></span>

<span data-ttu-id="9c944-174">Bien entendu, vous pouvez également répertorier les images à l’aide de la `docker images` commande.</span><span class="sxs-lookup"><span data-stu-id="9c944-174">Of course, you can also list the images using the `docker images` command.</span></span> <span data-ttu-id="9c944-175">Vous devez voir les `webapi` `webapp` images et avec les `dev` balises créées par le déploiement automatique de notre projet avec Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="9c944-175">You should see the `webapi` and `webapp` images with the `dev` tags created by the automatic deployment of our project with Visual Studio 2019.</span></span>

```console
docker images
```

![La sortie de console de la commande dockers images affiche une liste avec : dépôt, étiquette, ID d’image, créé (date) et taille.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-images-command.png)

<span data-ttu-id="9c944-177">**Figure 4-45**.</span><span class="sxs-lookup"><span data-stu-id="9c944-177">**Figure 4-45**.</span></span> <span data-ttu-id="9c944-178">Affichage des images Docker</span><span class="sxs-lookup"><span data-stu-id="9c944-178">View of Docker images</span></span>

## <a name="register-the-solution-in-an-azure-container-registry-acr"></a><span data-ttu-id="9c944-179">Inscrire la solution dans une Azure Container Registry (ACR)</span><span class="sxs-lookup"><span data-stu-id="9c944-179">Register the Solution in an Azure Container Registry (ACR)</span></span>

<span data-ttu-id="9c944-180">Vous pouvez télécharger les images vers le [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/), mais vous pouvez également utiliser le hub d’ancrage ou tout autre registre, afin que les images puissent être déployées sur le cluster AKS à partir de ce registre.</span><span class="sxs-lookup"><span data-stu-id="9c944-180">You can upload the images to the [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/), but you could also use Docker Hub or any other registry, so the images can be deployed to the AKS cluster from that registry.</span></span>

### <a name="create-an-acr-instance"></a><span data-ttu-id="9c944-181">Créer une instance ACR</span><span class="sxs-lookup"><span data-stu-id="9c944-181">Create an ACR instance</span></span>

<span data-ttu-id="9c944-182">Exécutez la commande suivante à partir de la commande **AZ CLI**:</span><span class="sxs-lookup"><span data-stu-id="9c944-182">Run the following command from the **az cli**:</span></span>

```powershell
az acr create --name exploredocker --resource-group explore-docker-aks-rg --sku basic --admin-enabled
```

> [!NOTE]
> <span data-ttu-id="9c944-183">Le nom du registre de conteneurs (par exemple `exploredocker` ,) doit être unique dans Azure et contenir des caractères alphanumériques 5-50.</span><span class="sxs-lookup"><span data-stu-id="9c944-183">The container registry name (e.g `exploredocker`) must be unique within Azure, and contain 5-50 alphanumeric characters.</span></span> <span data-ttu-id="9c944-184">Pour plus d’informations, consultez [créer un registre de conteneurs](/azure/container-registry/container-registry-get-started-azure-cli#create-a-container-registry)</span><span class="sxs-lookup"><span data-stu-id="9c944-184">For more details, refer [Create a container registry](/azure/container-registry/container-registry-get-started-azure-cli#create-a-container-registry)</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="9c944-185">Créer l’image en mode Mise en production</span><span class="sxs-lookup"><span data-stu-id="9c944-185">Create the image in Release mode</span></span>

<span data-ttu-id="9c944-186">Vous allez maintenant créer l’image en mode de **mise** en production (prêt pour la production) en passant à la **version Release**, comme illustré dans la figure 4-46, et en exécutant l’application comme vous l’avez fait précédemment.</span><span class="sxs-lookup"><span data-stu-id="9c944-186">You'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-46, and running the application as you did before.</span></span>

![Option de barre d’outils dans Visual Studio pour créer en mode Mise en production.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-release-mode.png)

<span data-ttu-id="9c944-188">**Figure 4-46**.</span><span class="sxs-lookup"><span data-stu-id="9c944-188">**Figure 4-46**.</span></span> <span data-ttu-id="9c944-189">Sélection du mode Mise en production</span><span class="sxs-lookup"><span data-stu-id="9c944-189">Selecting Release Mode</span></span>

<span data-ttu-id="9c944-190">Si vous exécutez la `docker images` commande, vous verrez les deux images créées, une pour `debug` (**dev**) et l’autre pour le `release` mode (le **plus récent**).</span><span class="sxs-lookup"><span data-stu-id="9c944-190">If you execute the `docker images` command, you'll see both images created, one for `debug` (**dev**) and the other for `release` (**latest**) mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="9c944-191">Créer une balise pour l’image</span><span class="sxs-lookup"><span data-stu-id="9c944-191">Create a new Tag for the Image</span></span>

<span data-ttu-id="9c944-192">Chaque image de conteneur doit être marquée avec le `loginServer` nom du registre.</span><span class="sxs-lookup"><span data-stu-id="9c944-192">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="9c944-193">Cette balise est utilisée pour l’acheminement lors de l’envoi des images de conteneur dans un registre d’images.</span><span class="sxs-lookup"><span data-stu-id="9c944-193">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="9c944-194">Vous pouvez voir le nom `loginServer` à partir du portail Azure, en prenant les informations auprès d’Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="9c944-194">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Affichage dans le navigateur du nom du registre de conteneurs Azure, dans le coin supérieur droit.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/loginServer-name.png)

<span data-ttu-id="9c944-196">**Figure 4-47**.</span><span class="sxs-lookup"><span data-stu-id="9c944-196">**Figure 4-47**.</span></span> <span data-ttu-id="9c944-197">Affichage du nom du registre</span><span class="sxs-lookup"><span data-stu-id="9c944-197">View of the name of the Registry</span></span>

<span data-ttu-id="9c944-198">Ou en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="9c944-198">Or by running the following command:</span></span>

```console
az acr list --resource-group <resource-group-name> --query "[].{acrLoginServer:loginServer}" --output table
```

![Sortie de console issue de la commande ci-dessus.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/az-cli-loginServer-name.png)

<span data-ttu-id="9c944-200">**Figure 4-48**.</span><span class="sxs-lookup"><span data-stu-id="9c944-200">**Figure 4-48**.</span></span> <span data-ttu-id="9c944-201">Obtient le nom du Registre à l’aide de la **commande AZ CLI**</span><span class="sxs-lookup"><span data-stu-id="9c944-201">Get the name of the registry using **az cli**</span></span>

<span data-ttu-id="9c944-202">Dans les deux cas, vous obtenez le nom.</span><span class="sxs-lookup"><span data-stu-id="9c944-202">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="9c944-203">Dans notre exemple, `exploredocker.azurecr.io`.</span><span class="sxs-lookup"><span data-stu-id="9c944-203">In our example, `exploredocker.azurecr.io`.</span></span>

<span data-ttu-id="9c944-204">Maintenant vous pouvez baliser l’image, en prenant la dernière (l’image de mise en production), avec la commande :</span><span class="sxs-lookup"><span data-stu-id="9c944-204">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag <image-name>:latest <login-server-name>/<image-name>:v1
```

<span data-ttu-id="9c944-205">Après avoir exécuté la commande `docker tag`, listez les images avec la commande `docker images`. L’image doit apparaître avec la nouvelle balise.</span><span class="sxs-lookup"><span data-stu-id="9c944-205">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![Sortie de console issue de la commande docker images.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/tagged-docker-images-list.png)

<span data-ttu-id="9c944-207">**Figure 4-49**.</span><span class="sxs-lookup"><span data-stu-id="9c944-207">**Figure 4-49**.</span></span> <span data-ttu-id="9c944-208">Vue des images balisées</span><span class="sxs-lookup"><span data-stu-id="9c944-208">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="9c944-209">Pousser (push) l’image vers Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="9c944-209">Push the image into the Azure ACR</span></span>

<span data-ttu-id="9c944-210">Connectez-vous à Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="9c944-210">Log in to the Azure Container Registry</span></span>

```console
az acr login --name exploredocker
```

<span data-ttu-id="9c944-211">Poussez (push) l’image vers Azure Container Registry avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="9c944-211">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push <login-server-name>/<image-name>:v1
```

<span data-ttu-id="9c944-212">Cette commande a besoin de temps pour charger les images, mais vous tient informé pendant le processus.</span><span class="sxs-lookup"><span data-stu-id="9c944-212">This command takes a while uploading the images but gives you feedback in the process.</span></span> <span data-ttu-id="9c944-213">Dans l’image suivante, vous pouvez voir la sortie d’une image terminée et une autre en cours.</span><span class="sxs-lookup"><span data-stu-id="9c944-213">In the following image, you can see the output from one image completed and another in progress.</span></span>

![Sortie de la console à partir de la commande dockr push.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/uploading-docker-images-complete.png)

<span data-ttu-id="9c944-215">**Figure 4-50**.</span><span class="sxs-lookup"><span data-stu-id="9c944-215">**Figure 4-50**.</span></span> <span data-ttu-id="9c944-216">Sortie de la console à partir de la commande Push.</span><span class="sxs-lookup"><span data-stu-id="9c944-216">Console output from the push command.</span></span>

<span data-ttu-id="9c944-217">Pour déployer votre application à conteneurs multiples dans votre cluster AKS, vous avez besoin de certains `.yaml` fichiers manifeste qui possèdent la plupart des propriétés extraites des `docker-compose.yml` `docker-compose.override.yml` fichiers et.</span><span class="sxs-lookup"><span data-stu-id="9c944-217">To deploy your multi-container app into your AKS cluster you need some manifest `.yaml` files that have, most of the properties taken from the `docker-compose.yml` and `docker-compose.override.yml` files.</span></span>

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
> <span data-ttu-id="9c944-218">Les `.yml` fichiers précédents activent uniquement les `HTTP` ports, à l’aide du `ASPNETCORE_URLS` paramètre, pour éviter les problèmes liés au certificat manquant dans l’exemple d’application.</span><span class="sxs-lookup"><span data-stu-id="9c944-218">The previous `.yml` files only enable the `HTTP` ports, using the `ASPNETCORE_URLS` parameter, to avoid issues with the missing certificate in the sample app.</span></span>

> [!TIP]
> <span data-ttu-id="9c944-219">Vous pouvez voir comment créer le cluster AKS pour cet exemple dans la section [**Déployer sur Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) de ce guide.</span><span class="sxs-lookup"><span data-stu-id="9c944-219">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

<span data-ttu-id="9c944-220">Maintenant, vous êtes presque prêt à déployer à l’aide de **kubectl**, mais vous devez d’abord récupérer les informations d’identification du cluster AKS avec cette commande :</span><span class="sxs-lookup"><span data-stu-id="9c944-220">Now you're almost ready to deploy using **kubectl**, but first you must get the credentials from the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![Sortie de la console à partir de la commande ci-dessus : fusionnée « explore-docker-AKS » comme contexte actuel dans C:\Users\Miguel.kube\config](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/getting-aks-credentials.png)

<span data-ttu-id="9c944-222">**Figure 4-51**.</span><span class="sxs-lookup"><span data-stu-id="9c944-222">**Figure 4-51**.</span></span> <span data-ttu-id="9c944-223">Obtention des informations d’identification de AKS dans l’environnement kubectl.</span><span class="sxs-lookup"><span data-stu-id="9c944-223">Getting credentials from AKS into the kubectl environment.</span></span>

<span data-ttu-id="9c944-224">Vous devez également autoriser le cluster AKS à extraire des images à partir du ACR, à l’aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="9c944-224">You also have to allow the AKS cluster to pull images from the ACR, using this command:</span></span>

```console
az aks update --name explore-docker-aks --resource-group explore-docker-aks-rg --attach-acr exploredocker
```

<span data-ttu-id="9c944-225">La commande précédente peut prendre quelques minutes.</span><span class="sxs-lookup"><span data-stu-id="9c944-225">The previous command might take a couple of minutes to complete.</span></span> <span data-ttu-id="9c944-226">Ensuite, utilisez la `kubectl apply` commande pour lancer les déploiements, puis `kubectl get all` consultez la liste des objets du cluster.</span><span class="sxs-lookup"><span data-stu-id="9c944-226">Then, use the `kubectl apply` command to launch the deployments, and then `kubectl get all` get list the cluster objects.</span></span>

```console
kubectl apply -f deploy-webapi.yml
kubectl apply -f deploy-webapp.yml

kubectl get all
```

![Sortie de la console à partir des commandes ci-dessus : déploiements appliqués.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubectl-apply-command.png)

<span data-ttu-id="9c944-229">**Figure 4-52**.</span><span class="sxs-lookup"><span data-stu-id="9c944-229">**Figure 4-52**.</span></span> <span data-ttu-id="9c944-230">Déploiement sur Kubernetes</span><span class="sxs-lookup"><span data-stu-id="9c944-230">Deployment to Kubernetes</span></span>

<span data-ttu-id="9c944-231">Vous devrez attendre un certain temps jusqu’à ce que l’équilibrage de charge récupère l’adresse IP externe, en vérifiant `kubectl get services` , puis l’application doit être disponible à cette adresse, comme indiqué dans l’image suivante :</span><span class="sxs-lookup"><span data-stu-id="9c944-231">You'll have to wait a while until the load balancer gets the external IP, checking with `kubectl get services`, and then the application should be available at that address, as shown in the next image:</span></span>

![Vue du navigateur de l’application déployée sur AKS](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/aks-deployed-application.png)

<span data-ttu-id="9c944-233">**Figure 4-53**.</span><span class="sxs-lookup"><span data-stu-id="9c944-233">**Figure 4-53**.</span></span> <span data-ttu-id="9c944-234">Déploiement sur Kubernetes</span><span class="sxs-lookup"><span data-stu-id="9c944-234">Deployment to Kubernetes</span></span>

<span data-ttu-id="9c944-235">Une fois le déploiement terminé, vous pouvez accéder à l' [interface utilisateur Web Kubernetes](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) avec un proxy local, à l’aide d’un tunnel SSH.</span><span class="sxs-lookup"><span data-stu-id="9c944-235">When the deployment completes, you can access the [Kubernetes Web UI](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) with a local proxy, using an ssh tunnel.</span></span>

<span data-ttu-id="9c944-236">Tout d’abord, vous devez créer un ClusterRoleBinding avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="9c944-236">First you must create a ClusterRoleBinding with the following command:</span></span>

```console
kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

<span data-ttu-id="9c944-237">Puis cette commande pour démarrer le proxy :</span><span class="sxs-lookup"><span data-stu-id="9c944-237">And then this command to start the proxy:</span></span>

```console
az aks browse --resource-group exploredocker-aks-rg --name explore-docker-aks
```

<span data-ttu-id="9c944-238">Une fenêtre de navigateur doit ouvrir à l' `http://127.0.0.1:8001` aide d’une vue similaire à celle-ci :</span><span class="sxs-lookup"><span data-stu-id="9c944-238">A browser window should open at `http://127.0.0.1:8001` with a view similar to this one:</span></span>

![Affichage dans le navigateur du tableau de bord Kubernetes, montrant les déploiements, les pods, les jeux de réplicas et les services.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubernetes-cluster-information.png)

<span data-ttu-id="9c944-240">**Figure 4-54**.</span><span class="sxs-lookup"><span data-stu-id="9c944-240">**Figure 4-54**.</span></span> <span data-ttu-id="9c944-241">Afficher les informations de cluster Kubernetes</span><span class="sxs-lookup"><span data-stu-id="9c944-241">View Kubernetes cluster information</span></span>

<span data-ttu-id="9c944-242">Vous disposez à présent de votre application ASP.NET Core, en cours d’exécution dans des conteneurs Linux, et déployée sur un cluster AKS sur Azure.</span><span class="sxs-lookup"><span data-stu-id="9c944-242">Now you have your ASP.NET Core application, running in Linux containers, and deployed to an AKS cluster on Azure.</span></span>

> [!NOTE]
> <span data-ttu-id="9c944-243">Pour plus d’informations sur le déploiement avec Kubernetes, consultez : <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="9c944-243">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="9c944-244">[Précédent](set-up-windows-containers-with-powershell.md) 
>  [Suivant](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="9c944-244">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
