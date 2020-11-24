---
title: Workflow de développement de la boucle interne pour les applications Docker
description: En savoir plus sur le flux de travail de développement « boucle interne » pour les applications Dockr.
ms.date: 08/06/2020
ms.openlocfilehash: d66274a64591f79f242c1e8a63951b51d94a9ecd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676528"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="9a046-103">Workflow de développement de la boucle interne pour les applications Docker</span><span class="sxs-lookup"><span data-stu-id="9a046-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="9a046-104">Avant de déclencher le workflow de boucle externe qui s’étend sur l’ensemble du cycle DevOps, chaque développeur doit, sur sa propre machine, coder l’application à l’aide de la plateforme et du langage de son choix, puis la tester localement (figure 4-21).</span><span class="sxs-lookup"><span data-stu-id="9a046-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-21).</span></span> <span data-ttu-id="9a046-105">Dans tous les cas, les développeurs auront tous un important point en commun, quels que soient le langage, le framework et la plateforme qu’ils auront choisis.</span><span class="sxs-lookup"><span data-stu-id="9a046-105">But in every case, you'll have an important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="9a046-106">Dans ce flux de travail spécifique, vous développez et testez toujours des conteneurs dockers dans aucun autre environnement, mais localement.</span><span class="sxs-lookup"><span data-stu-id="9a046-106">In this specific workflow, you're always developing and testing Docker containers in no other environments, but locally.</span></span>

![Diagramme montrant le concept d’un environnement de développement de boucles internes.](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

<span data-ttu-id="9a046-108">**Figure 4-21**.</span><span class="sxs-lookup"><span data-stu-id="9a046-108">**Figure 4-21**.</span></span> <span data-ttu-id="9a046-109">Contexte du développement de boucle interne</span><span class="sxs-lookup"><span data-stu-id="9a046-109">Inner-loop development context</span></span>

<span data-ttu-id="9a046-110">Le conteneur ou l’instance d’une image Docker contiennent les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="9a046-110">The container or instance of a Docker image will contain these components:</span></span>

- <span data-ttu-id="9a046-111">Un choix de système d’exploitation (par exemple, une distribution Linux ou Windows)</span><span class="sxs-lookup"><span data-stu-id="9a046-111">An operating system selection (for example, a Linux distribution or Windows)</span></span>

- <span data-ttu-id="9a046-112">Des fichiers ajoutés par le développeur (par exemple, des binaires d’application)</span><span class="sxs-lookup"><span data-stu-id="9a046-112">Files added by the developer (for example, app binaries)</span></span>

- <span data-ttu-id="9a046-113">Des informations de configuration (par exemple, des paramètres d’environnement et des dépendances)</span><span class="sxs-lookup"><span data-stu-id="9a046-113">Configuration (for example, environment settings and dependencies)</span></span>

- <span data-ttu-id="9a046-114">Instructions sur les processus que Docker doit exécuter</span><span class="sxs-lookup"><span data-stu-id="9a046-114">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="9a046-115">Vous pouvez configurer le workflow du développement de boucle interne qui utilise Docker comme processus (qui est décrit dans la section suivante).</span><span class="sxs-lookup"><span data-stu-id="9a046-115">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="9a046-116">Les premières étapes de configuration de l’environnement ne sont pas incluses, car elles ne doivent être effectuées qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="9a046-116">Consider that the initial steps to set up the environment are not included, because you only need to do it once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="9a046-117">Création d’une application dans un conteneur Docker à l’aide de Visual Studio Code et de l’interface CLI Docker</span><span class="sxs-lookup"><span data-stu-id="9a046-117">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="9a046-118">Les applications se composent de vos propres services et de bibliothèques supplémentaires (dépendances).</span><span class="sxs-lookup"><span data-stu-id="9a046-118">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="9a046-119">La figure 4-22 montre les étapes de base que vous devez généralement effectuer lors de la création d’une application Docker, et fournit une description détaillée de chaque étape.</span><span class="sxs-lookup"><span data-stu-id="9a046-119">Figure 4-22 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![Diagramme montrant les sept étapes nécessaires à la création d’une application en conteneur.](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

<span data-ttu-id="9a046-121">**Figure 4-22**.</span><span class="sxs-lookup"><span data-stu-id="9a046-121">**Figure 4-22**.</span></span> <span data-ttu-id="9a046-122">Workflow général du cycle de vie des applications Docker conteneurisées dans l’interface CLI Docker</span><span class="sxs-lookup"><span data-stu-id="9a046-122">High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="9a046-123">Étape 1 : commencer le codage dans Visual Studio Code et créer votre base de référence d’application/de service initiale</span><span class="sxs-lookup"><span data-stu-id="9a046-123">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="9a046-124">Le développement des applications se déroule de façon similaire avec ou sans Docker.</span><span class="sxs-lookup"><span data-stu-id="9a046-124">The way you develop your application is similar to the way you do it without Docker.</span></span> <span data-ttu-id="9a046-125">La différence est que, lors du développement, vous déployez et testez l’application ou les services exécutés dans des conteneurs Docker qui sont situés dans votre environnement local (comme une machine virtuelle Linux ou Windows).</span><span class="sxs-lookup"><span data-stu-id="9a046-125">The difference is that while developing, you're deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="9a046-126">**Configuration de votre environnement local**</span><span class="sxs-lookup"><span data-stu-id="9a046-126">**Setting up your local environment**</span></span>

<span data-ttu-id="9a046-127">Avec les dernières versions de Desktop Desktop pour Mac et Windows, il est plus facile que jamais de développer des applications Dockr, et l’installation est simple.</span><span class="sxs-lookup"><span data-stu-id="9a046-127">With the latest versions of Docker Desktop for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

> [!TIP]
> <span data-ttu-id="9a046-128">Pour obtenir des instructions sur la configuration de Desktop Dockr pour Windows, consultez <https://docs.docker.com/docker-for-windows/> .</span><span class="sxs-lookup"><span data-stu-id="9a046-128">For instructions on setting up Docker Desktop for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>
>
> <span data-ttu-id="9a046-129">Pour obtenir des instructions sur la configuration de Desktop Dockr pour Mac, consultez <https://docs.docker.com/docker-for-mac/> .</span><span class="sxs-lookup"><span data-stu-id="9a046-129">For instructions on setting up Docker Desktop for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="9a046-130">Par ailleurs, vous aurez besoin d’un éditeur de code pour développer votre application tout en utilisant l’interface CLI Docker.</span><span class="sxs-lookup"><span data-stu-id="9a046-130">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="9a046-131">Microsoft fournit Visual Studio Code, qui est un éditeur de code léger pris en charge sur Windows, Linux et macOS, et fournit à IntelliSense la [prise en charge de nombreux langages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .net, Go, Java, Ruby, Python et les langages les plus modernes), du [débogage](https://code.visualstudio.com/Docs/editor/debugging), [de l’intégration avec git](https://code.visualstudio.com/Docs/editor/versioncontrol) et des [Extensions](https://code.visualstudio.com/docs/extensions/overview).</span><span class="sxs-lookup"><span data-stu-id="9a046-131">Microsoft provides Visual Studio Code, which is a lightweight code editor that's supported on Windows, Linux, and macOS, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="9a046-132">Cet éditeur convient parfaitement aux développeurs macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="9a046-132">This editor is a great fit for macOS and Linux developers.</span></span> <span data-ttu-id="9a046-133">Dans Windows, vous pouvez également utiliser Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9a046-133">In Windows, you also can use Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="9a046-134">Pour obtenir des instructions sur l’installation de Visual Studio Code pour Windows, Linux ou macOS, consultez <https://code.visualstudio.com/docs/setup/setup-overview/> .</span><span class="sxs-lookup"><span data-stu-id="9a046-134">For instructions on installing Visual Studio Code for Windows, Linux, or macOS, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>
>
> <span data-ttu-id="9a046-135">Pour obtenir des instructions sur la configuration de Docker sur Mac, accédez à <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="9a046-135">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="9a046-136">Vous pouvez utiliser l’interface CLI Docker et écrire votre code à l’aide de n’importe quel éditeur de code. Toutefois, l’utilisation de Visual Studio Code avec l’extension Docker facilite la création des fichiers `Dockerfile` et `docker-compose.yml` dans votre espace de travail.</span><span class="sxs-lookup"><span data-stu-id="9a046-136">You can work with Docker CLI and write your code using any code editor, but using Visual Studio Code with the Docker extension makes it easy to author `Dockerfile` and `docker-compose.yml` files in your workspace.</span></span> <span data-ttu-id="9a046-137">Vous pouvez également exécuter des tâches et des scripts à partir de l’IDE de Visual Studio Code pour exécuter des commandes Docker à l’aide de l’interface CLI Docker ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="9a046-137">You can also run tasks and scripts from the Visual Studio Code IDE to execute Docker commands using the Docker CLI underneath.</span></span>

<span data-ttu-id="9a046-138">L’extension Docker pour VS Code fournit les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="9a046-138">The Docker extension for VS Code provides the following features:</span></span>

- <span data-ttu-id="9a046-139">La génération automatique des fichiers `Dockerfile` et `docker-compose.yml`</span><span class="sxs-lookup"><span data-stu-id="9a046-139">Automatic `Dockerfile` and `docker-compose.yml` file generation</span></span>

- <span data-ttu-id="9a046-140">La mise en surbrillance de la syntaxe et des info-bulles pour les fichiers `docker-compose.yml` et `Dockerfile`</span><span class="sxs-lookup"><span data-stu-id="9a046-140">Syntax highlighting and hover tips for `docker-compose.yml` and `Dockerfile` files</span></span>

- <span data-ttu-id="9a046-141">IntelliSense (saisie semi-automatique) pour les fichiers `Dockerfile` et `docker-compose.yml`</span><span class="sxs-lookup"><span data-stu-id="9a046-141">IntelliSense (completions) for `Dockerfile` and `docker-compose.yml` files</span></span>

- <span data-ttu-id="9a046-142">La vérification ou « linting » (erreurs et avertissements) pour les fichiers `Dockerfile`</span><span class="sxs-lookup"><span data-stu-id="9a046-142">Linting (errors and warnings) for `Dockerfile` files</span></span>

- <span data-ttu-id="9a046-143">L’intégration de la palette de commandes (F1) pour les commandes Docker les plus courantes</span><span class="sxs-lookup"><span data-stu-id="9a046-143">Command Palette (F1) integration for the most common Docker commands</span></span>

- <span data-ttu-id="9a046-144">L’intégration de l’explorateur pour la gestion des images et des conteneurs</span><span class="sxs-lookup"><span data-stu-id="9a046-144">Explorer integration for managing Images and Containers</span></span>

- <span data-ttu-id="9a046-145">Le déploiement des images de DockerHub et des registres de conteneur Azure sur Azure App Service</span><span class="sxs-lookup"><span data-stu-id="9a046-145">Deploy images from DockerHub and Azure Container Registries to Azure App Service</span></span>

<span data-ttu-id="9a046-146">Pour installer l’extension Docker, appuyez sur Ctrl + Maj + P, tapez `ext install`, puis exécutez la commande Install Extension pour afficher la liste des extensions Marketplace.</span><span class="sxs-lookup"><span data-stu-id="9a046-146">To install the Docker extension, press Ctrl+Shift+P, type `ext install`, and then run the Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="9a046-147">Ensuite, tapez **docker** pour filtrer les résultats et sélectionnez l’extension Docker Support, comme illustré dans la figure 4-23.</span><span class="sxs-lookup"><span data-stu-id="9a046-147">Next, type **docker** to filter the results, and then select the Docker Support extension, as depicted in Figure 4-23.</span></span>

![Vue de l’extension Docker pour VS Code.](media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

<span data-ttu-id="9a046-149">**Figure 4-23**.</span><span class="sxs-lookup"><span data-stu-id="9a046-149">**Figure 4-23**.</span></span> <span data-ttu-id="9a046-150">Installation de l’extension Docker dans Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="9a046-150">Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="9a046-151">Étape 2 : créer un fichier dockerfile lié à une image existante (environnements de système d’exploitation ou de développement simples tels que .NET Core, Node.js et Ruby)</span><span class="sxs-lookup"><span data-stu-id="9a046-151">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="9a046-152">Vous aurez besoin qu’un `DockerFile` soit créé pour chaque image personnalisée et déployé pour chaque conteneur.</span><span class="sxs-lookup"><span data-stu-id="9a046-152">You'll need a `DockerFile` per custom image to be built and per container to be deployed.</span></span> <span data-ttu-id="9a046-153">Si votre application est composée d’un seul service personnalisé, vous aurez besoin d’un seul `DockerFile` .</span><span class="sxs-lookup"><span data-stu-id="9a046-153">If your app is made up of single custom service, you'll need a single `DockerFile`.</span></span> <span data-ttu-id="9a046-154">Toutefois, si votre application est composée de plusieurs services (comme dans une architecture de microservices), vous aurez besoin d’un `Dockerfile` par service.</span><span class="sxs-lookup"><span data-stu-id="9a046-154">But if your app is composed of multiple services (as in a microservices architecture), you'll need one `Dockerfile` per service.</span></span>

<span data-ttu-id="9a046-155">Le `DockerFile` est généralement placé dans le dossier racine de votre application ou de votre service. Il contient les commandes dont a besoin Docker pour savoir comment configurer et exécuter l’application ou le service.</span><span class="sxs-lookup"><span data-stu-id="9a046-155">The `DockerFile` is commonly placed in the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="9a046-156">Vous pouvez créer votre `DockerFile` et l’ajouter à votre projet en même temps que votre code (node.js, .NET Core, etc.). Si vous ne connaissez pas encore bien l’environnement, lisez l’info-bulle suivante.</span><span class="sxs-lookup"><span data-stu-id="9a046-156">You can create your `DockerFile` and add it to your project along with your code (node.js, .NET Core, etc.), or, if you're new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="9a046-157">L’extension Docker peut vous guider lors de l’utilisation des fichiers `Dockerfile` et `docker-compose.yml` associés à vos conteneurs Docker.</span><span class="sxs-lookup"><span data-stu-id="9a046-157">You can use the Docker extension to guide you when using the `Dockerfile` and `docker-compose.yml` files related to your Docker containers.</span></span> <span data-ttu-id="9a046-158">Vous finirez probablement par écrire ces types de fichiers sans vous aider de cet outil. Toutefois, l’utilisation de l’extension Docker constitue un bon point de départ qui vous permet d’apprendre plus vite.</span><span class="sxs-lookup"><span data-stu-id="9a046-158">Eventually, you'll probably write these kinds of files without this tool, but using the Docker extension is a good starting point that will accelerate your learning curve.</span></span>

<span data-ttu-id="9a046-159">Dans la figure 4-24, vous pouvez voir les étapes permettant d’ajouter les fichiers de l’ancrage à un projet à l’aide de l’extension de l’ancrage pour VS Code :</span><span class="sxs-lookup"><span data-stu-id="9a046-159">In Figure 4-24, you can see the steps to add the docker files to a project by using the Docker Extension for VS Code:</span></span>

1. <span data-ttu-id="9a046-160">Ouvrez la palette de commandes, tapez «**docker**», puis sélectionnez «**Ajouter les fichiers de l’ancreur à l’espace de travail**».</span><span class="sxs-lookup"><span data-stu-id="9a046-160">Open the command palette, type "**docker**" and select "**Add Docker Files to Workspace**".</span></span>
2. <span data-ttu-id="9a046-161">Sélectionner une plateforme d’application (ASP.NET Core)</span><span class="sxs-lookup"><span data-stu-id="9a046-161">Select Application Platform (ASP.NET Core)</span></span>
3. <span data-ttu-id="9a046-162">Sélectionner le système d’exploitation (Linux)</span><span class="sxs-lookup"><span data-stu-id="9a046-162">Select Operating System (Linux)</span></span>
4. <span data-ttu-id="9a046-163">Inclure les fichiers Docker Compose facultatifs</span><span class="sxs-lookup"><span data-stu-id="9a046-163">Include optional Docker Compose files</span></span>
5. <span data-ttu-id="9a046-164">Entrer les ports à publier (80, 443)</span><span class="sxs-lookup"><span data-stu-id="9a046-164">Enter ports to publish (80, 443)</span></span>
6. <span data-ttu-id="9a046-165">Sélectionner le projet</span><span class="sxs-lookup"><span data-stu-id="9a046-165">Select the project</span></span>

![Procédure d’ajout de fichiers de l’ancrage avec l’extension de l’amarrage](media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

<span data-ttu-id="9a046-167">**Figure 4-24**.</span><span class="sxs-lookup"><span data-stu-id="9a046-167">**Figure 4-24**.</span></span> <span data-ttu-id="9a046-168">Fichiers de l’arrimeur ajoutés à l’aide de la commande **Ajouter des fichiers de l’ancrage à l’espace de travail**</span><span class="sxs-lookup"><span data-stu-id="9a046-168">Docker files added using the **Add Docker files to Workspace** command</span></span>

<span data-ttu-id="9a046-169">Lorsque vous ajoutez un fichier dockerfile, vous spécifiez l’image de base que vous utiliserez (comme avec `FROM mcr.microsoft.com/dotnet/aspnet` ).</span><span class="sxs-lookup"><span data-stu-id="9a046-169">When you add a DockerFile, you specify what base Docker image you'll be using (like using `FROM mcr.microsoft.com/dotnet/aspnet`).</span></span> <span data-ttu-id="9a046-170">En général, vous créez votre image personnalisée sur l’image de base que vous pouvez obtenir dans n’importe quel dépôt officiel du [registre Docker Hub](https://hub.docker.com/) (comme une [image pour .NET Core](https://hub.docker.com/_/microsoft-dotnet/) ou [pour Node.js](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="9a046-170">You'll usually build your custom image on top of a base image that you get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/_/microsoft-dotnet/) or the one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

> [!TIP]
> <span data-ttu-id="9a046-171">Vous devez répéter cette procédure pour chaque projet dans votre application.</span><span class="sxs-lookup"><span data-stu-id="9a046-171">You'll have to repeat this procedure for every project in your application.</span></span> <span data-ttu-id="9a046-172">Toutefois, l’extension demandera de remplacer le fichier d’ancrage-compose généré après la première fois.</span><span class="sxs-lookup"><span data-stu-id="9a046-172">However, the extension will ask to overwrite the generated docker-compose file after the first time.</span></span> <span data-ttu-id="9a046-173">Vous devez répondre à ne pas le remplacer. l’extension crée donc des fichiers dockr-compose distincts, que vous pouvez ensuite fusionner manuellement, avant d’exécuter dockr-compose.</span><span class="sxs-lookup"><span data-stu-id="9a046-173">You should reply to not overwrite it, so the extension creates separate docker-compose files, that you can then merge by hand, prior to running docker-compose.</span></span>

<span data-ttu-id="9a046-174">**_Utiliser une image officielle de l’Ancreur existante_**</span><span class="sxs-lookup"><span data-stu-id="9a046-174">**_Use an existing official Docker image_**</span></span>

<span data-ttu-id="9a046-175">L’utilisation du dépôt officiel d’une pile de langages avec numéro de version garantit que les mêmes fonctionnalités de langage seront disponibles sur toutes les machines (y compris celles de développement, de test et de production).</span><span class="sxs-lookup"><span data-stu-id="9a046-175">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="9a046-176">Voici un exemple de fichier DockerFile pour un conteneur .NET Core :</span><span class="sxs-lookup"><span data-stu-id="9a046-176">The following is a sample DockerFile for a .NET Core container:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
WORKDIR /src
COPY ["src/WebApi/WebApi.csproj", "src/WebApi/"]
RUN dotnet restore "src/WebApi/WebApi.csproj"
COPY . .
WORKDIR "/src/src/WebApi"
RUN dotnet build "WebApi.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApi.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApi.dll"]
```

<span data-ttu-id="9a046-177">Dans ce cas, l’image est basée sur la version 3,1 de l’image officielle de l’Ancreur ASP.NET Core (multi-arch pour Linux et Windows), conformément à la ligne `FROM mcr.microsoft.com/dotnet/aspnet:3.1` .</span><span class="sxs-lookup"><span data-stu-id="9a046-177">In this case, the image is based on version 3.1 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows), as per the line `FROM mcr.microsoft.com/dotnet/aspnet:3.1`.</span></span> <span data-ttu-id="9a046-178">(pour plus d’informations à ce sujet, consultez la page [Image Docker ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-aspnet/) et la page [Image Docker .NET Core](https://hub.docker.com/_/microsoft-dotnet/)).</span><span class="sxs-lookup"><span data-stu-id="9a046-178">(For more information about this topic, see the [ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-aspnet/) page and the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet/) page).</span></span>

<span data-ttu-id="9a046-179">Dans le fichier dockerfile, vous pouvez également demander à Dockr d’écouter le port TCP que vous allez utiliser lors de l’exécution (par exemple, le port 80 ou 443).</span><span class="sxs-lookup"><span data-stu-id="9a046-179">In the DockerFile, you can also instruct Docker to listen to the TCP port that you'll use at runtime (such as port 80 or 443).</span></span>

<span data-ttu-id="9a046-180">Vous pouvez spécifier des paramètres de configuration supplémentaires dans le fichier Dockerfile, en fonction du langage et du framework que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="9a046-180">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="9a046-181">Par exemple, la ligne `ENTRYPOINT` avec `["dotnet", "WebMvcApplication.dll"]` indique à Docker d’exécuter une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a046-181">For instance, the `ENTRYPOINT` line with `["dotnet", "WebMvcApplication.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="9a046-182">Si vous utilisez le SDK et l’interface CLI .NET Core (`dotnet CLI`) pour créer et exécuter l’application .NET, ce paramètre est différent.</span><span class="sxs-lookup"><span data-stu-id="9a046-182">If you're using the SDK and the .NET Core CLI (`dotnet CLI`) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="9a046-183">L’essentiel à retenir est que la ligne ENTRYPOINT et certains autres paramètres varient selon le langage et la plateforme choisis pour votre application.</span><span class="sxs-lookup"><span data-stu-id="9a046-183">The key point here is that the ENTRYPOINT line and other settings depend on the language and platform you choose for your application.</span></span>

> [!TIP]
> <span data-ttu-id="9a046-184">Pour plus d’informations sur la création d’images Docker pour les applications .NET Core, accédez à <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span><span class="sxs-lookup"><span data-stu-id="9a046-184">For more information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>
>
> <span data-ttu-id="9a046-185">Pour savoir comment créer vos propres images, accédez à <https://docs.docker.com/engine/tutorials/dockerimages/>.</span><span class="sxs-lookup"><span data-stu-id="9a046-185">To learn more about building your own images, go to <https://docs.docker.com/engine/tutorials/dockerimages/>.</span></span>

<span data-ttu-id="9a046-186">**Utiliser des dépôts d’images multiarch**</span><span class="sxs-lookup"><span data-stu-id="9a046-186">**Use multi-arch image repositories**</span></span>

<span data-ttu-id="9a046-187">Dans un dépôt, un même nom d’image peut contenir des variantes de plateforme, comme une image Linux et une image Windows.</span><span class="sxs-lookup"><span data-stu-id="9a046-187">A single image name in a repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="9a046-188">Cette fonctionnalité permet aux fournisseurs comme Microsoft (créateurs d’images de base) de créer un dépôt commun pour plusieurs plateformes (Linux et Windows).</span><span class="sxs-lookup"><span data-stu-id="9a046-188">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is, Linux and Windows).</span></span> <span data-ttu-id="9a046-189">Par exemple, le dépôt [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) disponible dans le registre Docker Hub assure la prise en charge de Linux et de Windows Nano Server sous le même nom d’image.</span><span class="sxs-lookup"><span data-stu-id="9a046-189">For example, the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same image name.</span></span>

<span data-ttu-id="9a046-190">Ainsi, quand vous tirez (pull) une image [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) d’un hôte Windows, la variante Windows est tirée, et quand vous tirez le même nom d’image d’un hôte Linux, la variante Linux est tirée.</span><span class="sxs-lookup"><span data-stu-id="9a046-190">Pulling the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) image from a Windows host pulls the Windows variant, whereas pulling the same image name from a Linux host pulls the Linux variant.</span></span>

<span data-ttu-id="9a046-191">**_Créer votre image de base à partir de zéro_**</span><span class="sxs-lookup"><span data-stu-id="9a046-191">**_Create your base image from scratch_**</span></span>

<span data-ttu-id="9a046-192">Vous pouvez créer votre propre image de base Docker à partir de zéro, comme l’explique [cet article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) tiré du site Docker.</span><span class="sxs-lookup"><span data-stu-id="9a046-192">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="9a046-193">Ce scénario n’est probablement pas adapté si vous n’êtes pas encore familiarisé avec Docker. Toutefois, si vous souhaitez définir certains aspects de votre propre image de base, vous pouvez le suivre.</span><span class="sxs-lookup"><span data-stu-id="9a046-193">This scenario is probably not the best for you if you're just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="9a046-194">Étape 3 : créer vos images d’ancrage personnalisées incorporant votre service dans celui-ci</span><span class="sxs-lookup"><span data-stu-id="9a046-194">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="9a046-195">Vous devrez créer une image pour chaque service personnalisé qui compose votre application.</span><span class="sxs-lookup"><span data-stu-id="9a046-195">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="9a046-196">Si votre application n’est composée que d’un seul service ou d’une seule application web, vous n’aurez besoin que d’une seule image.</span><span class="sxs-lookup"><span data-stu-id="9a046-196">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="9a046-197">Avec le « workflow de boucle externe DevOps », les images sont créées par un processus de génération automatique dès que vous poussez (push) votre code source vers un dépôt Git (intégration continue). Les images sont donc créées dans cet environnement global à partir de votre code source.</span><span class="sxs-lookup"><span data-stu-id="9a046-197">When taking into account the "outer-loop DevOps workflow", the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration), so the images will be created in that global environment from your source code.</span></span>
>
> <span data-ttu-id="9a046-198">Mais avant de passer à l’itinéraire de la boucle externe, vous devez vous assurer que l’application de l’arrimeur fonctionne correctement pour ne pas envoyer du code qui risque de ne pas fonctionner correctement dans le système de contrôle de code source (git, etc.).</span><span class="sxs-lookup"><span data-stu-id="9a046-198">But before you consider going to that outer-loop route, you need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>
>
> <span data-ttu-id="9a046-199">Par conséquent, chaque développeur doit d’abord effectuer l’intégralité du processus de boucle interne pour effectuer des tests localement et continuer à développer jusqu’à ce qu’il souhaite pousser (push) une fonctionnalité complète ou une modification vers le système de contrôle source.</span><span class="sxs-lookup"><span data-stu-id="9a046-199">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="9a046-200">Pour créer une image dans votre environnement local et à l’aide de fichier dockerfile, vous pouvez utiliser la commande dockr Build, comme le montre la figure 4-25, car elle balise déjà l’image pour vous et génère les images pour tous les services de l’application avec une commande simple.</span><span class="sxs-lookup"><span data-stu-id="9a046-200">To create an image in your local environment and using the DockerFile, you can use the docker build command, as shown in Figure 4-25, because it already tags the image for you and builds the images for all services in the application with a simple command.</span></span>

![Capture d’écran montrant la sortie de la console de la commande dockr-compose Build.](media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

<span data-ttu-id="9a046-202">**Figure 4-25**.</span><span class="sxs-lookup"><span data-stu-id="9a046-202">**Figure 4-25**.</span></span> <span data-ttu-id="9a046-203">Exécuter docker build</span><span class="sxs-lookup"><span data-stu-id="9a046-203">Running docker build</span></span>

<span data-ttu-id="9a046-204">Si vous le souhaitez, au lieu d’exécuter directement `docker build` à partir du dossier du projet, vous pouvez d’abord générer un dossier déployable avec les bibliothèques .NET nécessaires, en exécutant les commandes `dotnet publish` puis `docker build`.</span><span class="sxs-lookup"><span data-stu-id="9a046-204">Optionally, instead of directly running `docker build` from the project folder, you first can generate a deployable folder with the .NET libraries needed by using the run `dotnet publish` command, and then run `docker build`.</span></span>

<span data-ttu-id="9a046-205">Cet exemple crée une image Docker portant le nom `explore-docker-vscode/webapi:latest` (`:latest` est une balise, par exemple, une version).</span><span class="sxs-lookup"><span data-stu-id="9a046-205">This example creates a Docker image with the name `explore-docker-vscode/webapi:latest` (`:latest` is a tag, like a specific version).</span></span> <span data-ttu-id="9a046-206">Vous pouvez effectuer cette étape pour chaque image personnalisée que vous avez besoin de créer pour l’application Docker à plusieurs conteneurs.</span><span class="sxs-lookup"><span data-stu-id="9a046-206">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span> <span data-ttu-id="9a046-207">Toutefois, nous verrons dans la section suivante qu’il est plus facile de le faire à l’aide de `docker-compose` .</span><span class="sxs-lookup"><span data-stu-id="9a046-207">However, we'll see in the next section that it's easier to do this using `docker-compose`.</span></span>

<span data-ttu-id="9a046-208">Vous pouvez rechercher les images existantes dans votre dépôt local (votre ordinateur de développement) à l’aide de la `docker images` commande, comme illustré dans la Figure 4-26.</span><span class="sxs-lookup"><span data-stu-id="9a046-208">You can find the existing images in your local repository (your development machine) by using the `docker images` command, as illustrated in Figure 4-26.</span></span>

![Sortie de console de la commande docker images, montrant les images existantes.](media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="9a046-210">**Figure 4-26**.</span><span class="sxs-lookup"><span data-stu-id="9a046-210">**Figure 4-26**.</span></span> <span data-ttu-id="9a046-211">Affichage des images existantes à l’aide de la commande docker images</span><span class="sxs-lookup"><span data-stu-id="9a046-211">Viewing existing images using docker images</span></span>

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="9a046-212">Étape 4 : définir vos services dans docker-compose. yml lors de la création d’une application d’ancrage composée avec plusieurs services</span><span class="sxs-lookup"><span data-stu-id="9a046-212">Step 4: Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="9a046-213">Avec le fichier `docker-compose.yml`, vous pouvez définir un ensemble de services à déployer sous la forme d’une application composée, avec les commandes de déploiement décrites dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="9a046-213">With the `docker-compose.yml` file, you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="9a046-214">Créez ce fichier dans le dossier de solution racine ou principal, dont le contenu doit être similaire à celui illustré dans ce fichier `docker-compose.yml` :</span><span class="sxs-lookup"><span data-stu-id="9a046-214">Create that file in your main or root solution folder; it should have content similar to that shown in this `docker-compose.yml` file:</span></span>

```yml
version: "3.4"

services:
  webapi:
    image: webapi
    build:
      context: .
      dockerfile: src/WebApi/Dockerfile
    ports:
      - 51080:80
    depends_on:
      - redis
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80

  webapp:
    image: webapp
    build:
      context: .
      dockerfile: src/WebApp/Dockerfile
    ports:
      - 50080:80
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80
      - WebApiBaseAddress=http://webapi

  redis:
    image: redis
```

<span data-ttu-id="9a046-215">Dans ce cas particulier, ce fichier définit trois services : le service API Web (votre service personnalisé), une application Web et le service ReDim (un service de cache connu).</span><span class="sxs-lookup"><span data-stu-id="9a046-215">In this particular case, this file defines three services: the web API service (your custom service), a web application, and the Redis service (a popular cache service).</span></span> <span data-ttu-id="9a046-216">Chaque service sera déployé en tant que conteneur. vous devez donc utiliser une image d’ancrage concrète pour chacun d’entre eux.</span><span class="sxs-lookup"><span data-stu-id="9a046-216">Each service will be deployed as a container, so you need to use a concrete Docker image for each.</span></span> <span data-ttu-id="9a046-217">Pour cette application particulière :</span><span class="sxs-lookup"><span data-stu-id="9a046-217">For this particular application:</span></span>

- <span data-ttu-id="9a046-218">Le service API Web est créé à partir de fichier dockerfile dans le `src/WebApi/Dockerfile` répertoire.</span><span class="sxs-lookup"><span data-stu-id="9a046-218">The web API service is built from the DockerFile in the `src/WebApi/Dockerfile` directory.</span></span>

- <span data-ttu-id="9a046-219">Le port hôte 51080 est transféré vers le port exposé 80 sur le `webapi` conteneur.</span><span class="sxs-lookup"><span data-stu-id="9a046-219">The host port 51080 is forwarded to the exposed port 80 on the `webapi` container.</span></span>

- <span data-ttu-id="9a046-220">Le service API Web dépend du service ReDim</span><span class="sxs-lookup"><span data-stu-id="9a046-220">The web API service depends on the Redis service</span></span>

- <span data-ttu-id="9a046-221">L’application Web accède au service API Web à l’aide de l’adresse interne : `http://webapi` .</span><span class="sxs-lookup"><span data-stu-id="9a046-221">The web application accesses the web API service using the internal address: `http://webapi`.</span></span>

- <span data-ttu-id="9a046-222">Le service ReDim utilise la [dernière image des redims publics](https://hub.docker.com/_/redis/) extraite du Registre du Hub de l’ancrage.</span><span class="sxs-lookup"><span data-stu-id="9a046-222">The Redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="9a046-223">[Redims](https://redis.io/) est un système de cache populaires pour les applications côté serveur.</span><span class="sxs-lookup"><span data-stu-id="9a046-223">[Redis](https://redis.io/) is a popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="9a046-224">Étape 5 : générer et exécuter votre application Dockr</span><span class="sxs-lookup"><span data-stu-id="9a046-224">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="9a046-225">Si votre application ne comprend qu’un seul conteneur, vous pouvez l’exécuter en la déployant sur l’hôte Docker (machine virtuelle ou serveur physique).</span><span class="sxs-lookup"><span data-stu-id="9a046-225">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="9a046-226">Toutefois, si votre application est composée de plusieurs services, vous devez également la _composer_.</span><span class="sxs-lookup"><span data-stu-id="9a046-226">However, if your app is made up of multiple services, you need to _compose it_, too.</span></span> <span data-ttu-id="9a046-227">Voyons les différentes options.</span><span class="sxs-lookup"><span data-stu-id="9a046-227">Let's see the different options.</span></span>

<span data-ttu-id="9a046-228">**_Option A : exécuter un seul conteneur ou service_**</span><span class="sxs-lookup"><span data-stu-id="9a046-228">**_Option A: Run a single container or service_**</span></span>

<span data-ttu-id="9a046-229">Vous pouvez exécuter l’image Docker à l’aide de la commande docker run, comme illustré ici :</span><span class="sxs-lookup"><span data-stu-id="9a046-229">You can run the Docker image by using the docker run command, as shown here:</span></span>

```console
docker run -t -d -p 50080:80 explore-docker-vscode/webapp:latest
```

<span data-ttu-id="9a046-230">Pour ce déploiement particulier, nous allons rediriger les demandes envoyées au port 50080 sur l’hôte vers le port interne 80.</span><span class="sxs-lookup"><span data-stu-id="9a046-230">For this particular deployment, we'll be redirecting requests sent to port 50080 on the host to the internal port 80.</span></span>

<span data-ttu-id="9a046-231">**_Option B : composer et exécuter une application à plusieurs conteneurs_**</span><span class="sxs-lookup"><span data-stu-id="9a046-231">**_Option B: Compose and run a multiple-container application_**</span></span>

<span data-ttu-id="9a046-232">Dans la plupart des scénarios d’entreprise, une application Docker est composée de plusieurs services.</span><span class="sxs-lookup"><span data-stu-id="9a046-232">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="9a046-233">Dans ce cas, vous pouvez exécuter la `docker-compose up` commande (Figure 4-27), qui utilisera le fichier docker-compose. yml que vous avez créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="9a046-233">For these cases, you can run the `docker-compose up` command (Figure 4-27), which will use the docker-compose.yml file that you created previously.</span></span> <span data-ttu-id="9a046-234">L’exécution de cette commande génère toutes les images personnalisées et déploie l’application composée avec tous ses conteneurs associés.</span><span class="sxs-lookup"><span data-stu-id="9a046-234">Running this command builds all custom images and deploys the composed application with all of its related containers.</span></span>

![Sortie de console de la commande docker-compose up.](media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

<span data-ttu-id="9a046-236">**Figure 4-27**.</span><span class="sxs-lookup"><span data-stu-id="9a046-236">**Figure 4-27**.</span></span> <span data-ttu-id="9a046-237">Résultats de l’exécution de la commande docker-compose up</span><span class="sxs-lookup"><span data-stu-id="9a046-237">Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="9a046-238">Après avoir exécuté `docker-compose up`, déployez votre application et ses conteneurs sur votre hôte Docker (comme illustré à la figure 4-28) dans la représentation de machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="9a046-238">After you run `docker-compose up`, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-28, in the VM representation.</span></span>

![Machine virtuelle exécutant des applications à plusieurs conteneurs.](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="9a046-240">**Figure 4-28**.</span><span class="sxs-lookup"><span data-stu-id="9a046-240">**Figure 4-28**.</span></span> <span data-ttu-id="9a046-241">Machine virtuelle avec des conteneurs Docker déployés</span><span class="sxs-lookup"><span data-stu-id="9a046-241">VM with Docker containers deployed</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="9a046-242">Étape 6 : tester votre application Dockr (localement, sur votre machine virtuelle CD locale)</span><span class="sxs-lookup"><span data-stu-id="9a046-242">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="9a046-243">Cette étape varie en fonction de ce que fait votre application.</span><span class="sxs-lookup"><span data-stu-id="9a046-243">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="9a046-244">Dans une API web .NET Core de type « Hello World » déployée sous la forme d’un conteneur ou d’un service, vous devez simplement accéder au service en fournissant le port TCP qui est spécifié dans le fichier DockerFile.</span><span class="sxs-lookup"><span data-stu-id="9a046-244">In a simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="9a046-245">Sur l’hôte Docker, ouvrez un navigateur et accédez à ce site. Vous devez y voir votre application ou service s’exécuter, comme illustré à la figure 4-29.</span><span class="sxs-lookup"><span data-stu-id="9a046-245">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-29.</span></span>

![Vue du navigateur montrant la réponse à localhost/API/values.](media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="9a046-247">**Figure 4-29**.</span><span class="sxs-lookup"><span data-stu-id="9a046-247">**Figure 4-29**.</span></span> <span data-ttu-id="9a046-248">Test local de votre application Dockr à l’aide du navigateur</span><span class="sxs-lookup"><span data-stu-id="9a046-248">Testing your Docker application locally by using the browser</span></span>

<span data-ttu-id="9a046-249">Notez qu’il utilise le port 50080, mais qu’en interne il est redirigé vers le port 80, car c’est la manière dont il a été déployé avec `docker compose` , comme expliqué précédemment.</span><span class="sxs-lookup"><span data-stu-id="9a046-249">Note that it's using port 50080, but internally it's being redirected to port 80, because that's how it was deployed with `docker compose`, as explained earlier.</span></span>

<span data-ttu-id="9a046-250">Vous pouvez tester cela en utilisant le navigateur à l’aide de la boucle, comme illustré à la figure 4-30.</span><span class="sxs-lookup"><span data-stu-id="9a046-250">You can test this by using the browser using CURL from the terminal, as depicted in Figure 4-30.</span></span>

![Résultat de la boucle obtenu à partir de http://localhost:51080/WeatherForecast](media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="9a046-252">**Figure 4-30**.</span><span class="sxs-lookup"><span data-stu-id="9a046-252">**Figure 4-30**.</span></span> <span data-ttu-id="9a046-253">Test de l’application Docker localement avec CURL</span><span class="sxs-lookup"><span data-stu-id="9a046-253">Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="9a046-254">**Débogage d’un conteneur exécuté sur Docker**</span><span class="sxs-lookup"><span data-stu-id="9a046-254">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="9a046-255">Visual Studio Code prend en charge le débogage Docker si vous utilisez Node.js et d’autres plateformes telles que les conteneurs .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a046-255">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="9a046-256">Vous pouvez également déboguer les conteneurs .NET Core ou .NET Framework dans Docker si vous utilisez Visual Studio pour Windows ou Mac, comme décrit dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="9a046-256">You also can debug .NET Core or .NET Framework containers in Docker when using Visual Studio for Windows or Mac, as described in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="9a046-257">Pour en savoir plus sur le débogage Node.js conteneurs d’ancrage, consultez <https://blog.docker.com/2016/07/live-debugging-docker/> et <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more> .</span><span class="sxs-lookup"><span data-stu-id="9a046-257">To learn more about debugging Node.js Docker containers, see <https://blog.docker.com/2016/07/live-debugging-docker/> and <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="9a046-258">[Précédent](docker-apps-development-environment.md) 
>  [Suivant](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="9a046-258">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>
