---
title: Tutoriel Conteneuriser une application avec Docker
description: Dans ce didacticiel, vous allez apprendre à créer un conteneur pour une application .NET Core avec l’arrimeur.
ms.date: 01/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 17d3dfbe58770b19a75be1dad3ae03406584992c
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900111"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="1c8f9-103">Didacticiel : conteneur d’une application .NET Core</span><span class="sxs-lookup"><span data-stu-id="1c8f9-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="1c8f9-104">Ce tutoriel explique comment élaborer une image Docker contenant une application .NET Core existante.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="1c8f9-105">L’image vous permettra de créer des conteneurs pour votre environnement de développement local, votre cloud privé ou votre cloud public.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="1c8f9-106">Vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="1c8f9-106">You'll learn to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="1c8f9-107">Créer et publier une application .NET Core simple</span><span class="sxs-lookup"><span data-stu-id="1c8f9-107">Create and publish a simple .NET Core app</span></span>
> - <span data-ttu-id="1c8f9-108">Créer et configurer un Dockerfile pour .NET Core</span><span class="sxs-lookup"><span data-stu-id="1c8f9-108">Create and configure a Dockerfile for .NET Core</span></span>
> - <span data-ttu-id="1c8f9-109">Créer une image Docker</span><span class="sxs-lookup"><span data-stu-id="1c8f9-109">Build a Docker image</span></span>
> - <span data-ttu-id="1c8f9-110">Créer et exécuter un conteneur Docker</span><span class="sxs-lookup"><span data-stu-id="1c8f9-110">Create and run a Docker container</span></span>

<span data-ttu-id="1c8f9-111">Vous découvrirez la création d’un conteneur Docker et les tâches de déploiement pour une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-111">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="1c8f9-112">La *plateforme Docker* utilise le *moteur Docker* pour générer et empaqueter rapidement des applications comme *images Docker*.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-112">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="1c8f9-113">Ces images sont écrites au format *Dockerfile* pour être déployées et exécutées dans un conteneur en couches.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-113">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

> [!TIP]
> <span data-ttu-id="1c8f9-114">Si vous utilisez une application de ASP.NET Core existante, consultez le didacticiel [apprendre à déconteneurr une application ASP.net Core](/aspnet/core/host-and-deploy/docker/building-net-docker-images) .</span><span class="sxs-lookup"><span data-stu-id="1c8f9-114">If you're working with an existing ASP.NET Core application, see the [Learn how to containerize an ASP.NET Core application](/aspnet/core/host-and-deploy/docker/building-net-docker-images) tutorial.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1c8f9-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1c8f9-115">Prerequisites</span></span>

<span data-ttu-id="1c8f9-116">Installez les éléments requis suivants :</span><span class="sxs-lookup"><span data-stu-id="1c8f9-116">Install the following prerequisites:</span></span>

- <span data-ttu-id="1c8f9-117">\ du [Kit de développement logiciel (SDK) .net Core 3,1](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="1c8f9-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)\</span></span>
<span data-ttu-id="1c8f9-118">Si .NET Core est installé, utilisez la commande `dotnet --info` pour identifier le Kit SDK que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-118">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>

- [<span data-ttu-id="1c8f9-119">Docker Community Edition</span><span class="sxs-lookup"><span data-stu-id="1c8f9-119">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)

- <span data-ttu-id="1c8f9-120">Un dossier de travail temporaire pour le *Dockerfile* et un exemple d’application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-120">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="1c8f9-121">Dans ce didacticiel, le nom *docker-Worker* est utilisé comme dossier de travail.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-121">In this tutorial, the name *docker-working* is used as the working folder.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="1c8f9-122">Créer une application .NET Core</span><span class="sxs-lookup"><span data-stu-id="1c8f9-122">Create .NET Core app</span></span>

<span data-ttu-id="1c8f9-123">Vous avez besoin d’une application .NET Core que le conteneur Docker exécutera.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-123">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="1c8f9-124">Ouvrez votre terminal, créez un dossier de travail si ce n’est déjà fait, et accédez-y.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-124">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="1c8f9-125">Dans le dossier de travail, exécutez la commande suivante pour créer un nouveau projet dans un sous-répertoire nommé *app*:</span><span class="sxs-lookup"><span data-stu-id="1c8f9-125">In the working folder, run the following command to create a new project in a subdirectory named *app*:</span></span>

```dotnetcli
dotnet new console -o app -n myapp
```

<span data-ttu-id="1c8f9-126">Votre arborescence de dossiers doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="1c8f9-126">Your folder tree will look like the following:</span></span>

```
docker-working
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    └───obj
            myapp.csproj.nuget.cache
            myapp.csproj.nuget.dgspec.json
            myapp.csproj.nuget.g.props
            myapp.csproj.nuget.g.targets
            project.assets.json
```

<span data-ttu-id="1c8f9-127">La commande `dotnet new` crée un dossier nommé *app* et génère une application « Hello World ».</span><span class="sxs-lookup"><span data-stu-id="1c8f9-127">The `dotnet new` command creates a new folder named *app* and generates a "Hello World" app.</span></span> <span data-ttu-id="1c8f9-128">Accédez au dossier *app* et exécutez la commande `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-128">Enter the *app* folder and run the command `dotnet run`.</span></span> <span data-ttu-id="1c8f9-129">Le résultat suivant s’affiche :</span><span class="sxs-lookup"><span data-stu-id="1c8f9-129">You'll see the following output:</span></span>

```console
> dotnet run
Hello World!
```

<span data-ttu-id="1c8f9-130">Le modèle par défaut crée une application qui affiche les données dans le terminal, puis se ferme.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-130">The default template creates an app that prints to the terminal and then exits.</span></span> <span data-ttu-id="1c8f9-131">Pour ce tutoriel, vous utiliserez une application qui effectue une boucle indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-131">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="1c8f9-132">Ouvrez le fichier *Program.cs* dans un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-132">Open the *Program.cs* file in a text editor.</span></span> <span data-ttu-id="1c8f9-133">Il devrait ressembler au code suivant :</span><span class="sxs-lookup"><span data-stu-id="1c8f9-133">It should currently look like the following code:</span></span>

```csharp
using System;

namespace myapp
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

<span data-ttu-id="1c8f9-134">Remplacez le fichier par le code suivant qui compte les nombres chaque seconde :</span><span class="sxs-lookup"><span data-stu-id="1c8f9-134">Replace the file with the following code that counts numbers every second:</span></span>

```csharp
using System;

namespace myapp
{
    class Program
    {
        static void Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

<span data-ttu-id="1c8f9-135">Enregistrez le fichier et effectuez un nouveau avec `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-135">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="1c8f9-136">N’oubliez pas que cette application s’exécute indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-136">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="1c8f9-137">Utilisez la commande Annuler <kbd>CTRL</kbd>+<kbd>C</kbd> pour l’arrêter.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-137">Use the cancel command <kbd>CTRL</kbd>+<kbd>C</kbd> to stop it.</span></span> <span data-ttu-id="1c8f9-138">Le résultat suivant s’affiche :</span><span class="sxs-lookup"><span data-stu-id="1c8f9-138">You'll see the following output:</span></span>

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="1c8f9-139">Si vous envoyez un nombre à l’application sur la ligne de commande, l’application comptera uniquement jusqu’à ce montant puis se fermera.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-139">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="1c8f9-140">Effectuez un test avec `dotnet run -- 5` pour compter jusqu’à cinq.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-140">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!NOTE]
> <span data-ttu-id="1c8f9-141">Tous les paramètres après `--` sont transmis à votre application au lieu d’être transmis à la commande `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-141">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="1c8f9-142">Publier une application .NET Core</span><span class="sxs-lookup"><span data-stu-id="1c8f9-142">Publish .NET Core app</span></span>

<span data-ttu-id="1c8f9-143">Avant d’ajouter votre application .NET Core à l’image Docker, publiez-la.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-143">Before you add your .NET Core app to the Docker image, publish it.</span></span> <span data-ttu-id="1c8f9-144">Vous souhaitez vous assurer que le conteneur exécute la version publiée de l’application quand elle est démarrée.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-144">You want to make sure that the container runs the published version of the app when it's started.</span></span>

<span data-ttu-id="1c8f9-145">Dans le dossier de travail, accédez au dossier *app* contenant l’exemple de code source, puis exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="1c8f9-145">From the working folder, enter the *app* folder with the example source code and run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="1c8f9-146">Cette commande compile votre application dans le dossier *publish*.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-146">This command compiles your app to the *publish* folder.</span></span> <span data-ttu-id="1c8f9-147">Le chemin du dossier *publish* à partir du dossier de travail doit être `.\app\bin\Release\netcoreapp3.1\publish\`</span><span class="sxs-lookup"><span data-stu-id="1c8f9-147">The path to the *publish* folder from the working folder should be `.\app\bin\Release\netcoreapp3.1\publish\`</span></span>

<span data-ttu-id="1c8f9-148">Dans le dossier de l' *application* , accédez à la liste des répertoires du dossier de publication pour vérifier que le fichier *MyApp. dll* a été créé.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-148">From the *app* folder, get a directory listing of the publish folder to verify that the *myapp.dll* file was created.</span></span> 

```console
> dir bin\Release\netcoreapp3.1\publish

    Directory:  C:\docker-working\app\bin\Release\netcoreapp3.1\publish

01/09/2020  11:41 AM    <DIR>          .
01/09/2020  11:41 AM    <DIR>          ..
01/09/2020  11:41 AM               407 myapp.deps.json
01/09/2020  12:15 PM             4,608 myapp.dll
01/09/2020  12:15 PM           169,984 myapp.exe
01/09/2020  12:15 PM               736 myapp.pdb
01/09/2020  11:41 AM               154 myapp.runtimeconfig.json
```

<span data-ttu-id="1c8f9-149">Si vous utilisez Linux ou macOS, utilisez la commande `ls` pour obtenir une liste de répertoires et vérifier que le fichier *MyApp. dll* a été créé.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-149">If you're using Linux or macOS, use the `ls` command to get a directory listing and verify that the *myapp.dll* file was created.</span></span>

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a><span data-ttu-id="1c8f9-150">Créer le Dockerfile</span><span class="sxs-lookup"><span data-stu-id="1c8f9-150">Create the Dockerfile</span></span>

<span data-ttu-id="1c8f9-151">Le fichier *Dockerfile* est utilisé par la commande `docker build` pour créer une image de conteneur.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-151">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="1c8f9-152">Ce fichier est un fichier texte nommé *fichier dockerfile* qui n’a pas d’extension.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-152">This file is a text file named *Dockerfile* that doesn't have an extension.</span></span>

<span data-ttu-id="1c8f9-153">Dans votre terminal, accédez au dossier de travail que vous avez créé au début.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-153">In your terminal, navigate up a directory to the working folder you created at the start.</span></span> <span data-ttu-id="1c8f9-154">Créez un fichier nommé *Dockerfile* dans votre dossier de travail et ouvrez-le dans un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-154">Create a file named *Dockerfile* in your working folder and open it in a text editor.</span></span> <span data-ttu-id="1c8f9-155">Selon le type d’application que vous allez déconteneurr, vous devez choisir le runtime ASP.NET Core ou le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-155">Depending on the type of application you're going to containerize, you'll choose either the ASP.NET Core runtime or the .NET Core runtime.</span></span> <span data-ttu-id="1c8f9-156">En cas de doute, choisissez le runtime ASP.NET Core, qui comprend le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-156">When in doubt, choose the ASP.NET Core runtime, which includes the .NET Core runtime.</span></span> <span data-ttu-id="1c8f9-157">Ce didacticiel utilise l’image d’exécution ASP.NET Core, mais l’application créée dans les sections précédentes est une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-157">This tutorial will use the ASP.NET Core runtime image, but the application created in the previous sections is an .NET Core application.</span></span>

- <span data-ttu-id="1c8f9-158">Runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1c8f9-158">ASP.NET Core runtime</span></span>

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
  ```

- <span data-ttu-id="1c8f9-159">Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="1c8f9-159">.NET Core runtime</span></span>

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/runtime:3.1
  ```

<span data-ttu-id="1c8f9-160">La commande `FROM` indique à docker d’extraire l’image marquée **3,1** du dépôt spécifié.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-160">The `FROM` command tells Docker to pull down the image tagged **3.1** from the specified repository.</span></span> <span data-ttu-id="1c8f9-161">Veillez à extraire la version du runtime qui correspond au runtime ciblé par votre kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="1c8f9-161">Make sure that you pull the runtime version that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="1c8f9-162">Par exemple, l’application créée dans la section précédente utilisait le kit de développement logiciel (SDK) .NET Core 3,1 et l’image de base référencée dans le *fichier dockerfile* est marquée avec **3,1**.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-162">For example, the app created in the previous section used the .NET Core 3.1 SDK and the base image referred to in the *Dockerfile* is tagged with **3.1**.</span></span>

<span data-ttu-id="1c8f9-163">Enregistrez le fichier *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-163">Save the *Dockerfile* file.</span></span> <span data-ttu-id="1c8f9-164">La structure de répertoires du dossier de travail doit ressembler à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-164">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="1c8f9-165">Certains des fichiers et dossiers de niveau plus profond ont été supprimés pour économiser de l’espace dans l’article :</span><span class="sxs-lookup"><span data-stu-id="1c8f9-165">Some of the deeper-level files and folders have been cut to save space in the article:</span></span>

```
docker-working
│   Dockerfile
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    ├───bin
    │   └───Release
    │       └───netcoreapp3.1
    │           └───publish
    │                   myapp.deps.json
    │                   myapp.exe
    │                   myapp.dll
    │                   myapp.pdb
    │                   myapp.runtimeconfig.json
    │
    └───obj
```

<span data-ttu-id="1c8f9-166">Dans votre terminal, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="1c8f9-166">From your terminal, run the following command:</span></span>

```console
docker build -t myimage -f Dockerfile .
```

<span data-ttu-id="1c8f9-167">Docker traitera chaque ligne du *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-167">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="1c8f9-168">L’élément `.` de la commande `docker build` indique à Docker d’utiliser le dossier actif pour rechercher un *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-168">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="1c8f9-169">Cette commande génère l’image et crée un référentiel local nommé **myimage** qui pointe vers cette image.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-169">This command builds the image and creates a local repository named **myimage** that points to that image.</span></span> <span data-ttu-id="1c8f9-170">Une fois cette commande terminée, exécutez `docker images` pour afficher une liste des images installées :</span><span class="sxs-lookup"><span data-stu-id="1c8f9-170">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              38db0eb8f648        4 weeks ago         346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

<span data-ttu-id="1c8f9-171">Notez que les deux images partagent la même valeur **IMAGE ID**.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-171">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="1c8f9-172">La valeur est la même dans les deux images, car la seule commande dans le *Dockerfile* basait la nouvelle image sur une image existante.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-172">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="1c8f9-173">Ajoutons deux commandes au *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-173">Let's add two commands to the *Dockerfile*.</span></span> <span data-ttu-id="1c8f9-174">Chaque commande crée une nouvelle couche d’image avec la commande finale représentant l’image vers laquelle l’entrée de référentiel **myImage** pointe.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-174">Each command creates a new image layer with the final command representing the image the **myimage** repository entry points to.</span></span>

```dockerfile
COPY app/bin/Release/netcoreapp3.1/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

<span data-ttu-id="1c8f9-175">La commande `COPY` indique à Docker de copier le dossier spécifié sur votre ordinateur, dans un dossier du conteneur.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-175">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="1c8f9-176">Dans cet exemple, le dossier *publish* est copié vers un dossier nommé *app* dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-176">In this example, the *publish* folder is copied to a folder named *app* in the container.</span></span>

<span data-ttu-id="1c8f9-177">La commande suivante, `ENTRYPOINT`, indique à Docker de configurer le conteneur afin de l’exécuter comme un fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-177">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="1c8f9-178">Au démarrage du conteneur, la commande `ENTRYPOINT` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-178">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="1c8f9-179">Lorsque cette commande se termine, le conteneur s’arrête automatiquement.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-179">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="1c8f9-180">Dans votre terminal, exécutez `docker build -t myimage -f Dockerfile .` puis, une fois la commande terminée, exécutez `docker images`.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-180">From your terminal, run `docker build -t myimage -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  1.624MB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> 38db0eb8f648
Step 2/3 : COPY app/bin/Release/netcoreapp3.1/publish/ app/
 ---> 37873673e468
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in d8deb7b3aa9e
Removing intermediate container d8deb7b3aa9e
 ---> 0d602ca35c1d
Successfully built 0d602ca35c1d
Successfully tagged myimage:latest

> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              0d602ca35c1d        4 seconds ago       346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

<span data-ttu-id="1c8f9-181">Chaque commande dans le *Dockerfile* a généré une couche et créé une valeur **IMAGE ID**.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-181">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="1c8f9-182">La valeur **IMAGE ID** finale (la vôtre sera différente) est **ddcc6646461b**, et vous allez ensuite créer un conteneur basé sur cette image.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-182">The final **IMAGE ID** (yours will be different) is **ddcc6646461b** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="1c8f9-183">Créer un conteneur</span><span class="sxs-lookup"><span data-stu-id="1c8f9-183">Create a container</span></span>

<span data-ttu-id="1c8f9-184">Maintenant que vous disposez d’une image qui contient votre application, vous pouvez créer un conteneur.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-184">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="1c8f9-185">Vous pouvez créer un conteneur de deux manières.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-185">You can create a container in two ways.</span></span> <span data-ttu-id="1c8f9-186">Tout d’abord, créez un conteneur arrêté.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-186">First, create a new container that is stopped.</span></span>

```console
> docker create myimage
ceda87b219a4e55e9ad5d833ee1a7ea4da21b5ea7ce5a7d08f3051152e784944
```

<span data-ttu-id="1c8f9-187">La commande `docker create` ci-dessus crée un conteneur basé sur l’image **myimage**.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-187">The `docker create` command from above will create a container based on the **myimage** image.</span></span> <span data-ttu-id="1c8f9-188">Le résultat de cette commande affiche la valeur **CONTAINER ID** (la vôtre sera différente) du conteneur créé.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-188">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="1c8f9-189">Pour afficher une liste de *tous* les conteneurs, utilisez la commande `docker ps -a` :</span><span class="sxs-lookup"><span data-stu-id="1c8f9-189">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               gallant_lehmann
```

### <a name="manage-the-container"></a><span data-ttu-id="1c8f9-190">Gérer le conteneur</span><span class="sxs-lookup"><span data-stu-id="1c8f9-190">Manage the container</span></span>

<span data-ttu-id="1c8f9-191">Chaque conteneur reçoit un nom aléatoire que vous pouvez utiliser pour faire référence à cette instance de conteneur.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-191">Each container is assigned a random name that you can use to refer to that container instance.</span></span> <span data-ttu-id="1c8f9-192">Par exemple, le conteneur qui a été créé choisit automatiquement le nom **gallant_lehmann** (le vôtre sera différent) et ce nom peut être utilisé pour démarrer le conteneur.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-192">For example, the container that was created automatically chose the name **gallant_lehmann** (yours will be different) and that name can be used to start the container.</span></span> <span data-ttu-id="1c8f9-193">Vous remplacez le nom automatique par une valeur spécifique à l’aide du paramètre `docker create --name`.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-193">You override the automatic name with a specific one by using the `docker create --name` parameter.</span></span>

<span data-ttu-id="1c8f9-194">L’exemple suivant utilise la commande `docker start` pour démarrer le conteneur, puis la commande `docker ps` pour afficher uniquement les conteneurs en cours d’exécution :</span><span class="sxs-lookup"><span data-stu-id="1c8f9-194">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
> docker start gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           gallant_lehmann
```

<span data-ttu-id="1c8f9-195">De même, la commande `docker stop` arrêtera le conteneur.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-195">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="1c8f9-196">L’exemple suivant utilise la commande `docker stop` pour arrêter le conteneur, puis utilise la commande `docker ps` pour indiquer qu’aucun conteneur n’est en cours d’exécution :</span><span class="sxs-lookup"><span data-stu-id="1c8f9-196">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running:</span></span>

```console
> docker stop gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="1c8f9-197">Se connecter à un conteneur</span><span class="sxs-lookup"><span data-stu-id="1c8f9-197">Connect to a container</span></span>

<span data-ttu-id="1c8f9-198">Lorsqu’un conteneur est en cours d’exécution, vous pouvez vous connecter à ce dernier pour afficher le résultat.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-198">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="1c8f9-199">Utilisez les commandes `docker start` et `docker attach` pour démarrer le conteneur et observer le flux de sortie.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-199">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="1c8f9-200">Dans cet exemple, la combinaison de touches <kbd>Ctrl + C</kbd> est utilisée pour se détacher du conteneur en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-200">In this example, the <kbd>CTRL + C</kbd> keystroke is used to detach from the running container.</span></span> <span data-ttu-id="1c8f9-201">Cette séquence de touches peut mettre fin au processus dans le conteneur, ce qui entraîne l’arrêt du conteneur.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-201">This keystroke may actually end the process in the container, which will stop the container.</span></span> <span data-ttu-id="1c8f9-202">Le paramètre `--sig-proxy=false` garantit que la commande <kbd>Ctrl + C</kbd> n’arrêtera pas le processus dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-202">The `--sig-proxy=false` parameter ensures that <kbd>CTRL + C</kbd> won't stop the process in the container.</span></span>

<span data-ttu-id="1c8f9-203">Après vous être déconnecté du conteneur, reconnectez-vous pour vérifier qu’il est toujours en cours d’exécution et de comptage.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-203">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```console
> docker start gallant_lehmann
gallant_lehmann

> docker attach --sig-proxy=false gallant_lehmann
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false gallant_lehmann
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="1c8f9-204">Supprimer un conteneur</span><span class="sxs-lookup"><span data-stu-id="1c8f9-204">Delete a container</span></span>

<span data-ttu-id="1c8f9-205">Dans le cadre de cet article, vous devez éviter de vous retrouver avec des conteneurs inactifs.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-205">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="1c8f9-206">Supprimez le conteneur que vous avez créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-206">Delete the container you previously created.</span></span> <span data-ttu-id="1c8f9-207">Si le conteneur est en cours d’exécution, arrêtez-le.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-207">If the container is running, stop it.</span></span>

```console
> docker stop gallant_lehmann
```

<span data-ttu-id="1c8f9-208">L’exemple suivant répertorie tous les conteneurs.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-208">The following example lists all containers.</span></span> <span data-ttu-id="1c8f9-209">Il utilise ensuite la commande `docker rm` pour supprimer le conteneur, puis recherche une deuxième fois si des conteneurs sont en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-209">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             gallant_lehmann

> docker rm gallant_lehmann
gallant_lehmann

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="1c8f9-210">Exécution unique</span><span class="sxs-lookup"><span data-stu-id="1c8f9-210">Single run</span></span>

<span data-ttu-id="1c8f9-211">Docker fournit la commande `docker run` pour créer et exécuter le conteneur comme une commande unique.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-211">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="1c8f9-212">Cette commande vous évite de devoir exécuter `docker create` , puis `docker start`.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-212">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="1c8f9-213">Vous pouvez également définir cette commande pour supprimer automatiquement le conteneur lorsque le conteneur s’arrête.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-213">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="1c8f9-214">Par exemple, utilisez `docker run -it --rm` pour effectuer deux opérations : utiliser automatiquement le terminal actuel pour se connecter au conteneur, puis supprimer ce conteneur une fois qu’il est terminé :</span><span class="sxs-lookup"><span data-stu-id="1c8f9-214">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="1c8f9-215">Avec `docker run -it`, la commande <kbd>CTRL + C</kbd> interrompt le processus en cours d’exécution dans le conteneur, qui à son tour, arrête le conteneur.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-215">With `docker run -it`, the <kbd>CTRL + C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="1c8f9-216">Comme le paramètre `--rm` a été fourni, le conteneur est automatiquement supprimé lorsque le processus est arrêté.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-216">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="1c8f9-217">Vérifiez qu’il n’existe pas :</span><span class="sxs-lookup"><span data-stu-id="1c8f9-217">Verify that it doesn't exist:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="1c8f9-218">Modifier la commande ENTRYPOINT</span><span class="sxs-lookup"><span data-stu-id="1c8f9-218">Change the ENTRYPOINT</span></span>

<span data-ttu-id="1c8f9-219">La commande `docker run` vous permet également de modifier la commande `ENTRYPOINT` depuis le *Dockerfile* , puis d’exécuter un autre élément, mais uniquement pour ce conteneur.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-219">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="1c8f9-220">Par exemple, utilisez la commande suivante pour exécuter `bash` ou `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-220">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="1c8f9-221">Modifiez la commande selon vos besoins.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-221">Edit the command as necessary.</span></span>

#### <a name="windows"></a><span data-ttu-id="1c8f9-222">Portail</span><span class="sxs-lookup"><span data-stu-id="1c8f9-222">Windows</span></span>

<span data-ttu-id="1c8f9-223">Dans cet exemple, `ENTRYPOINT` est remplacé par `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-223">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="1c8f9-224">Appuyez sur <kbd>CTRL</kbd>+<kbd>C</kbd> pour terminer le processus et arrêter le conteneur.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-224"><kbd>CTRL</kbd>+<kbd>C</kbd> is pressed to end the process and stop the container.</span></span>

```console
> docker run -it --rm --entrypoint "cmd.exe" myimage

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

#### <a name="linux"></a><span data-ttu-id="1c8f9-225">Linux</span><span class="sxs-lookup"><span data-stu-id="1c8f9-225">Linux</span></span>

<span data-ttu-id="1c8f9-226">Dans cet exemple, `ENTRYPOINT` est remplacé par `bash`.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-226">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="1c8f9-227">La commande `quit` est exécutée, ce qui interrompt le processus et arrête le conteneur.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-227">The `quit` command is run which ends the process and stop the container.</span></span>

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a><span data-ttu-id="1c8f9-228">Commandes essentielles</span><span class="sxs-lookup"><span data-stu-id="1c8f9-228">Essential commands</span></span>

<span data-ttu-id="1c8f9-229">Docker propose différentes commandes qui couvrent vos besoins en matière de conteneurs et d’images.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-229">Docker has many different commands that cover what you want to do with your container and images.</span></span> <span data-ttu-id="1c8f9-230">Ces commandes Docker sont essentielles à la gestion de vos conteneurs :</span><span class="sxs-lookup"><span data-stu-id="1c8f9-230">These Docker commands are essential to managing your containers:</span></span>

- [<span data-ttu-id="1c8f9-231">docker build</span><span class="sxs-lookup"><span data-stu-id="1c8f9-231">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
- [<span data-ttu-id="1c8f9-232">docker run</span><span class="sxs-lookup"><span data-stu-id="1c8f9-232">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
- [<span data-ttu-id="1c8f9-233">docker ps</span><span class="sxs-lookup"><span data-stu-id="1c8f9-233">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
- [<span data-ttu-id="1c8f9-234">docker stop</span><span class="sxs-lookup"><span data-stu-id="1c8f9-234">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
- [<span data-ttu-id="1c8f9-235">docker rm</span><span class="sxs-lookup"><span data-stu-id="1c8f9-235">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
- [<span data-ttu-id="1c8f9-236">docker rmi</span><span class="sxs-lookup"><span data-stu-id="1c8f9-236">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
- [<span data-ttu-id="1c8f9-237">docker image</span><span class="sxs-lookup"><span data-stu-id="1c8f9-237">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="1c8f9-238">Nettoyer les ressources</span><span class="sxs-lookup"><span data-stu-id="1c8f9-238">Clean up resources</span></span>

<span data-ttu-id="1c8f9-239">Au cours de ce didacticiel, vous avez créé des conteneurs et des images.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-239">During this tutorial, you created containers and images.</span></span> <span data-ttu-id="1c8f9-240">Si vous le souhaitez, supprimez ces ressources.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-240">If you want, delete these resources.</span></span> <span data-ttu-id="1c8f9-241">Utilisez les commandes suivantes pour</span><span class="sxs-lookup"><span data-stu-id="1c8f9-241">Use the following commands to</span></span>

01. <span data-ttu-id="1c8f9-242">Lister tous les conteneurs</span><span class="sxs-lookup"><span data-stu-id="1c8f9-242">List all containers</span></span>

    ```console
    > docker ps -a
    ```

02. <span data-ttu-id="1c8f9-243">Arrêtez les conteneurs en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-243">Stop containers that are running.</span></span> <span data-ttu-id="1c8f9-244">`CONTAINER_NAME` représente le nom automatiquement attribué au conteneur.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-244">The `CONTAINER_NAME` represents the name automatically assigned to the container.</span></span>

    ```console
    > docker stop CONTAINER_NAME
    ```

03. <span data-ttu-id="1c8f9-245">Supprimer le conteneur</span><span class="sxs-lookup"><span data-stu-id="1c8f9-245">Delete the container</span></span>

    ```console
    > docker rm CONTAINER_NAME
    ```

<span data-ttu-id="1c8f9-246">Supprimez ensuite toutes les images que vous ne souhaitez plus conserver sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-246">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="1c8f9-247">Supprimez l’image créée par votre *Dockerfile*, puis l’image .NET Core sur laquelle le *Dockerfile* était basé.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-247">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="1c8f9-248">Vous pouvez utiliser la valeur **IMAGE ID** ou la chaîne mise en forme **REPOSITORY:TAG**.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-248">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

<span data-ttu-id="1c8f9-249">Utilisez la commande `docker images` pour afficher la liste des images installées.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-249">Use the `docker images` command to see a list of images installed.</span></span>

> [!NOTE]
> <span data-ttu-id="1c8f9-250">Les fichiers image peuvent être volumineux.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-250">Image files can be large.</span></span> <span data-ttu-id="1c8f9-251">En règle générale, vous supprimez les conteneurs temporaires que vous avez créés lors des tests et du développement de votre app.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-251">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="1c8f9-252">Vous conservez normalement les images de base avec le runtime installé si vous envisagez de créer d’autres images basées sur ce runtime.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-252">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1c8f9-253">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="1c8f9-253">Next steps</span></span>

- [<span data-ttu-id="1c8f9-254">Apprenez à conteneuriser une application ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-254">Learn how to containerize an ASP.NET Core application.</span></span>](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [<span data-ttu-id="1c8f9-255">Essayez le tutoriel sur le microservice ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-255">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [<span data-ttu-id="1c8f9-256">Passez en revue les services Azure qui prennent en charge des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-256">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
- [<span data-ttu-id="1c8f9-257">En savoir plus sur les commandes Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="1c8f9-257">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
- [<span data-ttu-id="1c8f9-258">Explorez les outils de conteneur pour Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1c8f9-258">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
