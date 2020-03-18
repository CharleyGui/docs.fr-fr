---
title: Workflow de développement de la boucle interne pour les applications Docker
description: Découvrez le workflow de type « boucle interne » pour le développement des applications Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 3d2fc889d22dbf02acccfbf9231ad98fca224cff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936810"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="fe76f-103">Workflow de développement de la boucle interne pour les applications Docker</span><span class="sxs-lookup"><span data-stu-id="fe76f-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="fe76f-104">Avant de déclencher le workflow de boucle externe qui s’étend sur l’ensemble du cycle DevOps, chaque développeur doit, sur sa propre machine, coder l’application à l’aide de la plateforme et du langage de son choix, puis la tester localement (figure 4-21).</span><span class="sxs-lookup"><span data-stu-id="fe76f-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-21).</span></span> <span data-ttu-id="fe76f-105">Dans tous les cas, les développeurs auront tous un important point en commun, quels que soient le langage, le framework et la plateforme qu’ils auront choisis.</span><span class="sxs-lookup"><span data-stu-id="fe76f-105">But in every case, you'll have an important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="fe76f-106">Dans ce workflow, vous allez également développer et tester des conteneurs Docker, mais localement.</span><span class="sxs-lookup"><span data-stu-id="fe76f-106">In this specific workflow, you're always developing and testing Docker containers, but locally.</span></span>

![Diagramme montrant le concept d’un environnement de dev de boucle intérieure.](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

<span data-ttu-id="fe76f-108">**Figure 4-21**.</span><span class="sxs-lookup"><span data-stu-id="fe76f-108">**Figure 4-21**.</span></span> <span data-ttu-id="fe76f-109">Contexte du développement de boucle interne</span><span class="sxs-lookup"><span data-stu-id="fe76f-109">Inner-loop development context</span></span>

<span data-ttu-id="fe76f-110">Le conteneur ou l’instance d’une image Docker contiennent les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="fe76f-110">The container or instance of a Docker image will contain these components:</span></span>

- <span data-ttu-id="fe76f-111">Un choix de système d’exploitation (par exemple, une distribution Linux ou Windows)</span><span class="sxs-lookup"><span data-stu-id="fe76f-111">An operating system selection (for example, a Linux distribution or Windows)</span></span>

- <span data-ttu-id="fe76f-112">Des fichiers ajoutés par le développeur (par exemple, des binaires d’application)</span><span class="sxs-lookup"><span data-stu-id="fe76f-112">Files added by the developer (for example, app binaries)</span></span>

- <span data-ttu-id="fe76f-113">Des informations de configuration (par exemple, des paramètres d’environnement et des dépendances)</span><span class="sxs-lookup"><span data-stu-id="fe76f-113">Configuration (for example, environment settings and dependencies)</span></span>

- <span data-ttu-id="fe76f-114">Instructions sur les processus que Docker doit exécuter</span><span class="sxs-lookup"><span data-stu-id="fe76f-114">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="fe76f-115">Vous pouvez configurer le workflow du développement de boucle interne qui utilise Docker comme processus (qui est décrit dans la section suivante).</span><span class="sxs-lookup"><span data-stu-id="fe76f-115">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="fe76f-116">Les premières étapes de configuration de l’environnement ne sont pas incluses, car elles ne doivent être effectuées qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="fe76f-116">Consider that the initial steps to set up the environment are not included, because you only need to do it once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="fe76f-117">Création d’une application dans un conteneur Docker à l’aide de Visual Studio Code et de l’interface CLI Docker</span><span class="sxs-lookup"><span data-stu-id="fe76f-117">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="fe76f-118">Les applications se composent de vos propres services et de bibliothèques supplémentaires (dépendances).</span><span class="sxs-lookup"><span data-stu-id="fe76f-118">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="fe76f-119">La figure 4-22 montre les étapes de base que vous devez généralement effectuer lors de la création d’une application Docker, et fournit une description détaillée de chaque étape.</span><span class="sxs-lookup"><span data-stu-id="fe76f-119">Figure 4-22 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![Diagramme montrant les sept étapes qu’il prend pour créer une application conteneurisée.](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

<span data-ttu-id="fe76f-121">**Figure 4-22**.</span><span class="sxs-lookup"><span data-stu-id="fe76f-121">**Figure 4-22**.</span></span> <span data-ttu-id="fe76f-122">Workflow général du cycle de vie des applications Docker conteneurisées dans l’interface CLI Docker</span><span class="sxs-lookup"><span data-stu-id="fe76f-122">High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="fe76f-123">Étape 1 : Commencez à coder dans visual Studio Code et créez votre base d’applications/service initiale</span><span class="sxs-lookup"><span data-stu-id="fe76f-123">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="fe76f-124">Le développement des applications se déroule de façon similaire avec ou sans Docker.</span><span class="sxs-lookup"><span data-stu-id="fe76f-124">The way you develop your application is similar to the way you do it without Docker.</span></span> <span data-ttu-id="fe76f-125">La différence est que, lors du développement, vous déployez et testez l’application ou les services exécutés dans des conteneurs Docker qui sont situés dans votre environnement local (comme une machine virtuelle Linux ou Windows).</span><span class="sxs-lookup"><span data-stu-id="fe76f-125">The difference is that while developing, you're deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="fe76f-126">**Configuration de votre environnement local**</span><span class="sxs-lookup"><span data-stu-id="fe76f-126">**Setting up your local environment**</span></span>

<span data-ttu-id="fe76f-127">Avec les dernières versions de Docker pour Mac et Windows, il n’a jamais été aussi facile de développer des applications Docker, car la configuration est très simple.</span><span class="sxs-lookup"><span data-stu-id="fe76f-127">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

> [!TIP]
> <span data-ttu-id="fe76f-128">Pour obtenir des instructions sur la configuration de Docker sur Windows, accédez à <https://docs.docker.com/docker-for-windows/>.</span><span class="sxs-lookup"><span data-stu-id="fe76f-128">For instructions on setting up Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>
>
><span data-ttu-id="fe76f-129">Pour obtenir des instructions sur la configuration de Docker sur Mac, accédez à <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="fe76f-129">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="fe76f-130">Par ailleurs, vous aurez besoin d’un éditeur de code pour développer votre application tout en utilisant l’interface CLI Docker.</span><span class="sxs-lookup"><span data-stu-id="fe76f-130">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="fe76f-131">Microsoft fournit Visual Studio Code, qui est un éditeur de code léger qui est pris en charge sur Windows, Linux, et macOS, et fournit IntelliSense avec [le soutien de nombreuses langues](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, et la plupart des langues modernes), [débogage](https://code.visualstudio.com/Docs/editor/debugging), [intégration avec Git](https://code.visualstudio.com/Docs/editor/versioncontrol) et [extensions de prise en charge](https://code.visualstudio.com/docs/extensions/overview).</span><span class="sxs-lookup"><span data-stu-id="fe76f-131">Microsoft provides Visual Studio Code, which is a lightweight code editor that's supported on Windows, Linux, and macOS, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="fe76f-132">Cet éditeur est un excellent ajustement pour les développeurs macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="fe76f-132">This editor is a great fit for macOS and Linux developers.</span></span> <span data-ttu-id="fe76f-133">Dans Windows, vous pouvez également utiliser Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fe76f-133">In Windows, you also can use Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="fe76f-134">Pour obtenir des instructions sur l’installation de code studio <https://code.visualstudio.com/docs/setup/setup-overview/>visuel pour Windows, Linux ou macOS, rendez-vous sur .</span><span class="sxs-lookup"><span data-stu-id="fe76f-134">For instructions on installing Visual Studio Code for Windows, Linux, or macOS, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>
>
> <span data-ttu-id="fe76f-135">Pour obtenir des instructions sur la configuration de Docker sur Mac, accédez à <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="fe76f-135">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="fe76f-136">Vous pouvez utiliser l’interface CLI Docker et écrire votre code à l’aide de n’importe quel éditeur de code. Toutefois, l’utilisation de Visual Studio Code avec l’extension Docker facilite la création des fichiers `Dockerfile` et `docker-compose.yml` dans votre espace de travail.</span><span class="sxs-lookup"><span data-stu-id="fe76f-136">You can work with Docker CLI and write your code using any code editor, but using Visual Studio Code with the Docker extension makes it easy to author `Dockerfile` and `docker-compose.yml` files in your workspace.</span></span> <span data-ttu-id="fe76f-137">Vous pouvez également exécuter des tâches et des scripts à partir de l’IDE de Visual Studio Code pour exécuter des commandes Docker à l’aide de l’interface CLI Docker ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="fe76f-137">You can also run tasks and scripts from the Visual Studio Code IDE to execute Docker commands using the Docker CLI underneath.</span></span>

<span data-ttu-id="fe76f-138">L’extension Docker pour VS Code fournit les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="fe76f-138">The Docker extension for VS Code provides the following features:</span></span>

- <span data-ttu-id="fe76f-139">La génération automatique des fichiers `Dockerfile` et `docker-compose.yml`</span><span class="sxs-lookup"><span data-stu-id="fe76f-139">Automatic `Dockerfile` and `docker-compose.yml` file generation</span></span>

- <span data-ttu-id="fe76f-140">La mise en surbrillance de la syntaxe et des info-bulles pour les fichiers `docker-compose.yml` et `Dockerfile`</span><span class="sxs-lookup"><span data-stu-id="fe76f-140">Syntax highlighting and hover tips for `docker-compose.yml` and `Dockerfile` files</span></span>

- <span data-ttu-id="fe76f-141">IntelliSense (saisie semi-automatique) pour les fichiers `Dockerfile` et `docker-compose.yml`</span><span class="sxs-lookup"><span data-stu-id="fe76f-141">IntelliSense (completions) for `Dockerfile` and `docker-compose.yml` files</span></span>

- <span data-ttu-id="fe76f-142">La vérification ou « linting » (erreurs et avertissements) pour les fichiers `Dockerfile`</span><span class="sxs-lookup"><span data-stu-id="fe76f-142">Linting (errors and warnings) for `Dockerfile` files</span></span>

- <span data-ttu-id="fe76f-143">L’intégration de la palette de commandes (F1) pour les commandes Docker les plus courantes</span><span class="sxs-lookup"><span data-stu-id="fe76f-143">Command Palette (F1) integration for the most common Docker commands</span></span>

- <span data-ttu-id="fe76f-144">L’intégration de l’explorateur pour la gestion des images et des conteneurs</span><span class="sxs-lookup"><span data-stu-id="fe76f-144">Explorer integration for managing Images and Containers</span></span>

- <span data-ttu-id="fe76f-145">Le déploiement des images de DockerHub et des registres de conteneur Azure sur Azure App Service</span><span class="sxs-lookup"><span data-stu-id="fe76f-145">Deploy images from DockerHub and Azure Container Registries to Azure App Service</span></span>

<span data-ttu-id="fe76f-146">Pour installer l’extension Docker, appuyez sur Ctrl + Maj + P, tapez `ext install`, puis exécutez la commande Install Extension pour afficher la liste des extensions Marketplace.</span><span class="sxs-lookup"><span data-stu-id="fe76f-146">To install the Docker extension, press Ctrl+Shift+P, type `ext install`, and then run the Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="fe76f-147">Ensuite, tapez **docker** pour filtrer les résultats et sélectionnez l’extension Docker Support, comme illustré dans la figure 4-23.</span><span class="sxs-lookup"><span data-stu-id="fe76f-147">Next, type **docker** to filter the results, and then select the Docker Support extension, as depicted in Figure 4-23.</span></span>

![Vue de l’extension Docker pour VS Code.](./media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

<span data-ttu-id="fe76f-149">**Figure 4-23**.</span><span class="sxs-lookup"><span data-stu-id="fe76f-149">**Figure 4-23**.</span></span> <span data-ttu-id="fe76f-150">Installation de l’extension Docker dans Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="fe76f-150">Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="fe76f-151">Étape 2 : Créez un DockerFile lié à une image existante (environnements de système d’exploitation ou de développement comme .NET Core, Node.js et Ruby)</span><span class="sxs-lookup"><span data-stu-id="fe76f-151">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="fe76f-152">Vous aurez besoin qu’un `DockerFile` soit créé pour chaque image personnalisée et déployé pour chaque conteneur.</span><span class="sxs-lookup"><span data-stu-id="fe76f-152">You'll need a `DockerFile` per custom image to be built and per container to be deployed.</span></span> <span data-ttu-id="fe76f-153">Si votre application est composée d’un seul service personnalisé, vous n’aurez besoin que d’un seul `DockerFile`.</span><span class="sxs-lookup"><span data-stu-id="fe76f-153">If your app is made up of a single custom service, you'll need a single `DockerFile`.</span></span> <span data-ttu-id="fe76f-154">Toutefois, si votre application est composée de plusieurs services (comme dans une architecture de microservices), vous aurez besoin d’un `Dockerfile` par service.</span><span class="sxs-lookup"><span data-stu-id="fe76f-154">But if your app is composed of multiple services (as in a microservices architecture), you'll need one `Dockerfile` per service.</span></span>

<span data-ttu-id="fe76f-155">Le `DockerFile` est généralement placé dans le dossier racine de votre application ou de votre service. Il contient les commandes dont a besoin Docker pour savoir comment configurer et exécuter l’application ou le service.</span><span class="sxs-lookup"><span data-stu-id="fe76f-155">The `DockerFile` is commonly placed in the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="fe76f-156">Vous pouvez créer votre `DockerFile` et l’ajouter à votre projet en même temps que votre code (node.js, .NET Core, etc.). Si vous ne connaissez pas encore bien l’environnement, lisez l’info-bulle suivante.</span><span class="sxs-lookup"><span data-stu-id="fe76f-156">You can create your `DockerFile` and add it to your project along with your code (node.js, .NET Core, etc.), or, if you're new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="fe76f-157">L’extension Docker peut vous guider lors de l’utilisation des fichiers `Dockerfile` et `docker-compose.yml` associés à vos conteneurs Docker.</span><span class="sxs-lookup"><span data-stu-id="fe76f-157">You can use the Docker extension to guide you when using the `Dockerfile` and `docker-compose.yml` files related to your Docker containers.</span></span> <span data-ttu-id="fe76f-158">Vous finirez probablement par écrire ces types de fichiers sans vous aider de cet outil. Toutefois, l’utilisation de l’extension Docker constitue un bon point de départ qui vous permet d’apprendre plus vite.</span><span class="sxs-lookup"><span data-stu-id="fe76f-158">Eventually, you'll probably write these kinds of files without this tool, but using the Docker extension is a good starting point that will accelerate your learning curve.</span></span>

<span data-ttu-id="fe76f-159">Dans la figure 4-24, vous pouvez voir comment le fichier docker-compose est ajouté à l’aide de l’extension Docker pour VS Code.</span><span class="sxs-lookup"><span data-stu-id="fe76f-159">In Figure 4-24, you can see how a docker-compose file is added by using the Docker Extension for VS Code.</span></span>

![Vue de l’extension Docker pour VS Code dans la console.](./media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

<span data-ttu-id="fe76f-161">**Figure 4-24**.</span><span class="sxs-lookup"><span data-stu-id="fe76f-161">**Figure 4-24**.</span></span> <span data-ttu-id="fe76f-162">Fichiers Docker ajoutés à l’aide de la **commande Add Docker files to Workspace**</span><span class="sxs-lookup"><span data-stu-id="fe76f-162">Docker files added using the **Add Docker files to Workspace command**</span></span>

<span data-ttu-id="fe76f-163">Lorsque vous ajoutez un fichier DockerFile, vous devez spécifier quelle image Docker de base vous allez utiliser (par exemple, `FROM mcr.microsoft.com/dotnet/core/aspnet`).</span><span class="sxs-lookup"><span data-stu-id="fe76f-163">When you add a DockerFile, you specify what base Docker image you’ll be using (like using `FROM mcr.microsoft.com/dotnet/core/aspnet`).</span></span> <span data-ttu-id="fe76f-164">En général, vous créez votre image personnalisée sur l’image de base que vous pouvez obtenir dans n’importe quel dépôt officiel du [registre Docker Hub](https://hub.docker.com/) (comme une [image pour .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) ou [pour Node.js](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="fe76f-164">You'll usually build your custom image on top of a base image that you get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) or the one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="fe76f-165">***Utiliser une image Docker officielle existante***</span><span class="sxs-lookup"><span data-stu-id="fe76f-165">***Use an existing official Docker image***</span></span>

<span data-ttu-id="fe76f-166">L’utilisation du dépôt officiel d’une pile de langages avec numéro de version garantit que les mêmes fonctionnalités de langage seront disponibles sur toutes les machines (y compris celles de développement, de test et de production).</span><span class="sxs-lookup"><span data-stu-id="fe76f-166">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="fe76f-167">Voici un exemple de fichier DockerFile pour un conteneur .NET Core :</span><span class="sxs-lookup"><span data-stu-id="fe76f-167">The following is a sample DockerFile for a .NET Core container:</span></span>

```Dockerfile
# Base Docker image to use  
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
  
# Set the Working Directory and files to be copied to the image  
ARG source  
WORKDIR /app  
COPY ${source:-bin/Release/PublishOutput} .  
  
# Configure the listening port to 80 (Internal/Secured port within Docker host)  
EXPOSE 80  
  
# Application entry point  
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

<span data-ttu-id="fe76f-168">Dans ce cas, l’image est basée sur la version 2.2 de l’image Docker ASP.NET Core officielle (multi-architecture pour Linux et Windows), comme dans la ligne `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`</span><span class="sxs-lookup"><span data-stu-id="fe76f-168">In this case, the image is based on version 2.2 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows), as per the line `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="fe76f-169">(pour plus d’informations à ce sujet, consultez la page [Image Docker ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) et la page [Image Docker .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/)).</span><span class="sxs-lookup"><span data-stu-id="fe76f-169">(For more information about this topic, see the [ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) page and the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page).</span></span>

<span data-ttu-id="fe76f-170">Dans le fichier DockerFile, vous pouvez également demander à Docker d’écouter le port TCP que vous utiliserez lors de l’exécution (par exemple, le port 80).</span><span class="sxs-lookup"><span data-stu-id="fe76f-170">In the DockerFile, you can also instruct Docker to listen to the TCP port that you'll use at runtime (such as port 80).</span></span>

<span data-ttu-id="fe76f-171">Vous pouvez spécifier des paramètres de configuration supplémentaires dans le fichier Dockerfile, en fonction du langage et du framework que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="fe76f-171">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="fe76f-172">Par exemple, la ligne `ENTRYPOINT` avec `["dotnet", "MySingleContainerWebApp.dll"]` indique à Docker d’exécuter une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe76f-172">For instance, the `ENTRYPOINT` line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="fe76f-173">Si vous utilisez le SDK et l’interface CLI .NET Core (`dotnet CLI`) pour créer et exécuter l’application .NET, ce paramètre est différent.</span><span class="sxs-lookup"><span data-stu-id="fe76f-173">If you're using the SDK and the .NET Core CLI (`dotnet CLI`) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="fe76f-174">L’essentiel à retenir est que la ligne ENTRYPOINT et certains autres paramètres varient selon le langage et la plateforme choisis pour votre application.</span><span class="sxs-lookup"><span data-stu-id="fe76f-174">The key point here is that the ENTRYPOINT line and other settings depend on the language and platform you choose for your application.</span></span>

> [!TIP]
> <span data-ttu-id="fe76f-175">Pour plus d’informations sur la création d’images Docker pour les applications .NET Core, accédez à <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span><span class="sxs-lookup"><span data-stu-id="fe76f-175">For more information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>
>
> <span data-ttu-id="fe76f-176">Pour savoir comment créer vos propres images, accédez à <https://docs.docker.com/engine/tutorials/dockerimages/>.</span><span class="sxs-lookup"><span data-stu-id="fe76f-176">To learn more about building your own images, go to <https://docs.docker.com/engine/tutorials/dockerimages/>.</span></span>

<span data-ttu-id="fe76f-177">**Utiliser des dépôts d’images multiarch**</span><span class="sxs-lookup"><span data-stu-id="fe76f-177">**Use multi-arch image repositories**</span></span>

<span data-ttu-id="fe76f-178">Dans un dépôt, un même nom d’image peut contenir des variantes de plateforme, comme une image Linux et une image Windows.</span><span class="sxs-lookup"><span data-stu-id="fe76f-178">A single image name in a repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="fe76f-179">Cette fonctionnalité permet aux fournisseurs comme Microsoft (créateurs d’images de base) de créer un dépôt commun pour plusieurs plateformes (Linux et Windows).</span><span class="sxs-lookup"><span data-stu-id="fe76f-179">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is, Linux and Windows).</span></span> <span data-ttu-id="fe76f-180">Par exemple, le dépôt [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) disponible dans le registre Docker Hub assure la prise en charge de Linux et de Windows Nano Server sous le même nom d’image.</span><span class="sxs-lookup"><span data-stu-id="fe76f-180">For example, the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same image name.</span></span>

<span data-ttu-id="fe76f-181">Ainsi, quand vous tirez (pull) une image [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) d’un hôte Windows, la variante Windows est tirée, et quand vous tirez le même nom d’image d’un hôte Linux, la variante Linux est tirée.</span><span class="sxs-lookup"><span data-stu-id="fe76f-181">Pulling the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) image from a Windows host pulls the Windows variant, whereas pulling the same image name from a Linux host pulls the Linux variant.</span></span>

<span data-ttu-id="fe76f-182">***Créer votre image de base à partir de zéro***</span><span class="sxs-lookup"><span data-stu-id="fe76f-182">***Create your base image from scratch***</span></span>

<span data-ttu-id="fe76f-183">Vous pouvez créer votre propre image de base Docker à partir de zéro, comme l’explique [cet article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) tiré du site Docker.</span><span class="sxs-lookup"><span data-stu-id="fe76f-183">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="fe76f-184">Ce scénario n’est probablement pas adapté si vous n’êtes pas encore familiarisé avec Docker. Toutefois, si vous souhaitez définir certains aspects de votre propre image de base, vous pouvez le suivre.</span><span class="sxs-lookup"><span data-stu-id="fe76f-184">This scenario is probably not the best for you if you're just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="fe76f-185">Étape 3 : Créez vos images Docker personnalisées intégrant votre service en elle</span><span class="sxs-lookup"><span data-stu-id="fe76f-185">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="fe76f-186">Vous devrez créer une image pour chaque service personnalisé qui compose votre application.</span><span class="sxs-lookup"><span data-stu-id="fe76f-186">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="fe76f-187">Si votre application n’est composée que d’un seul service ou d’une seule application web, vous n’aurez besoin que d’une seule image.</span><span class="sxs-lookup"><span data-stu-id="fe76f-187">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="fe76f-188">Avec le « workflow de boucle externe DevOps », les images sont créées par un processus de génération automatique dès que vous poussez (push) votre code source vers un dépôt Git (intégration continue). Les images sont donc créées dans cet environnement global à partir de votre code source.</span><span class="sxs-lookup"><span data-stu-id="fe76f-188">When taking into account the "outer-loop DevOps workflow", the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration), so the images will be created in that global environment from your source code.</span></span>
>
> <span data-ttu-id="fe76f-189">Mais avant de choisir l’option de boucle externe, nous devons vérifier que l’application Docker fonctionne correctement, afin de ne pas pousser (push) vers le système de contrôle de code source (Git, etc.) du code qui ne fonctionne pas correctement.</span><span class="sxs-lookup"><span data-stu-id="fe76f-189">But before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>
>
> <span data-ttu-id="fe76f-190">Par conséquent, chaque développeur doit d’abord effectuer l’intégralité du processus de boucle interne pour effectuer des tests localement et continuer à développer jusqu’à ce qu’il souhaite pousser (push) une fonctionnalité complète ou une modification vers le système de contrôle source.</span><span class="sxs-lookup"><span data-stu-id="fe76f-190">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="fe76f-191">Pour créer une image dans votre environnement local à l’aide du fichier DockerFile, vous pouvez utiliser la commande docker build, comme illustré dans la figure 4-25 (vous pouvez également exécuter `docker-compose up --build` pour les applications composées de plusieurs conteneurs ou services).</span><span class="sxs-lookup"><span data-stu-id="fe76f-191">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-25 (you also can run `docker-compose up --build` for applications composed by several containers/services).</span></span>

![Capture d’écran montrant la sortie de la console de la commande de construction docker.](./media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

<span data-ttu-id="fe76f-193">**Figure 4-25**.</span><span class="sxs-lookup"><span data-stu-id="fe76f-193">**Figure 4-25**.</span></span> <span data-ttu-id="fe76f-194">Exécuter docker build</span><span class="sxs-lookup"><span data-stu-id="fe76f-194">Running docker build</span></span>

<span data-ttu-id="fe76f-195">Si vous le souhaitez, au lieu d’exécuter directement `docker build` à partir du dossier du projet, vous pouvez d’abord générer un dossier déployable avec les bibliothèques .NET nécessaires, en exécutant les commandes `dotnet publish` puis `docker build`.</span><span class="sxs-lookup"><span data-stu-id="fe76f-195">Optionally, instead of directly running `docker build` from the project folder, you first can generate a deployable folder with the .NET libraries needed by using the run `dotnet publish` command, and then run `docker build`.</span></span>

<span data-ttu-id="fe76f-196">Cet exemple crée une image Docker portant le nom `cesardl/netcore-webapi-microservice-docker:first` (`:first` est une balise, par exemple, une version).</span><span class="sxs-lookup"><span data-stu-id="fe76f-196">This example creates a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first` (`:first` is a tag, like a specific version).</span></span> <span data-ttu-id="fe76f-197">Vous pouvez effectuer cette étape pour chaque image personnalisée que vous avez besoin de créer pour l’application Docker à plusieurs conteneurs.</span><span class="sxs-lookup"><span data-stu-id="fe76f-197">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="fe76f-198">Vous pouvez rechercher les images de votre dépôt local (votre machine de développement) à l’aide de la commande docker images (voir figure 4-26).</span><span class="sxs-lookup"><span data-stu-id="fe76f-198">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-26.</span></span>

![Sortie de console de la commande docker images, montrant les images existantes.](./media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="fe76f-200">**Figure 4-26**.</span><span class="sxs-lookup"><span data-stu-id="fe76f-200">**Figure 4-26**.</span></span> <span data-ttu-id="fe76f-201">Affichage des images existantes à l’aide de la commande docker images</span><span class="sxs-lookup"><span data-stu-id="fe76f-201">Viewing existing images using docker images</span></span>

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="fe76f-202">Étape 4 : Définissez vos services en docker-compose.yml lors de la construction d’une application Docker composée avec plusieurs services</span><span class="sxs-lookup"><span data-stu-id="fe76f-202">Step 4: Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="fe76f-203">Avec le fichier `docker-compose.yml`, vous pouvez définir un ensemble de services à déployer sous la forme d’une application composée, avec les commandes de déploiement décrites dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="fe76f-203">With the `docker-compose.yml` file, you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="fe76f-204">Créez ce fichier dans le dossier de solution racine ou principal, dont le contenu doit être similaire à celui illustré dans ce fichier `docker-compose.yml` :</span><span class="sxs-lookup"><span data-stu-id="fe76f-204">Create that file in your main or root solution folder; it should have content similar to that shown in this `docker-compose.yml` file:</span></span>

```yml
version: '3.4'
services:
  web:
    build: .
    ports:
     - "81:80"
    volumes:
     - .:/code
    depends_on:
     - redis
  redis:
    image: redis
```

<span data-ttu-id="fe76f-205">Dans ce cas particulier, ce fichier définit deux services : le service web (votre service personnalisé) et le service redis (un service de cache bien connu).</span><span class="sxs-lookup"><span data-stu-id="fe76f-205">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="fe76f-206">Étant donné que chaque service sera déployé comme un conteneur, nous devons utiliser une image Docker concrète pour chacun d’eux.</span><span class="sxs-lookup"><span data-stu-id="fe76f-206">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="fe76f-207">Pour ce service web en particulier, l’image doit :</span><span class="sxs-lookup"><span data-stu-id="fe76f-207">For this particular web service, the image will need to do the following:</span></span>

- <span data-ttu-id="fe76f-208">Être créée à partir du fichier DockerFile dans le répertoire actif</span><span class="sxs-lookup"><span data-stu-id="fe76f-208">Build from the DockerFile in the current directory</span></span>

- <span data-ttu-id="fe76f-209">Transférer le port 80 exposé du conteneur vers le port 81 de la machine hôte</span><span class="sxs-lookup"><span data-stu-id="fe76f-209">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

- <span data-ttu-id="fe76f-210">Monter le répertoire du projet sur l’ordinateur hôte pour coder dans le conteneur, ce qui vous permet de modifier le code sans avoir à recréer l’image</span><span class="sxs-lookup"><span data-stu-id="fe76f-210">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

- <span data-ttu-id="fe76f-211">Lier le service web au service redis</span><span class="sxs-lookup"><span data-stu-id="fe76f-211">Link the web service to the redis service</span></span>

<span data-ttu-id="fe76f-212">Le service redis utilise la [dernière image redis publique](https://hub.docker.com/_/redis/) tirée (pull) du registre Docker Hub.</span><span class="sxs-lookup"><span data-stu-id="fe76f-212">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="fe76f-213">[redis](https://redis.io/) est un système de cache bien connu qui est utilisé pour les applications côté serveur.</span><span class="sxs-lookup"><span data-stu-id="fe76f-213">[redis](https://redis.io/) is a popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="fe76f-214">Étape 5 : Construisez et exécutez votre application Docker</span><span class="sxs-lookup"><span data-stu-id="fe76f-214">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="fe76f-215">Si votre application ne comprend qu’un seul conteneur, vous pouvez l’exécuter en la déployant sur l’hôte Docker (machine virtuelle ou serveur physique).</span><span class="sxs-lookup"><span data-stu-id="fe76f-215">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="fe76f-216">Toutefois, si votre application est composée de plusieurs services, vous devez également la *composer*.</span><span class="sxs-lookup"><span data-stu-id="fe76f-216">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="fe76f-217">Voyons les différentes options.</span><span class="sxs-lookup"><span data-stu-id="fe76f-217">Let's see the different options.</span></span>

<span data-ttu-id="fe76f-218">***Option A : Exécuter un seul conteneur ou service***</span><span class="sxs-lookup"><span data-stu-id="fe76f-218">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="fe76f-219">Vous pouvez exécuter l’image Docker à l’aide de la commande docker run, comme illustré ici :</span><span class="sxs-lookup"><span data-stu-id="fe76f-219">You can run the Docker image by using the docker run command, as shown here:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="fe76f-220">Pour ce déploiement, nous allons rediriger les requêtes envoyées au port 80 vers le port interne 5000.</span><span class="sxs-lookup"><span data-stu-id="fe76f-220">For this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="fe76f-221">À présent, l’application écoute le port externe 80 au niveau de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="fe76f-221">Now the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="fe76f-222">***Option B : Composez et exécutez une application à conteneurs multiples***</span><span class="sxs-lookup"><span data-stu-id="fe76f-222">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="fe76f-223">Dans la plupart des scénarios d’entreprise, une application Docker est composée de plusieurs services.</span><span class="sxs-lookup"><span data-stu-id="fe76f-223">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="fe76f-224">Dans ce cas, vous pouvez exécuter la commande `docker-compose up` (figure 4-27), qui utilise le fichier docker-compose.yml que vous avez peut-être créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="fe76f-224">For these cases, you can run the `docker-compose up` command (Figure 4-27), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="fe76f-225">L’exécution de cette commande déploie une application composée avec tous ses conteneurs.</span><span class="sxs-lookup"><span data-stu-id="fe76f-225">Running this command deploys a composed application with all of its related containers.</span></span>

![Sortie de console de la commande docker-compose up.](./media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

<span data-ttu-id="fe76f-227">**Figure 4-27**.</span><span class="sxs-lookup"><span data-stu-id="fe76f-227">**Figure 4-27**.</span></span> <span data-ttu-id="fe76f-228">Résultats de l’exécution de la commande docker-compose up</span><span class="sxs-lookup"><span data-stu-id="fe76f-228">Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="fe76f-229">Après avoir exécuté `docker-compose up`, déployez votre application et ses conteneurs sur votre hôte Docker (comme illustré à la figure 4-28) dans la représentation de machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="fe76f-229">After you run `docker-compose up`, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-28, in the VM representation.</span></span>

![Machine virtuelle exécutant des applications à plusieurs conteneurs.](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="fe76f-231">**Figure 4-28**.</span><span class="sxs-lookup"><span data-stu-id="fe76f-231">**Figure 4-28**.</span></span> <span data-ttu-id="fe76f-232">Machine virtuelle avec des conteneurs Docker déployés</span><span class="sxs-lookup"><span data-stu-id="fe76f-232">VM with Docker containers deployed</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="fe76f-233">Étape 6 : Testez votre application Docker (localement, dans votre CD VM local)</span><span class="sxs-lookup"><span data-stu-id="fe76f-233">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="fe76f-234">Cette étape varie en fonction de ce que fait votre application.</span><span class="sxs-lookup"><span data-stu-id="fe76f-234">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="fe76f-235">Dans une API web .NET Core de type « Hello World » déployée sous la forme d’un conteneur ou d’un service, vous devez simplement accéder au service en fournissant le port TCP qui est spécifié dans le fichier DockerFile.</span><span class="sxs-lookup"><span data-stu-id="fe76f-235">In a simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="fe76f-236">Pour accéder à votre service si localhost n’est pas activé, vous pouvez trouver l’adresse IP de l’ordinateur à l’aide de cette commande :</span><span class="sxs-lookup"><span data-stu-id="fe76f-236">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

<span data-ttu-id="fe76f-237">Sur l’hôte Docker, ouvrez un navigateur et accédez à ce site. Vous devez y voir votre application ou service s’exécuter, comme illustré à la figure 4-29.</span><span class="sxs-lookup"><span data-stu-id="fe76f-237">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-29.</span></span>

![Vue du navigateur montrant la réponse à localhost/API/values.](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="fe76f-239">**Figure 4-29**.</span><span class="sxs-lookup"><span data-stu-id="fe76f-239">**Figure 4-29**.</span></span> <span data-ttu-id="fe76f-240">Test de l’application Docker localement avec localhost</span><span class="sxs-lookup"><span data-stu-id="fe76f-240">Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="fe76f-241">Notez que le port 80 est utilisé, mais qu’en interne,elle est redirigée vers le port 5000, car c’est ainsi qu’elle a été déployée avec `docker run`, comme nous l’avons vu précédemment.</span><span class="sxs-lookup"><span data-stu-id="fe76f-241">Note that it's using port 80, but internally it's being redirected to port 5000, because that's how it was deployed with `docker run`, as explained earlier.</span></span>

<span data-ttu-id="fe76f-242">Vous pouvez tester cela à l’aide de CURL dans le terminal.</span><span class="sxs-lookup"><span data-stu-id="fe76f-242">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="fe76f-243">Dans une installation Docker sur Windows, l’adresse IP par défaut est 10.0.75.1, comme illustré à la figure 4-30.</span><span class="sxs-lookup"><span data-stu-id="fe76f-243">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-30.</span></span>

![Sortie de console après obtention de http://10.0.75.1/API/values avec CURL](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="fe76f-245">**Figure 4-30**.</span><span class="sxs-lookup"><span data-stu-id="fe76f-245">**Figure 4-30**.</span></span> <span data-ttu-id="fe76f-246">Test de l’application Docker localement avec CURL</span><span class="sxs-lookup"><span data-stu-id="fe76f-246">Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="fe76f-247">**Débogage d’un conteneur exécuté sur Docker**</span><span class="sxs-lookup"><span data-stu-id="fe76f-247">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="fe76f-248">Visual Studio Code prend en charge le débogage Docker si vous utilisez Node.js et d’autres plateformes telles que les conteneurs .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe76f-248">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="fe76f-249">Vous pouvez également déboguer les conteneurs .NET Core ou .NET Framework dans Docker si vous utilisez Visual Studio pour Windows ou Mac, comme décrit dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="fe76f-249">You also can debug .NET Core or .NET Framework containers in Docker when using Visual Studio for Windows or Mac, as described in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="fe76f-250">Pour en savoir plus sur débogage Node.js Conteneurs Docker, voir <https://blog.docker.com/2016/07/live-debugging-docker/> et <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>.</span><span class="sxs-lookup"><span data-stu-id="fe76f-250">To learn more about debugging Node.js Docker containers, see <https://blog.docker.com/2016/07/live-debugging-docker/> and <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fe76f-251">[Suivant précédent](docker-apps-development-environment.md)
>[Next](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="fe76f-251">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>
