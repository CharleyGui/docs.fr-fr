---
title: Workflow de développement des applications Docker
description: Découvrez les détails du workflow de développement des applications Docker. Commencez étape par étape et entrez dans les détails pour optimiser les fichiers Dockerfile, puis terminez par le workflow simplifié disponible avec Visual Studio.
ms.date: 01/30/2020
ms.openlocfilehash: 1ae4e3cda71676caeab849a92207477652050e25
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594591"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="67983-104">Workflow de développement des applications Docker</span><span class="sxs-lookup"><span data-stu-id="67983-104">Development workflow for Docker apps</span></span>

<span data-ttu-id="67983-105">Le cycle de vie de développement d’une application débute sur votre ordinateur, si vous êtes développeur, là où vous codez l’application dans le langage de votre choix et que vous la testez localement.</span><span class="sxs-lookup"><span data-stu-id="67983-105">The application development life cycle starts at your computer, as a developer, where you code the application using your preferred language and test it locally.</span></span> <span data-ttu-id="67983-106">Avec ce workflow, quels que soient le langage, le framework et la plateforme que vous choisissez, vous développez et testez toujours des conteneurs Docker, mais vous le faites localement.</span><span class="sxs-lookup"><span data-stu-id="67983-106">With this workflow, no matter which language, framework, and platform you choose, you're always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="67983-107">Chaque conteneur (instance d’une image Docker) inclut les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="67983-107">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="67983-108">Un système d’exploitation sélectionné, par exemple, une distribution Linux, Windows Nano Server ou Windows Server Core.</span><span class="sxs-lookup"><span data-stu-id="67983-108">An operating system selection, for example, a Linux distribution, Windows Nano Server, or Windows Server Core.</span></span>

- <span data-ttu-id="67983-109">Des fichiers ajoutés pendant le développement, par exemple, du code source et des fichiers binaires d’application.</span><span class="sxs-lookup"><span data-stu-id="67983-109">Files added during development, for example, source code and application binaries.</span></span>

- <span data-ttu-id="67983-110">Des informations de configuration, comme les paramètres d’environnement et les dépendances.</span><span class="sxs-lookup"><span data-stu-id="67983-110">Configuration information, such as environment settings and dependencies.</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="67983-111">Workflow pour développer des applications basées sur des conteneurs Docker</span><span class="sxs-lookup"><span data-stu-id="67983-111">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="67983-112">Cette section décrit le workflow de développement de la *boucle interne* pour les applications basées sur des conteneurs Docker.</span><span class="sxs-lookup"><span data-stu-id="67983-112">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="67983-113">Le flux de travail de la boucle interne signifie qu’il n’est pas considéré comme un flux de travail DevOps plus large, qui peut inclure un déploiement en production, et se concentre sur l’ordinateur du développeur.</span><span class="sxs-lookup"><span data-stu-id="67983-113">The inner-loop workflow means it's not considering the broader DevOps workflow, which can include up to production deployment, and just focuses on the development work done on the developer's computer.</span></span> <span data-ttu-id="67983-114">Les étapes initiales de configuration de l’environnement ne sont pas comprises non plus, car elles sont effectuées une seule fois.</span><span class="sxs-lookup"><span data-stu-id="67983-114">The initial steps to set up the environment aren't included, since those steps are done only once.</span></span>

<span data-ttu-id="67983-115">Une application est composée de vos propres services et de bibliothèques supplémentaires (dépendances).</span><span class="sxs-lookup"><span data-stu-id="67983-115">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="67983-116">La figure 5-1 illustre les principales étapes qu’un développeur doit généralement effectuer pour créer une application Docker.</span><span class="sxs-lookup"><span data-stu-id="67983-116">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

:::image type="complex" source="./media/docker-app-development-workflow/life-cycle-containerized-apps-docker-cli.png" alt-text="Diagramme montrant les 7 étapes nécessaires à la création d’une application en conteneur.":::
<span data-ttu-id="67983-118">Processus de développement pour les applications de l’arrimeur : 1-coder votre application, 2-écrire fichier dockerfile/s, 3-créer des images définies sur fichier dockerfile/s, 4-(facultatif) composer des services dans le fichier docker-compose. yml, 5-exécuter le conteneur ou l’application dockr-compose, 6-tester votre application ou vos microservices, 7-Push vers référentiel</span><span class="sxs-lookup"><span data-stu-id="67983-118">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span>
:::image-end:::

<span data-ttu-id="67983-119">**Figure 5-1.**</span><span class="sxs-lookup"><span data-stu-id="67983-119">**Figure 5-1.**</span></span> <span data-ttu-id="67983-120">Workflow pas à pas pour développer des applications Docker en conteneur</span><span class="sxs-lookup"><span data-stu-id="67983-120">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="67983-121">Cette section décrit tout ce processus en détail, en expliquant chacune des grandes étapes dans le contexte d’un environnement Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="67983-121">In this section, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="67983-122">Si vous optez pour une approche de développement avec un éditeur ou une interface CLI (par exemple, Visual Studio Code plus l’interface CLI Docker sur macOS ou Windows), vous devez connaître toutes les étapes de manière plus détaillée que pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="67983-122">When you're using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you're using Visual Studio.</span></span> <span data-ttu-id="67983-123">Pour plus d’informations sur le développement dans un environnement CLI, consultez le livre électronique [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span><span class="sxs-lookup"><span data-stu-id="67983-123">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="67983-124">Lorsque vous utilisez Visual Studio 2019, un grand nombre de ces étapes sont gérées pour vous, ce qui améliore considérablement votre productivité.</span><span class="sxs-lookup"><span data-stu-id="67983-124">When you're using Visual Studio 2019, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="67983-125">Cela est particulièrement vrai lorsque vous utilisez Visual Studio 2019 et que vous ciblez des applications à plusieurs conteneurs.</span><span class="sxs-lookup"><span data-stu-id="67983-125">This is especially true when you're using Visual Studio 2019 and targeting multi-container applications.</span></span> <span data-ttu-id="67983-126">Par exemple, en un seul clic de souris, Visual Studio ajoute `Dockerfile` le `docker-compose.yml` fichier et à vos projets avec la configuration de votre application.</span><span class="sxs-lookup"><span data-stu-id="67983-126">For instance, with just one mouse click, Visual Studio adds the `Dockerfile` and `docker-compose.yml` file to your projects with the configuration for your application.</span></span> <span data-ttu-id="67983-127">Quand vous exécutez l’application dans Visual Studio, le programme crée l’image Docker et exécute l’application multiconteneur directement dans Docker. Il vous permet même de déboguer plusieurs conteneurs à la fois.</span><span class="sxs-lookup"><span data-stu-id="67983-127">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="67983-128">Grâce à ces fonctionnalités, vous allez développer nettement plus vite.</span><span class="sxs-lookup"><span data-stu-id="67983-128">These features will boost your development speed.</span></span>

<span data-ttu-id="67983-129">Toutefois, même si Visual Studio effectue ces étapes automatiquement, vous devez comprendre comment intervient Docker dans chacune d’elles.</span><span class="sxs-lookup"><span data-stu-id="67983-129">However, just because Visual Studio makes those steps automatic doesn't mean that you don't need to know what's going on underneath with Docker.</span></span> <span data-ttu-id="67983-130">Par conséquent, le guide suivant décrit en détail chaque étape.</span><span class="sxs-lookup"><span data-stu-id="67983-130">Therefore, the following guidance details every step.</span></span>

![Image de l’étape 1.](./media/docker-app-development-workflow/step-1-code-your-app.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="67983-132">Étape 1.</span><span class="sxs-lookup"><span data-stu-id="67983-132">Step 1.</span></span> <span data-ttu-id="67983-133">Commencer le codage et créer votre base de référence initiale pour l’application ou le service</span><span class="sxs-lookup"><span data-stu-id="67983-133">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="67983-134">Le développement d’une application se déroule de façon similaire avec ou sans Docker.</span><span class="sxs-lookup"><span data-stu-id="67983-134">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="67983-135">La différence est que, quand vous développez avec Docker, vous déployez et testez l’application ou les services exécutés dans des conteneurs Docker dans votre environnement local (une machine virtuelle Linux configurée par Docker ou directement Windows si vous utilisez des conteneurs Windows).</span><span class="sxs-lookup"><span data-stu-id="67983-135">The difference is that while developing for Docker, you're deploying and testing your application or services running within Docker containers in your local environment (either a Linux VM setup by Docker or directly Windows if using Windows Containers).</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="67983-136">Configurer votre environnement local avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="67983-136">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="67983-137">Pour commencer, assurez-vous que [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) pour Windows est installé, comme cela est expliqué dans les instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="67983-137">To begin, make sure you have [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="67983-138">Bien démarrer avec Docker CE pour Windows</span><span class="sxs-lookup"><span data-stu-id="67983-138">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="67983-139">En outre, vous avez besoin de Visual Studio 2019 version 16,4 ou ultérieure, avec la charge de travail **développement multiplateforme .net Core** installée, comme illustré à la figure 5-2.</span><span class="sxs-lookup"><span data-stu-id="67983-139">In addition, you need Visual Studio 2019 version 16.4 or later, with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![Capture d’écran de la sélection du développement multiplateforme .NET Core.](./media/docker-app-development-workflow/dotnet-core-cross-platform-development.png)

<span data-ttu-id="67983-141">**Figure 5-2**.</span><span class="sxs-lookup"><span data-stu-id="67983-141">**Figure 5-2**.</span></span> <span data-ttu-id="67983-142">Sélection de la charge de travail de **développement multiplateforme .net Core** lors de l’installation de Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="67983-142">Selecting the **.NET Core cross-platform development** workload during Visual Studio 2019 setup</span></span>

<span data-ttu-id="67983-143">Vous pouvez commencer le codage de votre application en .NET brut (généralement dans .NET Core si vous envisagez d’utiliser des conteneurs) même si vous n’avez pas encore activé Docker dans votre application, ni effectué de déploiement et de test dans Docker.</span><span class="sxs-lookup"><span data-stu-id="67983-143">You can start coding your application in plain .NET (usually in .NET Core if you're planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="67983-144">Toutefois, nous vous recommandons de commencer à travailler dans Docker le plus tôt possible, car Docker sera le véritable environnement de développement, et vous pourrez détecter les problèmes éventuels dès le début.</span><span class="sxs-lookup"><span data-stu-id="67983-144">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="67983-145">Nous le conseillons d’autant plus que Visual Studio rend l’utilisation de Docker extrêmement simple et intuitive. L’exemple le plus significatif est le débogage des applications multiconteneurs à partir de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="67983-145">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="67983-146">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="67983-146">Additional resources</span></span>

- <span data-ttu-id="67983-147">**Prise en main de Docker CE pour Windows** </span><span class="sxs-lookup"><span data-stu-id="67983-147">**Get started with Docker CE for Windows** </span></span>\
  <https://docs.docker.com/docker-for-windows/>

- <span data-ttu-id="67983-148">**Visual Studio 2019** </span><span class="sxs-lookup"><span data-stu-id="67983-148">**Visual Studio 2019** </span></span>\
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

![Image de l’étape 2.](./media/docker-app-development-workflow/step-2-write-dockerfile.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="67983-150">Étape 2.</span><span class="sxs-lookup"><span data-stu-id="67983-150">Step 2.</span></span> <span data-ttu-id="67983-151">Créer un fichier Dockerfile associé à une image de base .NET existante</span><span class="sxs-lookup"><span data-stu-id="67983-151">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="67983-152">Vous avez besoin d’un fichier Dockerfile pour chaque image personnalisée que vous souhaitez créer. Vous avez également besoin d’un fichier Dockerfile pour chaque conteneur à déployer, que vous choisissiez de le déployer automatiquement à partir de Visual Studio ou manuellement à l’aide de la CLI Docker (commandes docker run et docker-compose).</span><span class="sxs-lookup"><span data-stu-id="67983-152">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="67983-153">Si votre application contient un seul service personnalisé, créez un seul fichier Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="67983-153">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="67983-154">Si votre application contient plusieurs services (comme dans une architecture de microservices), vous devez créer un fichier Dockerfile pour chaque service.</span><span class="sxs-lookup"><span data-stu-id="67983-154">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="67983-155">Le fichier Dockerfile est créé dans le dossier racine de votre application ou service.</span><span class="sxs-lookup"><span data-stu-id="67983-155">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="67983-156">Il contient les commandes qui indiquent à Docker comment configurer et exécuter votre application ou service dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="67983-156">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="67983-157">Vous pouvez créer manuellement un fichier Dockerfile dans le code et l’ajouter à votre projet, avec vos dépendances .NET.</span><span class="sxs-lookup"><span data-stu-id="67983-157">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="67983-158">Avec Visual Studio et ses outils pour Docker, cette tâche se fait en quelques clics de souris seulement.</span><span class="sxs-lookup"><span data-stu-id="67983-158">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="67983-159">Lorsque vous créez un projet dans Visual Studio 2019, il existe une option nommée **activer la prise en charge** de l’ancrage, comme illustré à la figure 5-3.</span><span class="sxs-lookup"><span data-stu-id="67983-159">When you create a new project in Visual Studio 2019, there's an option named **Enable Docker Support** , as shown in Figure 5-3.</span></span>

![Capture d’écran montrant la case à cocher Activer la prise en charge de l’ancrage.](./media/docker-app-development-workflow/enable-docker-support-check-box.png)

<span data-ttu-id="67983-161">**Figure 5-3**.</span><span class="sxs-lookup"><span data-stu-id="67983-161">**Figure 5-3**.</span></span> <span data-ttu-id="67983-162">Activation de la prise en charge de l’ancrage lors de la création d’un projet de ASP.NET Core dans Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="67983-162">Enabling Docker Support when creating a new ASP.NET Core project in Visual Studio 2019</span></span>

<span data-ttu-id="67983-163">Vous pouvez également activer la prise en charge de l’ancrage sur un projet d’application Web ASP.net Core existant en cliquant avec le bouton droit sur le projet dans **Explorateur de solutions** et en sélectionnant **Ajouter** la  >  **prise en charge de l’ancrage...** , comme illustré à la figure 5-4.</span><span class="sxs-lookup"><span data-stu-id="67983-163">You can also enable Docker support on an existing ASP.NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support...** , as shown in Figure 5-4.</span></span>

![Capture d’écran montrant l’option prise en charge de l’ancrage dans le menu Ajouter.](./media/docker-app-development-workflow/add-docker-support-option.png)

<span data-ttu-id="67983-165">**Figure 5-4**.</span><span class="sxs-lookup"><span data-stu-id="67983-165">**Figure 5-4**.</span></span> <span data-ttu-id="67983-166">Activation de la prise en charge de l’ancrage dans un projet Visual Studio 2019 existant</span><span class="sxs-lookup"><span data-stu-id="67983-166">Enabling Docker support in an existing Visual Studio 2019 project</span></span>

<span data-ttu-id="67983-167">Cette action ajoute un fichier *Dockerfile* au projet avec la configuration nécessaire. Elle est disponible uniquement dans les projets d’application web ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="67983-167">This action adds a *Dockerfile* to the project with the required configuration, and is only available on ASP.NET Core projects.</span></span>

<span data-ttu-id="67983-168">De même, Visual Studio peut également ajouter un `docker-compose.yml` fichier pour l’ensemble de la solution avec l’option **Ajouter > prise en charge d’Orchestrator de conteneur...**. À l’étape 4, nous allons explorer cette option plus en détail.</span><span class="sxs-lookup"><span data-stu-id="67983-168">In a similar fashion, Visual Studio can also add a `docker-compose.yml` file for the whole solution with the option **Add > Container Orchestrator Support...**. In step 4, we'll explore this option in greater detail.</span></span>

### <a name="using-an-existing-official-net-docker-image"></a><span data-ttu-id="67983-169">Utilisation d’une image Docker .NET officielle existante</span><span class="sxs-lookup"><span data-stu-id="67983-169">Using an existing official .NET Docker image</span></span>

<span data-ttu-id="67983-170">Le plus souvent, vous créez une image personnalisée pour votre conteneur à partir d’une image de base que vous obtenez dans un dépôt officiel comme le registre [Docker Hub](https://hub.docker.com/).</span><span class="sxs-lookup"><span data-stu-id="67983-170">You usually build a custom image for your container on top of a base image you get from an official repository like the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="67983-171">C’est précisément ce qui se passe en arrière-plan quand vous activez la prise en charge de Docker dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="67983-171">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="67983-172">Votre fichier Dockerfile utilise une image `dotnet/core/aspnet` existante.</span><span class="sxs-lookup"><span data-stu-id="67983-172">Your Dockerfile will use an existing `dotnet/core/aspnet` image.</span></span>

<span data-ttu-id="67983-173">Précédemment, nous avons expliqué quels images et dépôts Docker vous pouvez utiliser selon le framework et le système d’exploitation que vous avez choisis.</span><span class="sxs-lookup"><span data-stu-id="67983-173">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="67983-174">Par exemple, si vous souhaitez utiliser ASP.NET Core (Windows ou Linux), l’image à utiliser est `mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span><span class="sxs-lookup"><span data-stu-id="67983-174">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is `mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span></span> <span data-ttu-id="67983-175">La seule chose à faire est donc de spécifier l’image Docker de base à utiliser pour votre conteneur.</span><span class="sxs-lookup"><span data-stu-id="67983-175">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="67983-176">Pour ce faire, ajoutez `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` à votre fichier Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="67983-176">You do that by adding `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` to your Dockerfile.</span></span> <span data-ttu-id="67983-177">Cette opération est effectuée automatiquement par Visual Studio, mais si vous avez à mettre à jour la version, vous devez modifier cette valeur.</span><span class="sxs-lookup"><span data-stu-id="67983-177">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="67983-178">L’utilisation d’un dépôt d’images .NET officiel fourni dans le Docker Hub avec un numéro de version garantit que les mêmes fonctionnalités de langage sont disponibles sur toutes les machines (y compris celles de développement, test et production).</span><span class="sxs-lookup"><span data-stu-id="67983-178">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="67983-179">L’extrait de code suivant est un exemple de fichier Dockerfile pour un conteneur ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="67983-179">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="67983-180">Dans ce cas, l’image est basée sur la version 3,1 de l’image officielle de l’ancre ASP.NET Core (multi-arch pour Linux et Windows).</span><span class="sxs-lookup"><span data-stu-id="67983-180">In this case, the image is based on version 3.1 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="67983-181">Il s’agit du paramètre `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span><span class="sxs-lookup"><span data-stu-id="67983-181">This is the setting `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span></span> <span data-ttu-id="67983-182">(Pour plus d’informations sur cette image de base, consultez la page image de l' [ancreur .net Core](https://hub.docker.com/_/microsoft-dotnet-core/) .) Dans le fichier dockerfile, vous devez également demander à Dockr d’écouter sur le port TCP que vous allez utiliser lors de l’exécution (dans ce cas, le port 80, tel que configuré avec le paramètre exposer).</span><span class="sxs-lookup"><span data-stu-id="67983-182">(For more information about this base image, see the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="67983-183">Vous pouvez spécifier des paramètres de configuration supplémentaires dans le fichier Dockerfile, en fonction du langage et du framework que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="67983-183">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="67983-184">Par exemple, la ligne ENTRYPOINT avec `["dotnet", "MySingleContainerWebApp.dll"]` indique à Docker d’exécuter une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="67983-184">For instance, the ENTRYPOINT line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="67983-185">Si vous utilisez le SDK et l’interface CLI (dotnet) de .NET Core pour créer et exécuter l’application .NET, ce paramètre est différent.</span><span class="sxs-lookup"><span data-stu-id="67983-185">If you're using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="67983-186">L’essentiel à retenir est que la ligne ENTRYPOINT et certains autres paramètres varient selon le langage et la plateforme choisis pour votre application.</span><span class="sxs-lookup"><span data-stu-id="67983-186">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="67983-187">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="67983-187">Additional resources</span></span>

- <span data-ttu-id="67983-188">**Création d’images d’ancrage pour les applications .NET Core** </span><span class="sxs-lookup"><span data-stu-id="67983-188">**Building Docker Images for .NET Core Applications** </span></span>\
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

- <span data-ttu-id="67983-189">**Créer votre propre image**.</span><span class="sxs-lookup"><span data-stu-id="67983-189">**Build your own image**.</span></span> <span data-ttu-id="67983-190">Dans la documentation officielle de Docker.</span><span class="sxs-lookup"><span data-stu-id="67983-190">In the official Docker documentation.</span></span>\
  <https://docs.docker.com/engine/tutorials/dockerimages/>

- <span data-ttu-id="67983-191">**Rester à jour avec les images de conteneur .NET** </span><span class="sxs-lookup"><span data-stu-id="67983-191">**Staying up-to-date with .NET Container Images** </span></span>\
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- <span data-ttu-id="67983-192">**Utilisation conjointe de .NET et de Dockr-DockerCon 2018 Update** </span><span class="sxs-lookup"><span data-stu-id="67983-192">**Using .NET and Docker Together - DockerCon 2018 Update** </span></span>\
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="67983-193">Utilisation de dépôts d’images multi-arch</span><span class="sxs-lookup"><span data-stu-id="67983-193">Using multi-arch image repositories</span></span>

<span data-ttu-id="67983-194">Un dépôt peut contenir des variantes de plateforme, comme une image Linux et une image Windows.</span><span class="sxs-lookup"><span data-stu-id="67983-194">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="67983-195">Cette fonctionnalité permet aux fournisseurs comme Microsoft (créateurs d’images de base) de créer un dépôt commun pour plusieurs plateformes (Linux et Windows).</span><span class="sxs-lookup"><span data-stu-id="67983-195">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="67983-196">Par exemple, le référentiel [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) disponible dans le registre Docker Hub assure sous le même nom la prise en charge de Linux et Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="67983-196">For example, the [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="67983-197">Si vous spécifiez une balise, le ciblage d’une plateforme est explicite, comme dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="67983-197">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim` \
  <span data-ttu-id="67983-198">Cibles : .NET Core 3,1 Runtime uniquement sur Linux</span><span class="sxs-lookup"><span data-stu-id="67983-198">Targets: .NET Core 3.1 runtime-only on Linux</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1909` \
  <span data-ttu-id="67983-199">Cibles : Runtime .NET Core 3,1 uniquement sur Windows nano Server</span><span class="sxs-lookup"><span data-stu-id="67983-199">Targets: .NET Core 3.1 runtime-only on Windows Nano Server</span></span>

<span data-ttu-id="67983-200">Toutefois, si vous spécifiez le même nom d’image avec la même balise, les images multi-architectures (comme l’image `aspnet`) utilisent la version Windows ou Linux selon le système d’exploitation hôte de Docker que vous déployez, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="67983-200">But, if you specify the same image name, even with the same tag, the multi-arch images (like the `aspnet` image) will use the Linux or Windows version depending on the Docker host OS you're deploying, as shown in the following example:</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1` \
  <span data-ttu-id="67983-201">Multi-arch : .NET Core 3,1 Runtime uniquement sur Linux ou Windows nano Server en fonction du système d’exploitation hôte de l’ordinateur d’amarrage</span><span class="sxs-lookup"><span data-stu-id="67983-201">Multi-arch: .NET Core 3.1 runtime-only on Linux or Windows Nano Server depending on the Docker host OS</span></span>

<span data-ttu-id="67983-202">Ainsi, quand vous tirez (pull) une image d’un hôte Windows, la variante Windows est tirée et quand vous tirez le même nom d’image d’un hôte Linux, la variante Linux est tirée.</span><span class="sxs-lookup"><span data-stu-id="67983-202">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="multi-stage-builds-in-dockerfile"></a><span data-ttu-id="67983-203">Builds multi-étapes dans le fichier Dockerfile</span><span class="sxs-lookup"><span data-stu-id="67983-203">Multi-stage builds in Dockerfile</span></span>

<span data-ttu-id="67983-204">Le fichier Dockerfile est similaire à un script de commandes par lot.</span><span class="sxs-lookup"><span data-stu-id="67983-204">The Dockerfile is similar to a batch script.</span></span> <span data-ttu-id="67983-205">C’est la même chose que configurer un ordinateur à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="67983-205">Similar to what you would do if you had to set up the machine from the command line.</span></span>

<span data-ttu-id="67983-206">Il commence par une image de base qui définit le contexte initial, comme le système de fichiers de départ, qui repose sur le système d’exploitation hôte.</span><span class="sxs-lookup"><span data-stu-id="67983-206">It starts with a base image that sets up the initial context, it's like the startup filesystem, that sits on top of the host OS.</span></span> <span data-ttu-id="67983-207">Ce n’est pas un système d’exploitation, mais vous pouvez le considérer comme le système d’exploitation à l’intérieur du conteneur.</span><span class="sxs-lookup"><span data-stu-id="67983-207">It's not an OS, but you can think of it like "the" OS inside the container.</span></span>

<span data-ttu-id="67983-208">L’exécution de chaque ligne de commande crée une couche sur le système de fichiers avec les changements de la couche précédente, et c’est la combinaison de ces couches qui produit le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="67983-208">The execution of every command line creates a new layer on the filesystem with the changes from the previous one, so that, when combined, produce the resulting filesystem.</span></span>

<span data-ttu-id="67983-209">Comme chaque nouvelle couche « repose » sur la précédente et que la taille de l’image obtenue augmente avec chaque commande, les images peuvent devenir très grandes, surtout si elles doivent comprendre, par exemple, le SDK nécessaire à la génération et la publication d’une application.</span><span class="sxs-lookup"><span data-stu-id="67983-209">Since every new layer "rests" on top of the previous one and the resulting image size increases with every command, images can get very large if they have to include, for example, the SDK needed to build and publish an application.</span></span>

<span data-ttu-id="67983-210">D’où l’intérêt des builds multi-étapes (à partir de Docker 17.05 et versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="67983-210">This is where multi-stage builds get into the plot (from Docker 17.05 and higher) to do their magic.</span></span>

<span data-ttu-id="67983-211">L’idée fondamentale est que vous pouvez diviser le processus d’exécution des fichiers Dockerfile en étapes, où une étape est une image initiale suivie d’une ou plusieurs commandes et la dernière étape détermine la taille finale de l’image.</span><span class="sxs-lookup"><span data-stu-id="67983-211">The core idea is that you can separate the Dockerfile execution process in stages, where a stage is an initial image followed by one or more commands, and the last stage determines the final image size.</span></span>

<span data-ttu-id="67983-212">En bref, les builds multi-étapes permettent de diviser la création en différentes « étapes » et d’assembler l’image finale en prenant uniquement les répertoires appropriés des étapes intermédiaires.</span><span class="sxs-lookup"><span data-stu-id="67983-212">In short, multi-stage builds allow splitting the creation in different "phases" and then assemble the final image taking only the relevant directories from the intermediate stages.</span></span> <span data-ttu-id="67983-213">La stratégie générale pour utiliser cette fonctionnalité est :</span><span class="sxs-lookup"><span data-stu-id="67983-213">The general strategy to use this feature is:</span></span>

1. <span data-ttu-id="67983-214">Utiliser une image SDK de base (peu importe la taille), avec tous les éléments nécessaires pour générer et publier l’application dans un dossier, puis</span><span class="sxs-lookup"><span data-stu-id="67983-214">Use a base SDK image (doesn't matter how large), with everything needed to build and publish the application to a folder and then</span></span>

2. <span data-ttu-id="67983-215">Utiliser une image de base, petite et pour le runtime uniquement, et copier le dossier de publication de l’étape précédente pour produire une petite image finale.</span><span class="sxs-lookup"><span data-stu-id="67983-215">Use a base, small, runtime-only image and copy the publishing folder from the previous stage to produce a small final image.</span></span>

<span data-ttu-id="67983-216">Vraisemblablement, la meilleure façon de comprendre le concept du multi-étape est d’étudier en détail un fichier Dockerfile, ligne par ligne. Commençons donc avec le fichier Dockerfile initial créé par Visual Studio pendant l’ajout de la prise en charge de Docker à un projet, nous verrons les optimisations plus tard.</span><span class="sxs-lookup"><span data-stu-id="67983-216">Probably the best way to understand multi-stage is going through a Dockerfile in detail, line by line, so let's begin with the initial Dockerfile created by Visual Studio when adding Docker support to a project and will get into some optimizations later.</span></span>

<span data-ttu-id="67983-217">Le fichier Dockerfile initial peut ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="67983-217">The initial Dockerfile might look something like this:</span></span>

```dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
 6  WORKDIR /src
 7  COPY src/Services/Catalog/Catalog.API/Catalog.API.csproj …
 8  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.AspNetCore.HealthChecks …
 9  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions.HealthChecks …
10  COPY src/BuildingBlocks/EventBus/IntegrationEventLogEF/ …
11  COPY src/BuildingBlocks/EventBus/EventBus/EventBus.csproj …
12  COPY src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.csproj …
13  COPY src/BuildingBlocks/EventBus/EventBusServiceBus/EventBusServiceBus.csproj …
14  COPY src/BuildingBlocks/WebHostCustomization/WebHost.Customization …
15  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
16  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
17  RUN dotnet restore src/Services/Catalog/Catalog.API/Catalog.API.csproj
18  COPY . .
19  WORKDIR /src/src/Services/Catalog/Catalog.API
20  RUN dotnet build Catalog.API.csproj -c Release -o /app
21
22  FROM build AS publish
23  RUN dotnet publish Catalog.API.csproj -c Release -o /app
24
25  FROM base AS final
26  WORKDIR /app
27  COPY --from=publish /app .
28  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

<span data-ttu-id="67983-218">Voici les détails, ligne par ligne :</span><span class="sxs-lookup"><span data-stu-id="67983-218">And these are the details, line by line:</span></span>

- <span data-ttu-id="67983-219">**#1 de ligne :** Commencez une étape avec une « petite » image de base du runtime uniquement, appelez la **base** IT pour référence.</span><span class="sxs-lookup"><span data-stu-id="67983-219">**Line #1:** Begin a stage with a "small" runtime-only base image, call it **base** for reference.</span></span>

- <span data-ttu-id="67983-220">**#2 de ligne :** Créez le répertoire **/app** dans l’image.</span><span class="sxs-lookup"><span data-stu-id="67983-220">**Line #2:** Create the **/app** directory in the image.</span></span>

- <span data-ttu-id="67983-221">**#3 de ligne :** Exposez le port **80**.</span><span class="sxs-lookup"><span data-stu-id="67983-221">**Line #3:** Expose port **80**.</span></span>

- <span data-ttu-id="67983-222">**#5 de ligne :** Commencez une nouvelle étape avec l’image « grande » pour la création ou la publication.</span><span class="sxs-lookup"><span data-stu-id="67983-222">**Line #5:** Begin a new stage with the "large" image for building/publishing.</span></span> <span data-ttu-id="67983-223">Appelez-la **Build** à des fins de référence.</span><span class="sxs-lookup"><span data-stu-id="67983-223">Call it **build** for reference.</span></span>

- <span data-ttu-id="67983-224">**#6 de ligne :** Créez le répertoire **/src** dans l’image.</span><span class="sxs-lookup"><span data-stu-id="67983-224">**Line #6:** Create directory **/src** in the image.</span></span>

- <span data-ttu-id="67983-225">**#7 de ligne :** Jusqu’à la ligne 16, copiez les fichiers projet **. csproj** référencés pour pouvoir restaurer les packages ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="67983-225">**Line #7:** Up to line 16, copy referenced **.csproj** project files to be able to restore packages later.</span></span>

- <span data-ttu-id="67983-226">**#17 de ligne :** Restaurez les packages du projet **Catalog. API** et des projets référencés.</span><span class="sxs-lookup"><span data-stu-id="67983-226">**Line #17:** Restore packages for the **Catalog.API** project and the referenced projects.</span></span>

- <span data-ttu-id="67983-227">**#18 de ligne :** Copiez **toutes les arborescences de répertoires de la solution** (à l’exception des fichiers/répertoires inclus dans le fichier **. dockerignore** ) dans le répertoire **/src** de l’image.</span><span class="sxs-lookup"><span data-stu-id="67983-227">**Line #18:** Copy **all directory tree for the solution** (except the files/directories included in the **.dockerignore** file) to the **/src** directory in the image.</span></span>

- <span data-ttu-id="67983-228">**#19 de ligne :** Remplacez le dossier actif par le projet **Catalog. API** .</span><span class="sxs-lookup"><span data-stu-id="67983-228">**Line #19:** Change the current folder to the **Catalog.API** project.</span></span>

- <span data-ttu-id="67983-229">**#20 de ligne :** Générez le projet (et les autres dépendances du projet) et la sortie dans le répertoire **/app** dans l’image.</span><span class="sxs-lookup"><span data-stu-id="67983-229">**Line #20:** Build the project (and other project dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="67983-230">**#22 de ligne :** Commencez une nouvelle étape en continuant à partir de la Build.</span><span class="sxs-lookup"><span data-stu-id="67983-230">**Line #22:** Begin a new stage continuing from the build.</span></span> <span data-ttu-id="67983-231">Appelez-la **publication** pour référence.</span><span class="sxs-lookup"><span data-stu-id="67983-231">Call it **publish** for reference.</span></span>

- <span data-ttu-id="67983-232">**#23 de ligne :** Publiez le projet (et les dépendances) et la sortie vers le répertoire **/app** dans l’image.</span><span class="sxs-lookup"><span data-stu-id="67983-232">**Line #23:** Publish the project (and dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="67983-233">**#25 de ligne :** Commencez une nouvelle étape en continuant à partir de la **base** et appelez-la **final**.</span><span class="sxs-lookup"><span data-stu-id="67983-233">**Line #25:** Begin a new stage continuing from **base** and call it **final**.</span></span>

- <span data-ttu-id="67983-234">**#26 de ligne :** Remplacez le répertoire actif par **/app**.</span><span class="sxs-lookup"><span data-stu-id="67983-234">**Line #26:** Change the current directory to **/app**.</span></span>

- <span data-ttu-id="67983-235">**#27 de ligne :** Copiez le répertoire **/app** à partir de l’étape **publier** dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="67983-235">**Line #27:** Copy the **/app** directory from stage **publish** to the current directory.</span></span>

- <span data-ttu-id="67983-236">**#28 de ligne :** Définissez la commande à exécuter lorsque le conteneur est démarré.</span><span class="sxs-lookup"><span data-stu-id="67983-236">**Line #28:** Define the command to run when the container is started.</span></span>

<span data-ttu-id="67983-237">Voyons maintenant les optimisations possibles pour améliorer les performances de l’ensemble du processus qui, dans le cas d’eShopOnContainers, signifie 22 minutes ou plus pour générer la solution complète dans des conteneurs Linux.</span><span class="sxs-lookup"><span data-stu-id="67983-237">Now let's explore some optimizations to improve the whole process performance that, in the case of eShopOnContainers, means about 22 minutes or more to build the complete solution in Linux containers.</span></span>

<span data-ttu-id="67983-238">Vous allez tirer parti de la fonctionnalité de cache de couches de Docker, qui est assez simple : si l’image de base et les commandes sont les mêmes que certaines exécutées précédemment, vous pouvez gagner du temps en utilisant simplement la couche qui en résulte sans avoir à exécuter les commandes.</span><span class="sxs-lookup"><span data-stu-id="67983-238">You'll take advantage of Docker's layer cache feature, which is quite simple: if the base image and the commands are the same as some previously executed, it can just use the resulting layer without the need to execute the commands, thus saving some time.</span></span>

<span data-ttu-id="67983-239">Par conséquent, prenons l’étape **build** , les lignes 5 et 6 sont quasiment les mêmes, mais les lignes 7 à 17 sont différentes pour chaque service d’eShopOnContainers, et doivent donc être exécutées à chaque fois, mais si vous remplacez les lignes 7 à 16 par :</span><span class="sxs-lookup"><span data-stu-id="67983-239">So, let's focus on the **build** stage, lines 5-6 are mostly the same, but lines 7-17 are different for every service from eShopOnContainers, so they have to execute every single time, however if you changed lines 7-16 to:</span></span>

```dockerfile
COPY . .
```

<span data-ttu-id="67983-240">Elles sont alors identiques pour chaque service, la solution entière est copiée, ce qui produit une couche plus grande, mais :</span><span class="sxs-lookup"><span data-stu-id="67983-240">Then it would be just the same for every service, it would copy the whole solution and would create a larger layer but:</span></span>

1. <span data-ttu-id="67983-241">Le processus de copie est seulement exécuté la première fois (et pendant la regénération si un fichier est changé) et utilise le cache pour tous les autres services, et</span><span class="sxs-lookup"><span data-stu-id="67983-241">The copy process would only be executed the first time (and when rebuilding if a file is changed) and would use the cache for all other services and</span></span>

2. <span data-ttu-id="67983-242">Étant donné que l’image la plus grande se produit à une étape intermédiaire, elle n’affecte pas la taille finale de l’image.</span><span class="sxs-lookup"><span data-stu-id="67983-242">Since the larger image occurs in an intermediate stage, it doesn't affect the final image size.</span></span>

<span data-ttu-id="67983-243">L’optimisation importante suivante implique la commande `restore` exécutée à la ligne 17, qui est également différente pour chaque service d’eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="67983-243">The next significant optimization involves the `restore` command executed in line 17, which is also different for every service of eShopOnContainers.</span></span> <span data-ttu-id="67983-244">Si vous remplacez cette ligne simplement par :</span><span class="sxs-lookup"><span data-stu-id="67983-244">If you change that line to just:</span></span>

```dockerfile
RUN dotnet restore
```

<span data-ttu-id="67983-245">Les packages sont restaurés pour l’ensemble de la solution, mais une fois encore, ils sont restaurés une seule fois au lieu de 15 fois avec la stratégie actuelle.</span><span class="sxs-lookup"><span data-stu-id="67983-245">It would restore the packages for the whole solution, but then again, it would do it just once, instead of the 15 times with the current strategy.</span></span>

<span data-ttu-id="67983-246">Toutefois, `dotnet restore` s’exécute uniquement si le dossier contient un seul fichier projet ou solution. Les choses se compliquent donc un peu et vous pouvez résoudre le problème, sans rentrer dans les détails, de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="67983-246">However, `dotnet restore` only runs if there's a single project or solution file in the folder, so achieving this is a bit more complicated and the way to solve it, without getting into too many details, is this:</span></span>

1. <span data-ttu-id="67983-247">Ajoutez les lignes suivantes à **.dockerignore**  :</span><span class="sxs-lookup"><span data-stu-id="67983-247">Add the following lines to **.dockerignore** :</span></span>

   - <span data-ttu-id="67983-248">`*.sln`, pour ignorer tous les fichiers solution dans l’arborescence de dossiers principale</span><span class="sxs-lookup"><span data-stu-id="67983-248">`*.sln`, to ignore all solution files in the main folder tree</span></span>

   - <span data-ttu-id="67983-249">`!eShopOnContainers-ServicesAndWebApps.sln`, pour inclure uniquement ce fichier solution.</span><span class="sxs-lookup"><span data-stu-id="67983-249">`!eShopOnContainers-ServicesAndWebApps.sln`, to include only this solution file.</span></span>

2. <span data-ttu-id="67983-250">Ajoutez l’argument `/ignoreprojectextensions:.dcproj` à `dotnet restore`, pour que le processus ignore également le projet docker-compose et restaure uniquement les packages de la solution eShopOnContainers-ServicesAndWebApps.</span><span class="sxs-lookup"><span data-stu-id="67983-250">Include the `/ignoreprojectextensions:.dcproj` argument to `dotnet restore`, so it also ignores the docker-compose project and only restores the packages for the eShopOnContainers-ServicesAndWebApps solution.</span></span>

<span data-ttu-id="67983-251">Voyons maintenant l’optimisation finale : la ligne 20 est redondante et, comme la ligne 23 génère aussi l’application et suit, logiquement, la ligne 20, la commande prend beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="67983-251">For the final optimization, it just happens that line 20 is redundant, as line 23 also builds the application and comes, in essence, right after line 20, so there goes another time-consuming command.</span></span>

<span data-ttu-id="67983-252">Le fichier résultant est alors :</span><span class="sxs-lookup"><span data-stu-id="67983-252">The resulting file is then:</span></span>

```dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS publish
 6  WORKDIR /src
 7  COPY . .
 8  RUN dotnet restore /ignoreprojectextensions:.dcproj
 9  WORKDIR /src/src/Services/Catalog/Catalog.API
10  RUN dotnet publish Catalog.API.csproj -c Release -o /app
11
12  FROM base AS final
13  WORKDIR /app
14  COPY --from=publish /app .
15  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

### <a name="creating-your-base-image-from-scratch"></a><span data-ttu-id="67983-253">Création de votre image de base à partir de zéro</span><span class="sxs-lookup"><span data-stu-id="67983-253">Creating your base image from scratch</span></span>

<span data-ttu-id="67983-254">Vous pouvez créer votre propre image de base Docker à partir de zéro.</span><span class="sxs-lookup"><span data-stu-id="67983-254">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="67983-255">Ce scénario n’est pas recommandé si vous n’êtes pas encore familiarisé avec Docker, mais si vous souhaitez définir les bits spécifiques de votre propre image de base, vous pouvez le faire.</span><span class="sxs-lookup"><span data-stu-id="67983-255">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="67983-256">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="67983-256">Additional resources</span></span>

- <span data-ttu-id="67983-257">**Images .net core à plusieurs arches**. </span><span class="sxs-lookup"><span data-stu-id="67983-257">**Multi-arch .NET Core images**.</span></span>\
  <https://github.com/dotnet/announcements/issues/14>

- <span data-ttu-id="67983-258">**Créer une image de base**.</span><span class="sxs-lookup"><span data-stu-id="67983-258">**Create a base image**.</span></span> <span data-ttu-id="67983-259">Documentation officielle de Docker.</span><span class="sxs-lookup"><span data-stu-id="67983-259">Official Docker documentation.</span></span>\
  <https://docs.docker.com/develop/develop-images/baseimages/>

![Image de l’étape 3.](./media/docker-app-development-workflow/step-3-create-dockerfile-defined-images.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="67983-261">Étape 3.</span><span class="sxs-lookup"><span data-stu-id="67983-261">Step 3.</span></span> <span data-ttu-id="67983-262">Créer vos images Docker personnalisées et incorporer votre application ou service dans ces images</span><span class="sxs-lookup"><span data-stu-id="67983-262">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="67983-263">Pour chaque service inclus dans votre application, vous devez créer une image associée.</span><span class="sxs-lookup"><span data-stu-id="67983-263">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="67983-264">Si votre application est composée uniquement d’un service ou d’une application web, vous avez besoin d’une seule image.</span><span class="sxs-lookup"><span data-stu-id="67983-264">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="67983-265">Sachez que les images Docker sont créées automatiquement dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="67983-265">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="67983-266">Les étapes suivantes s’appliquent uniquement dans le cadre du workflow avec un éditeur ou une CLI. Elles sont expliquées pour vous permettre de bien en comprendre tous les dessous.</span><span class="sxs-lookup"><span data-stu-id="67983-266">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="67983-267">En tant que développeur, vous avez besoin d’écrire du code et de le tester localement avant d’envoyer (push) une fonctionnalité ou une modification terminée dans votre système de contrôle de code source (par exemple, GitHub).</span><span class="sxs-lookup"><span data-stu-id="67983-267">You, as a developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="67983-268">Cela signifie que vous devez créer les images Docker et déployer des conteneurs sur un hôte Docker local (machine virtuelle Windows ou Linux), et exécuter, tester et déboguer dans ces conteneurs locaux.</span><span class="sxs-lookup"><span data-stu-id="67983-268">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="67983-269">Pour créer une image personnalisée dans votre environnement local avec la CLI Docker et votre fichier Dockerfile, vous pouvez utiliser la commande docker build, comme indiqué dans la figure 5-5.</span><span class="sxs-lookup"><span data-stu-id="67983-269">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![Capture d’écran montrant la sortie de la console de la commande dockr Build.](./media/docker-app-development-workflow/run-docker-build-command.png)

<span data-ttu-id="67983-271">**Figure 5-5**.</span><span class="sxs-lookup"><span data-stu-id="67983-271">**Figure 5-5**.</span></span> <span data-ttu-id="67983-272">Création d’une image Docker personnalisée</span><span class="sxs-lookup"><span data-stu-id="67983-272">Creating a custom Docker image</span></span>

<span data-ttu-id="67983-273">Si vous le souhaitez, au lieu d’exécuter la commande docker build directement à partir du dossier de projet, vous pouvez d’abord générer un dossier déployable avec les fichiers binaires et les bibliothèques .NET nécessaires en exécutant `dotnet publish` puis en utilisant la commande `docker build`.</span><span class="sxs-lookup"><span data-stu-id="67983-273">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running `dotnet publish`, and then use the `docker build` command.</span></span>

<span data-ttu-id="67983-274">Cette action crée une image Docker appelée `cesardl/netcore-webapi-microservice-docker:first`.</span><span class="sxs-lookup"><span data-stu-id="67983-274">This will create a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first`.</span></span> <span data-ttu-id="67983-275">Dans ce cas, :first est une balise qui représente une version spécifique.</span><span class="sxs-lookup"><span data-stu-id="67983-275">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="67983-276">Vous pouvez répéter cette étape pour chaque image personnalisée à créer pour votre application Docker composée.</span><span class="sxs-lookup"><span data-stu-id="67983-276">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="67983-277">Quand une application est constituée de plusieurs conteneurs (une application multiconteneur), vous pouvez également utiliser la commande `docker-compose up --build` pour créer toutes les images associées avec une seule commande à l’aide des métadonnées exposées dans les fichiers docker-compose.yml associés.</span><span class="sxs-lookup"><span data-stu-id="67983-277">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the `docker-compose up --build` command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="67983-278">Vous pouvez rechercher les images existantes dans votre dépôt local avec la commande docker images (voir la figure 5-6).</span><span class="sxs-lookup"><span data-stu-id="67983-278">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![Sortie de console de la commande docker images, montrant les images existantes.](./media/docker-app-development-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="67983-280">**Figure 5-6.**</span><span class="sxs-lookup"><span data-stu-id="67983-280">**Figure 5-6.**</span></span> <span data-ttu-id="67983-281">Affichage des images existantes à l’aide de la commande docker images</span><span class="sxs-lookup"><span data-stu-id="67983-281">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="67983-282">Création d’images Docker avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="67983-282">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="67983-283">Quand vous utilisez Visual Studio pour créer un projet avec la prise en charge de Docker, vous ne créez pas une image explicitement.</span><span class="sxs-lookup"><span data-stu-id="67983-283">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="67983-284">En fait, l’image est créée quand vous appuyez sur **F5** (ou **Ctrl-F5** ) pour exécuter l’application ou le service dockerisé.</span><span class="sxs-lookup"><span data-stu-id="67983-284">Instead, the image is created for you when you press **F5** (or **Ctrl-F5** ) to run the dockerized application or service.</span></span> <span data-ttu-id="67983-285">Cette étape est automatique dans Visual Studio. Vous ne la verrez donc pas à l’écran, mais il est important d’en comprendre le mécanisme.</span><span class="sxs-lookup"><span data-stu-id="67983-285">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![Image pour l’étape 4 facultative.](./media/docker-app-development-workflow/step-4-define-services-docker-compose-yml.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="67983-287">Étape 4.</span><span class="sxs-lookup"><span data-stu-id="67983-287">Step 4.</span></span> <span data-ttu-id="67983-288">Définir vos services dans docker-compose.yml lors de la création d’une application Docker multiconteneur</span><span class="sxs-lookup"><span data-stu-id="67983-288">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="67983-289">Le fichier [docker-compose.yml](https://docs.docker.com/compose/compose-file/) vous permet de définir un ensemble de services à déployer ensemble comme application composée avec les commandes de déploiement.</span><span class="sxs-lookup"><span data-stu-id="67983-289">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span> <span data-ttu-id="67983-290">Il configure également ses relations de dépendance et la configuration d’exécution.</span><span class="sxs-lookup"><span data-stu-id="67983-290">It also configures its dependency relations and run-time configuration.</span></span>

<span data-ttu-id="67983-291">Pour utiliser un fichier docker-compose.yml, vous devez d’abord le créer dans votre dossier solution principal ou racine. Le contenu du fichier doit être semblable à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="67983-291">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

```yml
version: '3.4'

services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog-api
      - OrderingUrl=http://ordering-api
    ports:
      - "80:80"
    depends_on:
      - catalog-api
      - ordering-api

  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Port=1433;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sqldata

  ordering-api:
    image: eshop/ordering-api
    environment:
      - ConnectionString=Server=sqldata;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sqldata

  sqldata:
    image: mcr.microsoft.com/mssql/server:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

<span data-ttu-id="67983-292">Ce fichier docker-compose.yml est une version simplifiée et fusionnée.</span><span class="sxs-lookup"><span data-stu-id="67983-292">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="67983-293">Il contient des données de configuration statiques pour chaque conteneur (comme le nom de l’image personnalisée), qui sont toujours nécessaires, ainsi que des informations de configuration variables selon l’environnement de déploiement, comme la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="67983-293">It contains static configuration data for each container (like the name of the custom image), which is always required, and configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="67983-294">Dans des sections ultérieures, vous découvrez comment fractionner la configuration du fichier docker-compose.yml en plusieurs fichiers docker-compose et remplacer les valeurs en fonction de l’environnement et du type d’exécution (debug ou release).</span><span class="sxs-lookup"><span data-stu-id="67983-294">In later sections, you will learn how to split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="67983-295">L’exemple de fichier docker-compose.yml définit quatre services : le service `webmvc` (une application web), deux microservices (`ordering-api` et `basket-api`), et un conteneur de source de données (`sqldata`), basé sur SQL Server pour Linux exécuté comme un conteneur.</span><span class="sxs-lookup"><span data-stu-id="67983-295">The docker-compose.yml file example defines four services: the `webmvc` service (a web application), two microservices (`ordering-api` and `basket-api`), and one data source container, `sqldata`, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="67983-296">Comme chaque service est déployé comme un conteneur, ils ont chacun besoin d’une image Docker.</span><span class="sxs-lookup"><span data-stu-id="67983-296">Each service will be deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="67983-297">Le fichier docker-compose.yml spécifie les conteneurs utilisés, mais aussi la configuration de chaque conteneur.</span><span class="sxs-lookup"><span data-stu-id="67983-297">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="67983-298">Par exemple, la définition du conteneur `webmvc` dans le fichier .yml :</span><span class="sxs-lookup"><span data-stu-id="67983-298">For instance, the `webmvc` container definition in the .yml file:</span></span>

- <span data-ttu-id="67983-299">Utilise une image `eshop/web:latest` prédéfinie.</span><span class="sxs-lookup"><span data-stu-id="67983-299">Uses a pre-built `eshop/web:latest` image.</span></span> <span data-ttu-id="67983-300">Toutefois, vous pouvez également configurer l’image à créer à l’exécution de docker-compose avec une configuration supplémentaire basée sur une section :build dans le fichier docker-compose.</span><span class="sxs-lookup"><span data-stu-id="67983-300">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="67983-301">Initialise deux variables d’environnement (CatalogUrl et OrderingUrl).</span><span class="sxs-lookup"><span data-stu-id="67983-301">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="67983-302">Transfère le port exposé 80 sur le conteneur vers le port externe 80 sur la machine hôte.</span><span class="sxs-lookup"><span data-stu-id="67983-302">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="67983-303">Lie l’application web aux services catalog et ordering avec le paramètre depends_on.</span><span class="sxs-lookup"><span data-stu-id="67983-303">Links the web app to the catalog and ordering service with the depends_on setting.</span></span> <span data-ttu-id="67983-304">Cela force le service à attendre le démarrage de ces services.</span><span class="sxs-lookup"><span data-stu-id="67983-304">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="67983-305">Nous reparlerons du fichier docker-compose.yml dans une section ultérieure, quand nous expliquerons comment implémenter des microservices et des applications multiconteneurs.</span><span class="sxs-lookup"><span data-stu-id="67983-305">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2019"></a><span data-ttu-id="67983-306">Utilisation de docker-compose. yml dans Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="67983-306">Working with docker-compose.yml in Visual Studio 2019</span></span>

<span data-ttu-id="67983-307">Outre l’ajout d’un fichier dockerfile à un projet, comme nous l’avons mentionné précédemment, Visual Studio 2017 (à partir de la version 15,8 sur) peut ajouter la prise en charge d’Orchestrator pour Docker Compose à une solution.</span><span class="sxs-lookup"><span data-stu-id="67983-307">Besides adding a Dockerfile to a project, as we mentioned before, Visual Studio 2017 (from version 15.8 on) can add orchestrator support for Docker Compose to a solution.</span></span>

<span data-ttu-id="67983-308">Quand vous ajoutez pour la première fois la prise en charge d’un orchestrateur de conteneurs, comme indiqué dans la Figure 5-7, Visual Studio crée le fichier Dockerfile pour le projet ainsi qu’un projet (section service) dans votre solution avec plusieurs fichiers `docker-compose*.yml` généraux, puis ajoute le projet à ces fichiers.</span><span class="sxs-lookup"><span data-stu-id="67983-308">When you add container orchestrator support, as shown in Figure 5-7, for the first time, Visual Studio creates the Dockerfile for the project and creates a new (service section) project in your solution with several global `docker-compose*.yml` files, and then adds the project to those files.</span></span> <span data-ttu-id="67983-309">Vous pouvez ensuite ouvrir les fichiers docker-compose.yml et les mettre à jour avec des fonctionnalités supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="67983-309">You can then open the docker-compose.yml files and update them with additional features.</span></span>

<span data-ttu-id="67983-310">Vous devez répéter cette opération pour chaque projet que vous souhaitez inclure dans le fichier docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="67983-310">You have to repeat this operation form every project you want to include in the docker-compose.yml file.</span></span>

<span data-ttu-id="67983-311">Au moment de la rédaction de cet article, Visual Studio prend en charge les orchestrateurs **docker compose** et **Kubernetes/Helm** .</span><span class="sxs-lookup"><span data-stu-id="67983-311">At the time of this writing, Visual Studio supports **Docker Compose** and **Kubernetes/Helm** orchestrators.</span></span>

![Capture d’écran montrant l’option de prise en charge de Container Orchestrator dans le menu contextuel du projet.](./media/docker-app-development-workflow/add-container-orchestrator-support-option.png)

<span data-ttu-id="67983-313">**Figure 5-7**.</span><span class="sxs-lookup"><span data-stu-id="67983-313">**Figure 5-7**.</span></span> <span data-ttu-id="67983-314">Ajout de la prise en charge de l’ancrage dans Visual Studio 2019 en cliquant avec le bouton droit sur un projet ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="67983-314">Adding Docker support in Visual Studio 2019 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="67983-315">Après avoir ajouté la prise en charge des orchestrateurs à votre solution dans Visual Studio, vous voyez également un nouveau nœud (dans le fichier projet `docker-compose.dcproj`) dans l’Explorateur de solutions. Ce nœud contient les fichiers docker-compose.yml qui ont été ajoutés (voir la figure 5-8).</span><span class="sxs-lookup"><span data-stu-id="67983-315">After you add orchestrator support to your solution in Visual Studio, you will also see a new node (in the `docker-compose.dcproj` project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![Capture d’écran du nœud dockr-compose dans Explorateur de solutions.](./media/docker-app-development-workflow/docker-compose-tree-node.png)

<span data-ttu-id="67983-317">**Figure 5-8**.</span><span class="sxs-lookup"><span data-stu-id="67983-317">**Figure 5-8**.</span></span> <span data-ttu-id="67983-318">Le nœud de l’arborescence **dockr-compose** ajouté dans Visual Studio 2019 Explorateur de solutions</span><span class="sxs-lookup"><span data-stu-id="67983-318">The **docker-compose** tree node added in Visual Studio 2019 Solution Explorer</span></span>

<span data-ttu-id="67983-319">Vous pouvez déployer une application multiconteneur avec un seul fichier docker-compose.yml en utilisant la commande `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="67983-319">You could deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span> <span data-ttu-id="67983-320">Toutefois, Visual Studio ajoute un groupe de ces fichiers pour vous permettre de remplacer les valeurs selon l’environnement (développement ou production) et le type d’exécution (release ou debug).</span><span class="sxs-lookup"><span data-stu-id="67983-320">However, Visual Studio adds a group of them so you can override values depending on the environment (development or production) and execution type (release or debug).</span></span> <span data-ttu-id="67983-321">Cette fonctionnalité sera expliquée dans des sections ultérieures.</span><span class="sxs-lookup"><span data-stu-id="67983-321">This capability will be explained in later sections.</span></span>

![Image de l’étape 5.](./media/docker-app-development-workflow/step-5-run-containers-compose-app.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="67983-323">Étape 5.</span><span class="sxs-lookup"><span data-stu-id="67983-323">Step 5.</span></span> <span data-ttu-id="67983-324">Générer et exécuter votre application Docker</span><span class="sxs-lookup"><span data-stu-id="67983-324">Build and run your Docker application</span></span>

<span data-ttu-id="67983-325">Si votre application n’a qu’un seul conteneur, vous pouvez l’exécuter en la déployant sur l’hôte Docker (machine virtuelle ou serveur physique).</span><span class="sxs-lookup"><span data-stu-id="67983-325">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="67983-326">Toutefois, si votre application contient plusieurs services, vous pouvez la déployer en tant qu’application composée, soit à l’aide d’une seule commande CLI ( `docker-compose up)` , soit avec Visual Studio, qui utilisera cette commande en coulisses).</span><span class="sxs-lookup"><span data-stu-id="67983-326">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (`docker-compose up)`, or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="67983-327">Voyons les différentes options.</span><span class="sxs-lookup"><span data-stu-id="67983-327">Let's look at the different options.</span></span>

### <a name="option-a-running-a-single-container-application"></a><span data-ttu-id="67983-328">Option A : exécution d’une application à conteneur unique</span><span class="sxs-lookup"><span data-stu-id="67983-328">Option A: Running a single-container application</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="67983-329">Utilisation de l’interface CLI Docker</span><span class="sxs-lookup"><span data-stu-id="67983-329">Using Docker CLI</span></span>

<span data-ttu-id="67983-330">Vous pouvez exécuter un conteneur Docker à l’aide de la commande `docker run`, comme indiqué dans la figure 5-9 :</span><span class="sxs-lookup"><span data-stu-id="67983-330">You can run a Docker container using the `docker run` command, as shown in Figure 5-9:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="67983-331">La commande ci-dessus crée une instance de conteneur à partir de l’image spécifiée, chaque fois qu’elle est exécutée.</span><span class="sxs-lookup"><span data-stu-id="67983-331">The above command will create a new container instance from the specified image, every time it's run.</span></span> <span data-ttu-id="67983-332">Vous pouvez utiliser le `--name` paramètre pour attribuer un nom au conteneur, puis utiliser `docker start {name}` (ou utiliser l’ID de conteneur ou le nom automatique) pour exécuter une instance de conteneur existante.</span><span class="sxs-lookup"><span data-stu-id="67983-332">You can use the `--name` parameter to give a name to the container and then use `docker start {name}` (or use the container ID or automatic name) to run an existing container instance.</span></span>

![Capture d’écran de l’exécution d’un conteneur Dockr à l’aide de la commande dockr Run.](./media/docker-app-development-workflow/use-docker-run-command.png)

<span data-ttu-id="67983-334">**Figure 5-9**.</span><span class="sxs-lookup"><span data-stu-id="67983-334">**Figure 5-9**.</span></span> <span data-ttu-id="67983-335">Exécution d’un conteneur Docker à l’aide de la commande docker run</span><span class="sxs-lookup"><span data-stu-id="67983-335">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="67983-336">Dans ce cas, la commande lie le port interne 5000 du conteneur au port 80 de la machine hôte.</span><span class="sxs-lookup"><span data-stu-id="67983-336">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="67983-337">Cela signifie que l’hôte écoute le port 80 et transfère le port sur le port 5000 sur le conteneur.</span><span class="sxs-lookup"><span data-stu-id="67983-337">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

<span data-ttu-id="67983-338">Le hachage indiqué est l’ID de conteneur et un nom lisible aléatoire lui est également attribué si l' `--name` option n’est pas utilisée.</span><span class="sxs-lookup"><span data-stu-id="67983-338">The hash shown is the container ID and it's also assigned a random readable name if the `--name` option is not used.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="67983-339">Utilisation de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="67983-339">Using Visual Studio</span></span>

<span data-ttu-id="67983-340">Si vous n’avez pas ajouté la prise en charge de l’orchestrateur de conteneurs, vous pouvez également exécuter une application monoconteneur dans Visual Studio en appuyant sur **Ctrl-F5** et vous pouvez aussi utiliser **F5** pour déboguer l’application dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="67983-340">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **Ctrl-F5** and you can also use **F5** to debug the application within the container.</span></span> <span data-ttu-id="67983-341">Avec docker run, le conteneur s’exécute localement.</span><span class="sxs-lookup"><span data-stu-id="67983-341">The container runs locally using docker run.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="67983-342">Option B : Exécution d’une application multiconteneur</span><span class="sxs-lookup"><span data-stu-id="67983-342">Option B: Running a multi-container application</span></span>

<span data-ttu-id="67983-343">Dans la plupart des scénarios d’entreprise, une application Docker est composée de plusieurs services, ce qui signifie que vous devez exécuter une application multiconteneur, comme illustré à la figure 5-10.</span><span class="sxs-lookup"><span data-stu-id="67983-343">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![Machine virtuelle avec plusieurs conteneurs Docker](./media/docker-app-development-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="67983-345">**Figure 5-10**.</span><span class="sxs-lookup"><span data-stu-id="67983-345">**Figure 5-10**.</span></span> <span data-ttu-id="67983-346">Machine virtuelle avec des conteneurs Docker déployés</span><span class="sxs-lookup"><span data-stu-id="67983-346">VM with Docker containers deployed</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="67983-347">Utilisation de l’interface CLI Docker</span><span class="sxs-lookup"><span data-stu-id="67983-347">Using Docker CLI</span></span>

<span data-ttu-id="67983-348">Pour exécuter une application multiconteneur avec l’interface CLI Docker, vous utilisez la commande `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="67983-348">To run a multi-container application with the Docker CLI, you use the `docker-compose up` command.</span></span> <span data-ttu-id="67983-349">Cette commande utilise le fichier **docker-compose. yml** que vous avez au niveau de la solution pour déployer une application à plusieurs conteneurs.</span><span class="sxs-lookup"><span data-stu-id="67983-349">This command uses the **docker-compose.yml** file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="67983-350">La figure 5-11 montre les résultats de l’exécution de la commande à partir de votre répertoire de solution principal, qui contient le fichier docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="67983-350">Figure 5-11 shows the results when running the command from your main solution directory, which contains the docker-compose.yml file.</span></span>

![Vue de l’écran d’exécution de la commande docker-compose up](./media/docker-app-development-workflow/results-docker-compose-up.png)

<span data-ttu-id="67983-352">**Figure 5-11**.</span><span class="sxs-lookup"><span data-stu-id="67983-352">**Figure 5-11**.</span></span> <span data-ttu-id="67983-353">Exemple de résultats de l’exécution de la commande docker-compose up</span><span class="sxs-lookup"><span data-stu-id="67983-353">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="67983-354">Après l’exécution de la commande docker-compose up, l’application et ses conteneurs associés sont déployés sur votre hôte Docker, comme indiqué dans la figure 5-10.</span><span class="sxs-lookup"><span data-stu-id="67983-354">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as depicted in Figure 5-10.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="67983-355">Utilisation de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="67983-355">Using Visual Studio</span></span>

<span data-ttu-id="67983-356">L’exécution d’une application à plusieurs conteneurs à l’aide de Visual Studio 2019 ne peut pas être plus simple.</span><span class="sxs-lookup"><span data-stu-id="67983-356">Running a multi-container application using Visual Studio 2019 can't get any simpler.</span></span> <span data-ttu-id="67983-357">Appuyez simplement sur **Ctrl-F5** pour exécuter ou **F5** pour déboguer, comme d’habitude, en configurant le projet **docker-compose** comme projet de démarrage.</span><span class="sxs-lookup"><span data-stu-id="67983-357">You just press **Ctrl-F5** to run or **F5** to debug, as usual, setting up the **docker-compose** project as the startup project.</span></span>  <span data-ttu-id="67983-358">Visual Studio gère toutes les opérations d’installation nécessaires. vous pouvez donc créer des points d’arrêt comme d’habitude et déboguer ce qui est finalement devenu des processus indépendants s’exécutant dans des « serveurs distants », avec le débogueur déjà attaché, comme c’est le cas.</span><span class="sxs-lookup"><span data-stu-id="67983-358">Visual Studio handles all needed setup, so you can create breakpoints as usual and debug what finally become independent processes running in "remote servers", with the debugger already attached, just like that.</span></span>

<span data-ttu-id="67983-359">Comme nous l’avons mentionné plus haut, chaque fois que vous ajoutez la prise en charge de la solution Docker à un projet dans une solution, ce projet est configuré dans le fichier docker-compose.yml global (au niveau de la solution), ce qui vous permet d’exécuter ou de déboguer la solution dans son intégralité.</span><span class="sxs-lookup"><span data-stu-id="67983-359">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="67983-360">Visual Studio démarre un conteneur pour chaque projet pour lequel la prise en charge de la solution Docker est activée, puis il effectue automatiquement toutes les étapes internes (dotnet publish, docker build, etc.).</span><span class="sxs-lookup"><span data-stu-id="67983-360">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="67983-361">Si vous voulez rentrer dans les détails, jetez un œil au fichier :</span><span class="sxs-lookup"><span data-stu-id="67983-361">If you want to take a peek at all the drudgery, take a look at the file:</span></span>

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

<span data-ttu-id="67983-362">Le point important ici est que, comme illustré dans la figure 5-12, dans Visual Studio 2019, il existe une commande d' **ancrage** supplémentaire pour l’action touche F5.</span><span class="sxs-lookup"><span data-stu-id="67983-362">The important point here is that, as shown in Figure 5-12, in Visual Studio 2019 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="67983-363">Cette option vous permet d’exécuter ou de déboguer une application multiconteneur en exécutant tous les conteneurs qui sont définis dans les fichiers docker-compose.yml au niveau de la solution.</span><span class="sxs-lookup"><span data-stu-id="67983-363">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="67983-364">Pour déboguer des solutions multiconteneurs, vous pouvez définir plusieurs points d’arrêt, chaque point d’arrêt dans un projet (conteneur) distinct, et, pendant le débogage à partir de Visual Studio, vous vous arrêtez aux points d’arrêt définis dans les différents projets et exécutés sur des conteneurs différents.</span><span class="sxs-lookup"><span data-stu-id="67983-364">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![Capture d’écran de la barre d’outils de débogage exécutant un projet dockr-compose.](./media/docker-app-development-workflow/debug-toolbar-docker-compose-project.png)

<span data-ttu-id="67983-366">**Figure 5-12**.</span><span class="sxs-lookup"><span data-stu-id="67983-366">**Figure 5-12**.</span></span> <span data-ttu-id="67983-367">Exécution d’applications à plusieurs conteneurs dans Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="67983-367">Running multi-container apps in Visual Studio 2019</span></span>

### <a name="additional-resources"></a><span data-ttu-id="67983-368">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="67983-368">Additional resources</span></span>

- <span data-ttu-id="67983-369">**Déployer un conteneur ASP.NET sur un hôte de l’arrimeur distant** </span><span class="sxs-lookup"><span data-stu-id="67983-369">**Deploy an ASP.NET container to a remote Docker host** </span></span>\
  <https://docs.microsoft.com/visualstudio/containers/hosting-web-apps-in-docker>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="67983-370">Note sur le test et le déploiement avec des orchestrateurs</span><span class="sxs-lookup"><span data-stu-id="67983-370">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="67983-371">Les commandes docker-compose up et docker run (ou l’exécution et le débogage des conteneurs dans Visual Studio) sont une approche appropriée pour tester les conteneurs dans votre environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="67983-371">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="67983-372">Toutefois, vous ne devez pas utiliser cette approche pour les déploiements de production, où vous devez cibler des orchestrateurs comme [Kubernetes](https://kubernetes.io/) ou [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span><span class="sxs-lookup"><span data-stu-id="67983-372">But you should not use this approach for production deployments, where you should target orchestrators like [Kubernetes](https://kubernetes.io/) or [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span></span> <span data-ttu-id="67983-373">Si vous utilisez Kubernetes, vous devez utiliser des [gousses](https://kubernetes.io/docs/concepts/workloads/pods/pod/) pour organiser les conteneurs et les [services](https://kubernetes.io/docs/concepts/services-networking/service/) en réseau.</span><span class="sxs-lookup"><span data-stu-id="67983-373">If you're using Kubernetes, you have to use [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/) to organize containers and [services](https://kubernetes.io/docs/concepts/services-networking/service/) to network them.</span></span> <span data-ttu-id="67983-374">Vous utilisez également des [déploiements](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) pour organiser la création et la modification des pods.</span><span class="sxs-lookup"><span data-stu-id="67983-374">You also use [deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) to organize pod creation and modification.</span></span>

![Image de l’étape 6.](./media/docker-app-development-workflow/step-6-test-app-microservices.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="67983-376">Étape 6.</span><span class="sxs-lookup"><span data-stu-id="67983-376">Step 6.</span></span> <span data-ttu-id="67983-377">Tester votre application Docker à l’aide de l’hôte Docker local</span><span class="sxs-lookup"><span data-stu-id="67983-377">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="67983-378">Cette étape varie en fonction de ce que fait votre application.</span><span class="sxs-lookup"><span data-stu-id="67983-378">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="67983-379">Dans une application web .NET Core simple qui est déployée comme service ou conteneur unique, vous pouvez accéder au service en ouvrant un navigateur sur l’hôte Docker et en accédant à ce site (voir la figure 5-13).</span><span class="sxs-lookup"><span data-stu-id="67983-379">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="67983-380">(Si la configuration dans le fichier Dockerfile mappe le conteneur à un autre port sur l’hôte que le port 80, incluez le port de l’hôte dans l’URL.)</span><span class="sxs-lookup"><span data-stu-id="67983-380">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![Capture d’écran de la réponse de localhost/API/values.](./media/docker-app-development-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="67983-382">**Figure 5-13**.</span><span class="sxs-lookup"><span data-stu-id="67983-382">**Figure 5-13**.</span></span> <span data-ttu-id="67983-383">Exemple de test de l’application Docker en local avec localhost</span><span class="sxs-lookup"><span data-stu-id="67983-383">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="67983-384">Si localhost ne pointe pas vers l’IP hôte de Docker (contrairement à la configuration par défaut quand vous utilisez Docker CE), utilisez l’adresse IP de la carte réseau de votre machine pour pouvoir accéder à votre service.</span><span class="sxs-lookup"><span data-stu-id="67983-384">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine's network card.</span></span>

<span data-ttu-id="67983-385">Notez que cette URL dans le navigateur utilise le port 80 pour l’exemple de conteneur particulier présenté ici.</span><span class="sxs-lookup"><span data-stu-id="67983-385">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="67983-386">Toutefois, en interne, les requêtes sont redirigées vers le port 5000, car le déploiement a été fait de cette façon avec la commande docker run, comme nous l’avons expliqué dans une étape précédente.</span><span class="sxs-lookup"><span data-stu-id="67983-386">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="67983-387">Vous pouvez également tester l’application en exécutant curl à partir du terminal, comme indiqué à la figure 5-14.</span><span class="sxs-lookup"><span data-stu-id="67983-387">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="67983-388">Dans une installation Docker sur Windows, l’adresse IP par défaut de l’hôte Docker est toujours 10.0.75.1 en plus de l’adresse IP réelle de votre machine.</span><span class="sxs-lookup"><span data-stu-id="67983-388">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine's actual IP address.</span></span>

![Sortie de la console de l’obtention de l' http://10.0.75.1/API/values accolade.](./media/docker-app-development-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="67983-390">**Figure 5-14**.</span><span class="sxs-lookup"><span data-stu-id="67983-390">**Figure 5-14**.</span></span> <span data-ttu-id="67983-391">Exemple de test de l’application Docker en local avec curl</span><span class="sxs-lookup"><span data-stu-id="67983-391">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2019"></a><span data-ttu-id="67983-392">Test et débogage de conteneurs avec Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="67983-392">Testing and debugging containers with Visual Studio 2019</span></span>

<span data-ttu-id="67983-393">Lors de l’exécution et du débogage des conteneurs avec Visual Studio 2019, vous pouvez déboguer l’application .NET de la même façon que vous le feriez lors de l’exécution sans conteneurs.</span><span class="sxs-lookup"><span data-stu-id="67983-393">When running and debugging the containers with Visual Studio 2019, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="67983-394">Test et débogage sans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="67983-394">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="67983-395">Si vous développez à l’aide de l’approche éditeur/CLI, le débogage des conteneurs est plus difficile et vous souhaiterez probablement déboguer en générant des traces.</span><span class="sxs-lookup"><span data-stu-id="67983-395">If you're developing using the editor/CLI approach, debugging containers is more difficult and you'll probably want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="67983-396">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="67983-396">Additional resources</span></span>

- <span data-ttu-id="67983-397">**Débogage d’applications dans un conteneur d’ancrage local** </span><span class="sxs-lookup"><span data-stu-id="67983-397">**Debugging apps in a local Docker container** </span></span>\
  [https://docs.microsoft.com/visualstudio/containers/edit-and-refresh](/visualstudio/containers/edit-and-refresh)

- <span data-ttu-id="67983-398">**Steve Lasker. Générez, déboguez et déployez des applications ASP.NET Core avec l’arrimeur.**</span><span class="sxs-lookup"><span data-stu-id="67983-398">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="67983-399">Vidéo.</span><span class="sxs-lookup"><span data-stu-id="67983-399">Video.</span></span> \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115>

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="67983-400">Workflow simplifié du développement de conteneurs avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="67983-400">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="67983-401">En effet, le workflow avec Visual Studio est beaucoup plus simple que si vous utilisez un éditeur ou une CLI.</span><span class="sxs-lookup"><span data-stu-id="67983-401">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="67983-402">La plupart des étapes requises par Docker liées aux fichiers Dockerfile et docker-compose.yml sont masquées ou simplifiées par Visual Studio, comme illustré à la figure 5-15.</span><span class="sxs-lookup"><span data-stu-id="67983-402">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

:::image type="complex" source="./media/docker-app-development-workflow/simplified-life-cycle-containerized-apps-docker-cli.png" alt-text="Diagramme montrant les cinq étapes simplifiées nécessaires à la création d’une application.":::
<span data-ttu-id="67983-404">Processus de développement pour les applications de l’arrimeur : 1-coder votre application, 2-écrire fichier dockerfile/s, 3-créer des images définies sur fichier dockerfile/s, 4-(facultatif) composer des services dans le fichier docker-compose. yml, 5-exécuter le conteneur ou l’application dockr-compose, 6-tester votre application ou vos microservices, 7-Push vers référentiel</span><span class="sxs-lookup"><span data-stu-id="67983-404">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span>
:::image-end:::

<span data-ttu-id="67983-405">**Figure 5-15**.</span><span class="sxs-lookup"><span data-stu-id="67983-405">**Figure 5-15**.</span></span> <span data-ttu-id="67983-406">Workflow simplifié du développement avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="67983-406">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="67983-407">De plus, notez que vous devez effectuer l’étape 2 (ajout de la prise en charge de Docker à vos projets) une seule fois.</span><span class="sxs-lookup"><span data-stu-id="67983-407">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="67983-408">Le workflow est donc similaire aux tâches de développement que vous avez l’habitude de faire dans le cadre d’un développement avec .NET.</span><span class="sxs-lookup"><span data-stu-id="67983-408">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="67983-409">Vous devez comprendre ce qui se passe en arrière-plan (le processus de création d’image, les images de base utilisées, le déploiement des conteneurs, etc.) et parfois vous devez modifier le fichier Dockerfile ou docker-compose.yml pour personnaliser les comportements.</span><span class="sxs-lookup"><span data-stu-id="67983-409">You need to know what is going on under the covers (the image build process, what base images you're using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="67983-410">Au final, Visual Studio simplifie considérablement la plupart des tâches et vous permet de développer beaucoup plus rapidement.</span><span class="sxs-lookup"><span data-stu-id="67983-410">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="67983-411">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="67983-411">Additional resources</span></span>

- <span data-ttu-id="67983-412">**Steve Lasker. Développement de l’amarrage .NET avec Visual Studio (2017)** </span><span class="sxs-lookup"><span data-stu-id="67983-412">**Steve Lasker. .NET Docker Development with Visual Studio (2017)** </span></span>\
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="67983-413">Utilisation de commandes PowerShell dans un fichier Dockerfile pour configurer des conteneurs Windows</span><span class="sxs-lookup"><span data-stu-id="67983-413">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span>

<span data-ttu-id="67983-414">Les [conteneurs Windows](/virtualization/windowscontainers/about/index) vous permettent de convertir vos applications Windows existantes en images Docker, puis de les déployer avec les mêmes outils que le reste de l’écosystème Docker.</span><span class="sxs-lookup"><span data-stu-id="67983-414">[Windows Containers](/virtualization/windowscontainers/about/index) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="67983-415">Pour utiliser les conteneurs Windows, vous exécutez des commandes PowerShell dans le fichier Dockerfile, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="67983-415">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```dockerfile
FROM mcr.microsoft.com/windows/servercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="67983-416">Dans ce cas, nous utilisons une image de base Windows Server Core (le paramètre FROM) et nous installons IIS à l’aide d’une commande PowerShell (le paramètre RUN).</span><span class="sxs-lookup"><span data-stu-id="67983-416">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="67983-417">De la même façon, vous pouvez également utiliser des commandes PowerShell pour configurer des composants supplémentaires comme ASP.NET 4.x, .NET 4.6 ou tout autre logiciel Windows.</span><span class="sxs-lookup"><span data-stu-id="67983-417">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="67983-418">Par exemple, la commande suivante dans un fichier Dockerfile configure ASP.NET 4.5 :</span><span class="sxs-lookup"><span data-stu-id="67983-418">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="67983-419">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="67983-419">Additional resources</span></span>

- <span data-ttu-id="67983-420">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="67983-420">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="67983-421">Exemples de commandes PowerShell à exécuter à partir de fichiers Dockerfile pour ajouter des fonctionnalités Windows.</span><span class="sxs-lookup"><span data-stu-id="67983-421">Example PowerShell commands to run from dockerfiles to include Windows features.</span></span>\
  <https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile>

>[!div class="step-by-step"]
><span data-ttu-id="67983-422">[Précédent](index.md) 
> [Suivant](../multi-container-microservice-net-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="67983-422">[Previous](index.md)
[Next](../multi-container-microservice-net-applications/index.md)</span></span>
