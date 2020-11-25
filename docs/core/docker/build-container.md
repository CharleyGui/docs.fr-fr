---
title: Tutoriel Conteneuriser une application avec Docker
description: Dans ce didacticiel, vous allez apprendre à créer un conteneur pour une application .NET Core avec l’arrimeur.
ms.date: 04/27/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7605f847a76907f4f9d0a451ba69332d6d174615
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724726"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="207ea-103">Didacticiel : Conteneuriser une application .NET Core</span><span class="sxs-lookup"><span data-stu-id="207ea-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="207ea-104">Dans ce didacticiel, vous allez apprendre à créer un conteneur pour une application .NET Core avec l’arrimeur.</span><span class="sxs-lookup"><span data-stu-id="207ea-104">In this tutorial, you'll learn how to containerize a .NET Core application with Docker.</span></span> <span data-ttu-id="207ea-105">Les conteneurs présentent de nombreuses fonctionnalités et avantages, tels que la mise en place d’une infrastructure immuable, la fourniture d’une architecture portable et l’évolutivité.</span><span class="sxs-lookup"><span data-stu-id="207ea-105">Containers have many features and benefits, such as being an immutable infrastructure, providing a portable architecture, and enabling scalability.</span></span> <span data-ttu-id="207ea-106">L’image vous permettra de créer des conteneurs pour votre environnement de développement local, votre cloud privé ou votre cloud public.</span><span class="sxs-lookup"><span data-stu-id="207ea-106">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="207ea-107">Dans ce tutoriel, vous allez :</span><span class="sxs-lookup"><span data-stu-id="207ea-107">In this tutorial, you:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="207ea-108">Créer et publier une application .NET Core simple</span><span class="sxs-lookup"><span data-stu-id="207ea-108">Create and publish a simple .NET Core app</span></span>
> - <span data-ttu-id="207ea-109">Créer et configurer un Dockerfile pour .NET Core</span><span class="sxs-lookup"><span data-stu-id="207ea-109">Create and configure a Dockerfile for .NET Core</span></span>
> - <span data-ttu-id="207ea-110">Générer une image Docker</span><span class="sxs-lookup"><span data-stu-id="207ea-110">Build a Docker image</span></span>
> - <span data-ttu-id="207ea-111">Créer et exécuter un conteneur Docker</span><span class="sxs-lookup"><span data-stu-id="207ea-111">Create and run a Docker container</span></span>

<span data-ttu-id="207ea-112">Vous découvrirez la création d’un conteneur Docker et les tâches de déploiement pour une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="207ea-112">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="207ea-113">La *plateforme d’ancrage* utilise le *moteur* de l’ancrage pour générer et empaqueter rapidement des applications en tant qu’images de l' *ancrage*.</span><span class="sxs-lookup"><span data-stu-id="207ea-113">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="207ea-114">Ces images sont écrites au format *Dockerfile* pour être déployées et exécutées dans un conteneur en couches.</span><span class="sxs-lookup"><span data-stu-id="207ea-114">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

> [!NOTE]
> <span data-ttu-id="207ea-115">Ce didacticiel ne concerne **pas** les applications ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="207ea-115">This tutorial **is not** for ASP.NET Core apps.</span></span> <span data-ttu-id="207ea-116">Si vous utilisez ASP.NET Core, consultez le didacticiel [apprendre à déconteneurr une application ASP.net Core](/aspnet/core/host-and-deploy/docker/building-net-docker-images) .</span><span class="sxs-lookup"><span data-stu-id="207ea-116">If you're using ASP.NET Core, see the [Learn how to containerize an ASP.NET Core application](/aspnet/core/host-and-deploy/docker/building-net-docker-images) tutorial.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="207ea-117">Prérequis</span><span class="sxs-lookup"><span data-stu-id="207ea-117">Prerequisites</span></span>

<span data-ttu-id="207ea-118">Installez les éléments requis suivants :</span><span class="sxs-lookup"><span data-stu-id="207ea-118">Install the following prerequisites:</span></span>

- <span data-ttu-id="207ea-119">[SDK .NET Core 3,1](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="207ea-119">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="207ea-120">Si .NET Core est installé, utilisez la commande `dotnet --info` pour identifier le Kit SDK que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="207ea-120">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>
- [<span data-ttu-id="207ea-121">Dockr Community Edition</span><span class="sxs-lookup"><span data-stu-id="207ea-121">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)
- <span data-ttu-id="207ea-122">Un dossier de travail temporaire pour le *Dockerfile* et un exemple d’application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="207ea-122">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="207ea-123">Dans ce didacticiel, le nom *docker-Worker* est utilisé comme dossier de travail.</span><span class="sxs-lookup"><span data-stu-id="207ea-123">In this tutorial, the name *docker-working* is used as the working folder.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="207ea-124">Créer une application .NET Core</span><span class="sxs-lookup"><span data-stu-id="207ea-124">Create .NET Core app</span></span>

<span data-ttu-id="207ea-125">Vous avez besoin d’une application .NET Core que le conteneur Docker exécutera.</span><span class="sxs-lookup"><span data-stu-id="207ea-125">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="207ea-126">Ouvrez votre terminal, créez un dossier de travail si ce n’est déjà fait, et accédez-y.</span><span class="sxs-lookup"><span data-stu-id="207ea-126">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="207ea-127">Dans le dossier de travail, exécutez la commande suivante pour créer un nouveau projet dans un sous-répertoire nommé *app*:</span><span class="sxs-lookup"><span data-stu-id="207ea-127">In the working folder, run the following command to create a new project in a subdirectory named *app*:</span></span>

```dotnetcli
dotnet new console -o App -n NetCore.Docker
```

<span data-ttu-id="207ea-128">Votre arborescence de dossiers doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="207ea-128">Your folder tree will look like the following:</span></span>

```
docker-working
    └──App
        ├──NetCore.Docker.csproj
        ├──Program.cs
        └──obj
            ├──NetCore.Docker.csproj.nuget.dgspec.json
            ├──NetCore.Docker.csproj.nuget.g.props
            ├──NetCore.Docker.csproj.nuget.g.targets
            ├──project.assets.json
            └──project.nuget.cache
```

<span data-ttu-id="207ea-129">La `dotnet new` commande crée un dossier nommé *app* et génère une application console « Hello World ».</span><span class="sxs-lookup"><span data-stu-id="207ea-129">The `dotnet new` command creates a new folder named *App* and generates a "Hello World" console application.</span></span> <span data-ttu-id="207ea-130">Modifiez les répertoires et accédez au dossier de l' *application* , à partir de votre session terminal.</span><span class="sxs-lookup"><span data-stu-id="207ea-130">Change directories and navigate into the *App* folder, from your terminal session.</span></span> <span data-ttu-id="207ea-131">Utilisez la `dotnet run` commande pour démarrer l’application.</span><span class="sxs-lookup"><span data-stu-id="207ea-131">Use the `dotnet run` command to start the app.</span></span> <span data-ttu-id="207ea-132">L’application s’exécute et s’affiche `Hello World!` sous la commande :</span><span class="sxs-lookup"><span data-stu-id="207ea-132">The application will run, and print `Hello World!` below the command:</span></span>

```dotnetcli
dotnet run
Hello World!
```

<span data-ttu-id="207ea-133">Le modèle par défaut crée une application qui s’imprime sur le terminal, puis se termine immédiatement.</span><span class="sxs-lookup"><span data-stu-id="207ea-133">The default template creates an app that prints to the terminal and then immediately terminates.</span></span> <span data-ttu-id="207ea-134">Pour ce tutoriel, vous utiliserez une application qui effectue une boucle indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="207ea-134">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="207ea-135">Ouvrez le fichier *Program.cs* dans un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="207ea-135">Open the *Program.cs* file in a text editor.</span></span>

> [!TIP]
> <span data-ttu-id="207ea-136">Si vous utilisez Visual Studio Code, à partir de la session Terminal précédente, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="207ea-136">If you're using Visual Studio Code, from the previous terminal session type the following command:</span></span>
>
> ```console
> code .
> ```
>
> <span data-ttu-id="207ea-137">Le dossier d' *application* qui contient le projet s’ouvre dans Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="207ea-137">This will open the *App* folder that contains the project in Visual Studio Code.</span></span>

<span data-ttu-id="207ea-138">Le *Program.cs* doit ressembler au code C# suivant :</span><span class="sxs-lookup"><span data-stu-id="207ea-138">The *Program.cs* should look like the following C# code:</span></span>

```csharp
using System;

namespace NetCore.Docker
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="207ea-139">Remplacez le fichier par le code suivant qui compte les nombres chaque seconde :</span><span class="sxs-lookup"><span data-stu-id="207ea-139">Replace the file with the following code that counts numbers every second:</span></span>

```csharp
using System;
using System.Threading.Tasks;

namespace NetCore.Docker
{
    class Program
    {
        static async Task Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                Console.WriteLine($"Counter: {++counter}");
                await Task.Delay(1000);
            }
        }
    }
}
```

<span data-ttu-id="207ea-140">Enregistrez le fichier et effectuez un nouveau avec `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="207ea-140">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="207ea-141">N’oubliez pas que cette application s’exécute indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="207ea-141">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="207ea-142">Utilisez la commande Annuler <kbd>Ctrl + C</kbd> pour l’arrêter.</span><span class="sxs-lookup"><span data-stu-id="207ea-142">Use the cancel command <kbd>Ctrl+C</kbd> to stop it.</span></span> <span data-ttu-id="207ea-143">Voici un exemple de sortie :</span><span class="sxs-lookup"><span data-stu-id="207ea-143">The following is an example output:</span></span>

```dotnetcli
dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="207ea-144">Si vous envoyez un nombre à l’application sur la ligne de commande, l’application comptera uniquement jusqu’à ce montant puis se fermera.</span><span class="sxs-lookup"><span data-stu-id="207ea-144">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="207ea-145">Effectuez un test avec `dotnet run -- 5` pour compter jusqu’à cinq.</span><span class="sxs-lookup"><span data-stu-id="207ea-145">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="207ea-146">Tous les paramètres après `--` sont transmis à votre application au lieu d’être transmis à la commande `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="207ea-146">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="207ea-147">Publier une application .NET Core</span><span class="sxs-lookup"><span data-stu-id="207ea-147">Publish .NET Core app</span></span>

<span data-ttu-id="207ea-148">Avant d’ajouter l’application .NET Core à l’image de l’ancrer, vous devez d’abord la publier.</span><span class="sxs-lookup"><span data-stu-id="207ea-148">Before adding the .NET Core app to the Docker image, first it must be published.</span></span> <span data-ttu-id="207ea-149">Il est préférable que le conteneur exécute la version publiée de l’application.</span><span class="sxs-lookup"><span data-stu-id="207ea-149">It is best to have the container run the published version of the app.</span></span> <span data-ttu-id="207ea-150">Pour publier l’application, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="207ea-150">To publish the app, run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="207ea-151">Cette commande compile votre application dans le dossier *publish*.</span><span class="sxs-lookup"><span data-stu-id="207ea-151">This command compiles your app to the *publish* folder.</span></span> <span data-ttu-id="207ea-152">Le chemin du dossier *publish* à partir du dossier de travail doit être `.\App\bin\Release\netcoreapp3.1\publish\`</span><span class="sxs-lookup"><span data-stu-id="207ea-152">The path to the *publish* folder from the working folder should be `.\App\bin\Release\netcoreapp3.1\publish\`</span></span>

#### <a name="windows"></a>[<span data-ttu-id="207ea-153">Windows</span><span class="sxs-lookup"><span data-stu-id="207ea-153">Windows</span></span>](#tab/windows)

<span data-ttu-id="207ea-154">Dans le dossier de l' *application* , accédez à la liste des répertoires du dossier de publication pour vérifier que le fichier de *NetCore.Docker.dll* a été créé.</span><span class="sxs-lookup"><span data-stu-id="207ea-154">From the *App* folder, get a directory listing of the publish folder to verify that the *NetCore.Docker.dll* file was created.</span></span>

```powershell
dir .\bin\Release\netcoreapp3.1\publish\

    Directory: C:\Users\dapine\App\bin\Release\netcoreapp3.1\publish

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        4/27/2020   8:27 AM            434 NetCore.Docker.deps.json
-a----        4/27/2020   8:27 AM           6144 NetCore.Docker.dll
-a----        4/27/2020   8:27 AM         171520 NetCore.Docker.exe
-a----        4/27/2020   8:27 AM            860 NetCore.Docker.pdb
-a----        4/27/2020   8:27 AM            154 NetCore.Docker.runtimeconfig.json
```

#### <a name="linux"></a>[<span data-ttu-id="207ea-155">Linux</span><span class="sxs-lookup"><span data-stu-id="207ea-155">Linux</span></span>](#tab/linux)

<span data-ttu-id="207ea-156">Utilisez la `ls` commande pour obtenir une liste de répertoires et vérifier que le fichier *NetCore.Docker.dll* a été créé.</span><span class="sxs-lookup"><span data-stu-id="207ea-156">Use the `ls` command to get a directory listing and verify that the *NetCore.Docker.dll* file was created.</span></span>

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
```

---

## <a name="create-the-dockerfile"></a><span data-ttu-id="207ea-157">Créer le Dockerfile</span><span class="sxs-lookup"><span data-stu-id="207ea-157">Create the Dockerfile</span></span>

<span data-ttu-id="207ea-158">Le fichier *Dockerfile* est utilisé par la commande `docker build` pour créer une image de conteneur.</span><span class="sxs-lookup"><span data-stu-id="207ea-158">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="207ea-159">Ce fichier est un fichier texte nommé *fichier dockerfile* qui n’a pas d’extension.</span><span class="sxs-lookup"><span data-stu-id="207ea-159">This file is a text file named *Dockerfile* that doesn't have an extension.</span></span>

<span data-ttu-id="207ea-160">Créez un fichier nommé *fichier dockerfile* dans le répertoire contenant le fichier *. csproj* et ouvrez-le dans un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="207ea-160">Create a file named *Dockerfile* in directory containing the *.csproj* and open it in a text editor.</span></span> <span data-ttu-id="207ea-161">Ce didacticiel utilise l’image d’exécution ASP.NET Core (qui contient l’image du Runtime .NET Core) et correspond à l’application console .NET Core.</span><span class="sxs-lookup"><span data-stu-id="207ea-161">This tutorial will use the ASP.NET Core runtime image (which contains the .NET Core runtime image) and corresponds with the .NET Core console application.</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:3.1
```

> [!NOTE]
> <span data-ttu-id="207ea-162">L’image ASP.NET Core Runtime est utilisée intentionnellement ici, bien que l' `mcr.microsoft.com/dotnet/runtime:3.1` image puisse avoir été utilisée.</span><span class="sxs-lookup"><span data-stu-id="207ea-162">The ASP.NET Core runtime image is used intentionally here, although the `mcr.microsoft.com/dotnet/runtime:3.1` image could have been used.</span></span>

<span data-ttu-id="207ea-163">Le `FROM` mot clé requiert un nom d’image de conteneur d’ancrage complet.</span><span class="sxs-lookup"><span data-stu-id="207ea-163">The `FROM` keyword requires a fully qualified Docker container image name.</span></span> <span data-ttu-id="207ea-164">Le Container Registry Microsoft (mcr.microsoft.com) est un syndicat de l’arrimeur d’ancrage, qui héberge des conteneurs accessibles publiquement.</span><span class="sxs-lookup"><span data-stu-id="207ea-164">The Microsoft Container Registry (MCR, mcr.microsoft.com) is a syndicate of Docker Hub - which hosts publicly accessible containers.</span></span> <span data-ttu-id="207ea-165">Le `dotnet/core` segment est le référentiel de conteneurs, où le `aspnet` segment est le nom de l’image de conteneur.</span><span class="sxs-lookup"><span data-stu-id="207ea-165">The `dotnet/core` segment is the container repository, where as the `aspnet` segment is the container image name.</span></span> <span data-ttu-id="207ea-166">L’image est marquée avec `3.1` , qui est utilisé pour le contrôle de version.</span><span class="sxs-lookup"><span data-stu-id="207ea-166">The image is tagged with `3.1`, which is used for versioning.</span></span> <span data-ttu-id="207ea-167">Par conséquent, `mcr.microsoft.com/dotnet/aspnet:3.1` est le Runtime .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="207ea-167">Thus, `mcr.microsoft.com/dotnet/aspnet:3.1` is the .NET Core 3.1 runtime.</span></span> <span data-ttu-id="207ea-168">Veillez à extraire la version du runtime qui correspond au runtime ciblé par votre kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="207ea-168">Make sure that you pull the runtime version that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="207ea-169">Par exemple, l’application créée dans la section précédente utilisait le kit de développement logiciel (SDK) .NET Core 3,1 et l’image de base référencée dans le *fichier dockerfile* est marquée avec **3,1**.</span><span class="sxs-lookup"><span data-stu-id="207ea-169">For example, the app created in the previous section used the .NET Core 3.1 SDK and the base image referred to in the *Dockerfile* is tagged with **3.1**.</span></span>

<span data-ttu-id="207ea-170">Enregistrez le fichier *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="207ea-170">Save the *Dockerfile* file.</span></span> <span data-ttu-id="207ea-171">La structure de répertoires du dossier de travail doit ressembler à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="207ea-171">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="207ea-172">Certains fichiers et dossiers de niveau supérieur ont été omis pour économiser de l’espace dans l’article :</span><span class="sxs-lookup"><span data-stu-id="207ea-172">Some of the deeper-level files and folders have been omitted to save space in the article:</span></span>

```
docker-working
    └──App
        ├──Dockerfile
        ├──NetCore.Docker.csproj
        ├──Program.cs
        ├──bin
        │   └──Release
        │       └──netcoreapp3.1
        │           └──publish
        │               ├──NetCore.Docker.deps.json
        │               ├──NetCore.Docker.exe
        │               ├──NetCore.Docker.dll
        │               ├──NetCore.Docker.pdb
        │               └──NetCore.Docker.runtimeconfig.json
        └──obj
            └──...
```

<span data-ttu-id="207ea-173">Dans votre terminal, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="207ea-173">From your terminal, run the following command:</span></span>

```console
docker build -t counter-image -f Dockerfile .
```

<span data-ttu-id="207ea-174">Docker traitera chaque ligne du *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="207ea-174">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="207ea-175">L’élément `.` de la commande `docker build` indique à Docker d’utiliser le dossier actif pour rechercher un *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="207ea-175">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="207ea-176">Cette commande génère l’image et crée un référentiel local nommé **Counter-image** qui pointe vers cette image.</span><span class="sxs-lookup"><span data-stu-id="207ea-176">This command builds the image and creates a local repository named **counter-image** that points to that image.</span></span> <span data-ttu-id="207ea-177">Une fois cette commande terminée, exécutez `docker images` pour afficher une liste des images installées :</span><span class="sxs-lookup"><span data-stu-id="207ea-177">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              e6780479db63        4 days ago          190MB
mcr.microsoft.com/dotnet/aspnet         3.1                 e6780479db63        4 days ago          190MB
```

<span data-ttu-id="207ea-178">Notez que les deux images partagent la même valeur **IMAGE ID**.</span><span class="sxs-lookup"><span data-stu-id="207ea-178">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="207ea-179">La valeur est la même dans les deux images, car la seule commande dans le *Dockerfile* basait la nouvelle image sur une image existante.</span><span class="sxs-lookup"><span data-stu-id="207ea-179">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="207ea-180">Nous allons ajouter trois commandes au *fichier dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="207ea-180">Let's add three commands to the *Dockerfile*.</span></span> <span data-ttu-id="207ea-181">Chaque commande crée une nouvelle couche d’image avec la commande finale représentant le point d’entrée de dépôt d' **image de compteur** vers.</span><span class="sxs-lookup"><span data-stu-id="207ea-181">Each command creates a new image layer with the final command representing the **counter-image** repository entry points to.</span></span>

```dockerfile
COPY bin/Release/netcoreapp3.1/publish/ App/
WORKDIR /App
ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
```

<span data-ttu-id="207ea-182">La commande `COPY` indique à Docker de copier le dossier spécifié sur votre ordinateur, dans un dossier du conteneur.</span><span class="sxs-lookup"><span data-stu-id="207ea-182">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="207ea-183">Dans cet exemple, le dossier *Publish* est copié dans un dossier nommé *app* dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="207ea-183">In this example, the *publish* folder is copied to a folder named *App* in the container.</span></span>

<span data-ttu-id="207ea-184">La `WORKDIR` commande modifie le **répertoire actif** à l’intérieur du conteneur en *app*.</span><span class="sxs-lookup"><span data-stu-id="207ea-184">The `WORKDIR` command changes the **current directory** inside of the container to *App*.</span></span>

<span data-ttu-id="207ea-185">La commande suivante, `ENTRYPOINT`, indique à Docker de configurer le conteneur afin de l’exécuter comme un fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="207ea-185">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="207ea-186">Au démarrage du conteneur, la commande `ENTRYPOINT` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="207ea-186">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="207ea-187">Lorsque cette commande se termine, le conteneur s’arrête automatiquement.</span><span class="sxs-lookup"><span data-stu-id="207ea-187">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="207ea-188">Dans votre terminal, exécutez `docker build -t counter-image -f Dockerfile .` puis, une fois la commande terminée, exécutez `docker images`.</span><span class="sxs-lookup"><span data-stu-id="207ea-188">From your terminal, run `docker build -t counter-image -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```console
docker build -t counter-image -f Dockerfile .
Sending build context to Docker daemon  1.117MB
Step 1/4 : FROM mcr.microsoft.com/dotnet/aspnet:3.1
 ---> e6780479db63
Step 2/4 : COPY bin/Release/netcoreapp3.1/publish/ App/
 ---> d1732740eed2
Step 3/4 : WORKDIR /App
 ---> Running in b1701a42f3ff
Removing intermediate container b1701a42f3ff
 ---> 919aab5b95e3
Step 4/4 : ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
 ---> Running in c12aebd26ced
Removing intermediate container c12aebd26ced
 ---> cd11c3df9b19
Successfully built cd11c3df9b19
Successfully tagged counter-image:latest

docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              cd11c3df9b19        41 seconds ago      190MB
mcr.microsoft.com/dotnet/aspnet         3.1                 e6780479db63        4 days ago          190MB
```

<span data-ttu-id="207ea-189">Chaque commande dans le *Dockerfile* a généré une couche et créé une valeur **IMAGE ID**.</span><span class="sxs-lookup"><span data-stu-id="207ea-189">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="207ea-190">L’ID de l' **image** finale (la vôtre sera différente) est **cd11c3df9b19** et suivant, vous allez créer un conteneur basé sur cette image.</span><span class="sxs-lookup"><span data-stu-id="207ea-190">The final **IMAGE ID** (yours will be different) is **cd11c3df9b19** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="207ea-191">Créez un conteneur.</span><span class="sxs-lookup"><span data-stu-id="207ea-191">Create a container</span></span>

<span data-ttu-id="207ea-192">Maintenant que vous disposez d’une image qui contient votre application, vous pouvez créer un conteneur.</span><span class="sxs-lookup"><span data-stu-id="207ea-192">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="207ea-193">Vous pouvez créer un conteneur de deux manières.</span><span class="sxs-lookup"><span data-stu-id="207ea-193">You can create a container in two ways.</span></span> <span data-ttu-id="207ea-194">Tout d’abord, créez un conteneur arrêté.</span><span class="sxs-lookup"><span data-stu-id="207ea-194">First, create a new container that is stopped.</span></span>

```console
docker create --name core-counter counter-image
0f281cb3af994fba5d962cc7d482828484ea14ead6bfe386a35e5088c0058851
```

<span data-ttu-id="207ea-195">La `docker create` commande ci-dessus crée un conteneur basé sur l’image **Counter-image** .</span><span class="sxs-lookup"><span data-stu-id="207ea-195">The `docker create` command from above will create a container based on the **counter-image** image.</span></span> <span data-ttu-id="207ea-196">Le résultat de cette commande affiche la valeur **CONTAINER ID** (la vôtre sera différente) du conteneur créé.</span><span class="sxs-lookup"><span data-stu-id="207ea-196">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="207ea-197">Pour afficher une liste de *tous* les conteneurs, utilisez la commande `docker ps -a` :</span><span class="sxs-lookup"><span data-stu-id="207ea-197">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED           STATUS     PORTS    NAMES
0f281cb3af99    counter-image    "dotnet NetCore.Dock…"    40 seconds ago    Created             core-counter
```

### <a name="manage-the-container"></a><span data-ttu-id="207ea-198">Gérer le conteneur</span><span class="sxs-lookup"><span data-stu-id="207ea-198">Manage the container</span></span>

<span data-ttu-id="207ea-199">Le conteneur a été créé avec un nom spécifique `core-counter` , ce nom est utilisé pour gérer le conteneur.</span><span class="sxs-lookup"><span data-stu-id="207ea-199">The container was created with a specific name `core-counter`, this name is used to manage the container.</span></span> <span data-ttu-id="207ea-200">L’exemple suivant utilise la commande `docker start` pour démarrer le conteneur, puis la commande `docker ps` pour afficher uniquement les conteneurs en cours d’exécution :</span><span class="sxs-lookup"><span data-stu-id="207ea-200">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
docker start core-counter
core-counter

docker ps
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS          PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    2 minutes ago    Up 11 seconds            core-counter
```

<span data-ttu-id="207ea-201">De même, la commande `docker stop` arrêtera le conteneur.</span><span class="sxs-lookup"><span data-stu-id="207ea-201">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="207ea-202">L’exemple suivant utilise la `docker stop` commande pour arrêter le conteneur, puis utilise la `docker ps` commande pour indiquer qu’aucun conteneur n’est en cours d’exécution :</span><span class="sxs-lookup"><span data-stu-id="207ea-202">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running:</span></span>

```console
docker stop core-counter
core-counter

docker ps
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="207ea-203">Se connecter à un conteneur</span><span class="sxs-lookup"><span data-stu-id="207ea-203">Connect to a container</span></span>

<span data-ttu-id="207ea-204">Lorsqu’un conteneur est en cours d’exécution, vous pouvez vous connecter à ce dernier pour afficher le résultat.</span><span class="sxs-lookup"><span data-stu-id="207ea-204">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="207ea-205">Utilisez les commandes `docker start` et `docker attach` pour démarrer le conteneur et observer le flux de sortie.</span><span class="sxs-lookup"><span data-stu-id="207ea-205">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="207ea-206">Dans cet exemple, la combinaison de touches <kbd>Ctrl + C</kbd> est utilisée pour se détacher du conteneur en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="207ea-206">In this example, the <kbd>Ctrl+C</kbd> keystroke is used to detach from the running container.</span></span> <span data-ttu-id="207ea-207">Cette séquence de touches met fin au processus dans le conteneur, sauf spécification contraire, qui arrête le conteneur.</span><span class="sxs-lookup"><span data-stu-id="207ea-207">This keystroke will end the process in the container unless otherwise specified, which would stop the container.</span></span> <span data-ttu-id="207ea-208">Le `--sig-proxy=false` paramètre garantit que <kbd>Ctrl + C</kbd> n’arrête pas le processus dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="207ea-208">The `--sig-proxy=false` parameter ensures that <kbd>Ctrl+C</kbd> will not stop the process in the container.</span></span>

<span data-ttu-id="207ea-209">Après vous être déconnecté du conteneur, reconnectez-vous pour vérifier qu’il est toujours en cours d’exécution et de comptage.</span><span class="sxs-lookup"><span data-stu-id="207ea-209">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```console
docker start core-counter
core-counter

docker attach --sig-proxy=false core-counter
Counter: 7
Counter: 8
Counter: 9
^C

docker attach --sig-proxy=false core-counter
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="207ea-210">Supprimer un conteneur</span><span class="sxs-lookup"><span data-stu-id="207ea-210">Delete a container</span></span>

<span data-ttu-id="207ea-211">Dans le cadre de cet article, vous devez éviter de vous retrouver avec des conteneurs inactifs.</span><span class="sxs-lookup"><span data-stu-id="207ea-211">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="207ea-212">Supprimez le conteneur que vous avez créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="207ea-212">Delete the container you previously created.</span></span> <span data-ttu-id="207ea-213">Si le conteneur est en cours d’exécution, arrêtez-le.</span><span class="sxs-lookup"><span data-stu-id="207ea-213">If the container is running, stop it.</span></span>

```console
docker stop core-counter
```

<span data-ttu-id="207ea-214">L’exemple suivant répertorie tous les conteneurs.</span><span class="sxs-lookup"><span data-stu-id="207ea-214">The following example lists all containers.</span></span> <span data-ttu-id="207ea-215">Il utilise ensuite la commande `docker rm` pour supprimer le conteneur, puis recherche une deuxième fois si des conteneurs sont en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="207ea-215">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS                        PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    7 minutes ago    Exited (143) 20 seconds ago            core-counter

docker rm core-counter
core-counter

docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="207ea-216">Exécution unique</span><span class="sxs-lookup"><span data-stu-id="207ea-216">Single run</span></span>

<span data-ttu-id="207ea-217">Docker fournit la commande `docker run` pour créer et exécuter le conteneur comme une commande unique.</span><span class="sxs-lookup"><span data-stu-id="207ea-217">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="207ea-218">Cette commande vous évite de devoir exécuter `docker create` , puis `docker start`.</span><span class="sxs-lookup"><span data-stu-id="207ea-218">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="207ea-219">Vous pouvez également définir cette commande pour supprimer automatiquement le conteneur lorsque le conteneur s’arrête.</span><span class="sxs-lookup"><span data-stu-id="207ea-219">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="207ea-220">Par exemple, utilisez `docker run -it --rm` pour effectuer deux opérations : utiliser automatiquement le terminal actuel pour se connecter au conteneur, puis supprimer ce conteneur une fois qu’il est terminé :</span><span class="sxs-lookup"><span data-stu-id="207ea-220">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```console
docker run -it --rm counter-image
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="207ea-221">Le conteneur transmet également des paramètres dans l’exécution de l’application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="207ea-221">The container also passes parameters into the execution of the .NET Core app.</span></span> <span data-ttu-id="207ea-222">Pour ordonner à l’application .NET Core de compter uniquement jusqu’à 3 passe 3.</span><span class="sxs-lookup"><span data-stu-id="207ea-222">To instruct the .NET Core app to count only to 3 pass in 3.</span></span>

```console
docker run -it --rm counter-image 3
Counter: 1
Counter: 2
Counter: 3
```

<span data-ttu-id="207ea-223">Avec `docker run -it` , la commande <kbd>Ctrl + C</kbd> arrête le processus en cours d’exécution dans le conteneur qui, à son tour, arrête le conteneur.</span><span class="sxs-lookup"><span data-stu-id="207ea-223">With `docker run -it`, the <kbd>Ctrl+C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="207ea-224">Comme le paramètre `--rm` a été fourni, le conteneur est automatiquement supprimé lorsque le processus est arrêté.</span><span class="sxs-lookup"><span data-stu-id="207ea-224">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="207ea-225">Vérifiez qu’il n’existe pas :</span><span class="sxs-lookup"><span data-stu-id="207ea-225">Verify that it doesn't exist:</span></span>

```console
docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="207ea-226">Modifier la commande ENTRYPOINT</span><span class="sxs-lookup"><span data-stu-id="207ea-226">Change the ENTRYPOINT</span></span>

<span data-ttu-id="207ea-227">La commande `docker run` vous permet également de modifier la commande `ENTRYPOINT` depuis le *Dockerfile* , puis d’exécuter un autre élément, mais uniquement pour ce conteneur.</span><span class="sxs-lookup"><span data-stu-id="207ea-227">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="207ea-228">Par exemple, utilisez la commande suivante pour exécuter `bash` ou `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="207ea-228">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="207ea-229">Modifiez la commande selon vos besoins.</span><span class="sxs-lookup"><span data-stu-id="207ea-229">Edit the command as necessary.</span></span>

#### <a name="windows"></a>[<span data-ttu-id="207ea-230">Windows</span><span class="sxs-lookup"><span data-stu-id="207ea-230">Windows</span></span>](#tab/windows)

<span data-ttu-id="207ea-231">Dans cet exemple, `ENTRYPOINT` est remplacé par `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="207ea-231">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="207ea-232">Appuyez sur <kbd>Ctrl + C</kbd> pour terminer le processus et arrêter le conteneur.</span><span class="sxs-lookup"><span data-stu-id="207ea-232"><kbd>Ctrl+C</kbd> is pressed to end the process and stop the container.</span></span>

```console
docker run -it --rm --entrypoint "cmd.exe" counter-image

Microsoft Windows [Version 10.0.17763.379]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\>dir
 Volume in drive C has no label.
 Volume Serial Number is 3005-1E84

 Directory of C:\

04/09/2019  08:46 AM    <DIR>          app
03/07/2019  10:25 AM             5,510 License.txt
04/02/2019  01:35 PM    <DIR>          Program Files
04/09/2019  01:06 PM    <DIR>          Users
04/02/2019  01:35 PM    <DIR>          Windows
               1 File(s)          5,510 bytes
               4 Dir(s)  21,246,517,248 bytes free

C:\>^C
```

#### <a name="linux"></a>[<span data-ttu-id="207ea-233">Linux</span><span class="sxs-lookup"><span data-stu-id="207ea-233">Linux</span></span>](#tab/linux)

<span data-ttu-id="207ea-234">Dans cet exemple, `ENTRYPOINT` est remplacé par `bash`.</span><span class="sxs-lookup"><span data-stu-id="207ea-234">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="207ea-235">La commande `exit` est exécutée, ce qui interrompt le processus et arrête le conteneur.</span><span class="sxs-lookup"><span data-stu-id="207ea-235">The `exit` command is run which ends the process and stop the container.</span></span>

```bash
docker run -it --rm --entrypoint "bash" counter-image
root@b735b9799abf:/App# ls
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.exe  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
root@b735b9799abf:/App# dotnet NetCore.Docker.dll 3
Counter: 1
Counter: 2
Counter: 3
root@b735b9799abf:/App# exit
exit
```

---

## <a name="essential-commands"></a><span data-ttu-id="207ea-236">Commandes essentielles</span><span class="sxs-lookup"><span data-stu-id="207ea-236">Essential commands</span></span>

<span data-ttu-id="207ea-237">L’ancrage possède de nombreuses commandes différentes qui créent, gèrent et interagissent avec les conteneurs et les images.</span><span class="sxs-lookup"><span data-stu-id="207ea-237">Docker has many different commands that create, manage, and interact with containers and images.</span></span> <span data-ttu-id="207ea-238">Ces commandes Docker sont essentielles à la gestion de vos conteneurs :</span><span class="sxs-lookup"><span data-stu-id="207ea-238">These Docker commands are essential to managing your containers:</span></span>

- [<span data-ttu-id="207ea-239">docker build</span><span class="sxs-lookup"><span data-stu-id="207ea-239">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
- [<span data-ttu-id="207ea-240">docker run</span><span class="sxs-lookup"><span data-stu-id="207ea-240">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
- [<span data-ttu-id="207ea-241">docker ps</span><span class="sxs-lookup"><span data-stu-id="207ea-241">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
- [<span data-ttu-id="207ea-242">docker stop</span><span class="sxs-lookup"><span data-stu-id="207ea-242">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
- [<span data-ttu-id="207ea-243">docker rm</span><span class="sxs-lookup"><span data-stu-id="207ea-243">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
- [<span data-ttu-id="207ea-244">docker rmi</span><span class="sxs-lookup"><span data-stu-id="207ea-244">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
- [<span data-ttu-id="207ea-245">image de l’ancrage</span><span class="sxs-lookup"><span data-stu-id="207ea-245">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="207ea-246">Nettoyer les ressources</span><span class="sxs-lookup"><span data-stu-id="207ea-246">Clean up resources</span></span>

<span data-ttu-id="207ea-247">Au cours de ce didacticiel, vous avez créé des conteneurs et des images.</span><span class="sxs-lookup"><span data-stu-id="207ea-247">During this tutorial, you created containers and images.</span></span> <span data-ttu-id="207ea-248">Si vous le souhaitez, supprimez ces ressources.</span><span class="sxs-lookup"><span data-stu-id="207ea-248">If you want, delete these resources.</span></span> <span data-ttu-id="207ea-249">Utilisez les commandes suivantes pour</span><span class="sxs-lookup"><span data-stu-id="207ea-249">Use the following commands to</span></span>

01. <span data-ttu-id="207ea-250">Lister tous les conteneurs</span><span class="sxs-lookup"><span data-stu-id="207ea-250">List all containers</span></span>

    ```console
    docker ps -a
    ```

02. <span data-ttu-id="207ea-251">Arrêtez les conteneurs qui s’exécutent par leur nom.</span><span class="sxs-lookup"><span data-stu-id="207ea-251">Stop containers that are running by their name.</span></span>

    ```console
    docker stop counter-image
    ```

03. <span data-ttu-id="207ea-252">Supprimer un conteneur</span><span class="sxs-lookup"><span data-stu-id="207ea-252">Delete the container</span></span>

    ```console
    docker rm counter-image
    ```

<span data-ttu-id="207ea-253">Supprimez ensuite toutes les images que vous ne souhaitez plus conserver sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="207ea-253">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="207ea-254">Supprimez l’image créée par votre *Dockerfile*, puis l’image .NET Core sur laquelle le *Dockerfile* était basé.</span><span class="sxs-lookup"><span data-stu-id="207ea-254">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="207ea-255">Vous pouvez utiliser la valeur **IMAGE ID** ou la chaîne mise en forme **REPOSITORY:TAG**.</span><span class="sxs-lookup"><span data-stu-id="207ea-255">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi counter-image:latest
docker rmi mcr.microsoft.com/dotnet/aspnet:3.1
```

<span data-ttu-id="207ea-256">Utilisez la commande `docker images` pour afficher la liste des images installées.</span><span class="sxs-lookup"><span data-stu-id="207ea-256">Use the `docker images` command to see a list of images installed.</span></span>

> [!TIP]
> <span data-ttu-id="207ea-257">Les fichiers image peuvent être volumineux.</span><span class="sxs-lookup"><span data-stu-id="207ea-257">Image files can be large.</span></span> <span data-ttu-id="207ea-258">En règle générale, vous supprimez les conteneurs temporaires que vous avez créés lors des tests et du développement de votre app.</span><span class="sxs-lookup"><span data-stu-id="207ea-258">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="207ea-259">Vous conservez normalement les images de base avec le runtime installé si vous envisagez de créer d’autres images basées sur ce runtime.</span><span class="sxs-lookup"><span data-stu-id="207ea-259">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="207ea-260">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="207ea-260">Next steps</span></span>

- [<span data-ttu-id="207ea-261">Apprenez à conteneuriser une application ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="207ea-261">Learn how to containerize an ASP.NET Core application.</span></span>](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [<span data-ttu-id="207ea-262">Essayez le tutoriel sur le microservice ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="207ea-262">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [<span data-ttu-id="207ea-263">Passez en revue les services Azure qui prennent en charge des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="207ea-263">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
- [<span data-ttu-id="207ea-264">En savoir plus sur les commandes Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="207ea-264">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
- [<span data-ttu-id="207ea-265">Explorez les outils de conteneur pour Visual Studio</span><span class="sxs-lookup"><span data-stu-id="207ea-265">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
