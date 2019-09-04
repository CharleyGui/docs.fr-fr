---
title: Tutoriel Conteneuriser une application avec Docker
description: Ce tutoriel explique comment conteneuriser une application .NET Core avec Docker.
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: ec1c6eb5c1a78a631b8205da5d082e44884cde7a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253948"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="3f450-103">Tutoriel : Conteneuriser une application .NET Core</span><span class="sxs-lookup"><span data-stu-id="3f450-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="3f450-104">Ce tutoriel explique comment élaborer une image Docker contenant une application .NET Core existante.</span><span class="sxs-lookup"><span data-stu-id="3f450-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="3f450-105">L’image vous permettra de créer des conteneurs pour votre environnement de développement local, votre cloud privé ou votre cloud public.</span><span class="sxs-lookup"><span data-stu-id="3f450-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="3f450-106">Vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="3f450-106">You'll learn to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="3f450-107">Créer et publier une application .NET Core simple</span><span class="sxs-lookup"><span data-stu-id="3f450-107">Create and publish a simple .NET Core app</span></span>
> * <span data-ttu-id="3f450-108">Créer et configurer un Dockerfile pour .NET Core</span><span class="sxs-lookup"><span data-stu-id="3f450-108">Create and configure a Dockerfile for .NET Core</span></span>
> * <span data-ttu-id="3f450-109">Créer une image Docker</span><span class="sxs-lookup"><span data-stu-id="3f450-109">Build a Docker image</span></span>
> * <span data-ttu-id="3f450-110">Créer et exécuter un conteneur Docker</span><span class="sxs-lookup"><span data-stu-id="3f450-110">Create and run a Docker container</span></span>

<span data-ttu-id="3f450-111">Vous découvrirez la création d’un conteneur Docker et les tâches de déploiement pour une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3f450-111">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="3f450-112">La *plateforme Docker* utilise le *moteur Docker* pour générer et empaqueter rapidement des applications comme *images Docker*.</span><span class="sxs-lookup"><span data-stu-id="3f450-112">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="3f450-113">Ces images sont écrites au format *Dockerfile* pour être déployées et exécutées dans un conteneur en couches.</span><span class="sxs-lookup"><span data-stu-id="3f450-113">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3f450-114">Prérequis</span><span class="sxs-lookup"><span data-stu-id="3f450-114">Prerequisites</span></span>

<span data-ttu-id="3f450-115">Installez les éléments requis suivants :</span><span class="sxs-lookup"><span data-stu-id="3f450-115">Install the following prerequisites:</span></span>

* <span data-ttu-id="3f450-116">[Kit SDK .NET Core 2.2](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="3f450-116">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="3f450-117">Si .NET Core est installé, utilisez la commande `dotnet --info` pour identifier le Kit SDK que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="3f450-117">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>

* [<span data-ttu-id="3f450-118">Docker Community Edition</span><span class="sxs-lookup"><span data-stu-id="3f450-118">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)

* <span data-ttu-id="3f450-119">Un dossier de travail temporaire pour le *Dockerfile* et un exemple d’application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3f450-119">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="3f450-120">Dans ce tutoriel, le nom `docker-working` est utilisé comme dossier de travail</span><span class="sxs-lookup"><span data-stu-id="3f450-120">In this tutorial, the name `docker-working` is used as the working folder.</span></span>

### <a name="use-sdk-version-22"></a><span data-ttu-id="3f450-121">Utiliser le Kit SDK version 2.2</span><span class="sxs-lookup"><span data-stu-id="3f450-121">Use SDK version 2.2</span></span>

<span data-ttu-id="3f450-122">Si vous utilisez un kit SDK plus récent, par exemple 3.0, assurez-vous que votre application est forcée d’utiliser le Kit SDK 2.2.</span><span class="sxs-lookup"><span data-stu-id="3f450-122">If you're using an SDK that is newer, like 3.0, make sure that your app is forced to use the 2.2 SDK.</span></span> <span data-ttu-id="3f450-123">Créez un fichier nommé `global.json` dans votre dossier de travail et collez-y le code json suivant :</span><span class="sxs-lookup"><span data-stu-id="3f450-123">Create a file named `global.json` in your working folder and paste in the following json code:</span></span>

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

<span data-ttu-id="3f450-124">Enregistrez ce fichier.</span><span class="sxs-lookup"><span data-stu-id="3f450-124">Save this file.</span></span> <span data-ttu-id="3f450-125">La présence du fichier forcera .NET Core à utiliser la version 2.2 pour toute commande `dotnet` appelée à partir de ce dossier et de ses sous-dossiers.</span><span class="sxs-lookup"><span data-stu-id="3f450-125">The presence of file will force .NET Core to use version 2.2 for any `dotnet` command called from this folder and below.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="3f450-126">Créer une application .NET Core</span><span class="sxs-lookup"><span data-stu-id="3f450-126">Create .NET Core app</span></span>

<span data-ttu-id="3f450-127">Vous avez besoin d’une application .NET Core que le conteneur Docker exécutera.</span><span class="sxs-lookup"><span data-stu-id="3f450-127">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="3f450-128">Ouvrez votre terminal, créez un dossier de travail si ce n’est déjà fait, et accédez-y.</span><span class="sxs-lookup"><span data-stu-id="3f450-128">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="3f450-129">Dans le dossier de travail, exécutez la commande suivante pour créer un projet dans un sous-répertoire nommé app :</span><span class="sxs-lookup"><span data-stu-id="3f450-129">In the working folder, run the following command to create a new project in a subdirectory named app:</span></span>

```console
dotnet new console -o app -n myapp
```

<span data-ttu-id="3f450-130">Votre arborescence de dossiers doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="3f450-130">Your folder tree will look like the following:</span></span>

```
docker-working
│   global.json
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    └───obj
            myapp.csproj.nuget.cache
            myapp.csproj.nuget.g.props
            myapp.csproj.nuget.g.targets
            project.assets.json
```

<span data-ttu-id="3f450-131">La commande `dotnet new` crée un dossier nommé *app* et génère une application « Hello World ».</span><span class="sxs-lookup"><span data-stu-id="3f450-131">The `dotnet new` command creates a new folder named *app* and generates a "Hello World" app.</span></span> <span data-ttu-id="3f450-132">Accédez au dossier *app* et exécutez la commande `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="3f450-132">Enter the *app* folder and run the command `dotnet run`.</span></span> <span data-ttu-id="3f450-133">Le résultat suivant s’affiche :</span><span class="sxs-lookup"><span data-stu-id="3f450-133">You'll see the following output:</span></span>

```console
> dotnet run
Hello World!
```

<span data-ttu-id="3f450-134">Le modèle par défaut crée une application qui affiche les données dans le terminal, puis se ferme.</span><span class="sxs-lookup"><span data-stu-id="3f450-134">The default template creates an app that prints to the terminal and then exits.</span></span> <span data-ttu-id="3f450-135">Pour ce tutoriel, vous utiliserez une application qui effectue une boucle indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="3f450-135">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="3f450-136">Ouvrez le fichier **Program.cs** dans un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="3f450-136">Open the **Program.cs** file in a text editor.</span></span> <span data-ttu-id="3f450-137">Il devrait ressembler au code suivant :</span><span class="sxs-lookup"><span data-stu-id="3f450-137">It should currently look like the following code:</span></span>

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

<span data-ttu-id="3f450-138">Remplacez le fichier par le code suivant qui compte les nombres chaque seconde :</span><span class="sxs-lookup"><span data-stu-id="3f450-138">Replace the file with the following code that counts numbers every second:</span></span>

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
            while(max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

<span data-ttu-id="3f450-139">Enregistrez le fichier et effectuez un nouveau avec `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="3f450-139">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="3f450-140">N’oubliez pas que cette application s’exécute indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="3f450-140">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="3f450-141">Utilisez la commande Annuler <kbd>CTRL + C</kbd> pour l’arrêter.</span><span class="sxs-lookup"><span data-stu-id="3f450-141">Use the cancel command <kbd>CTRL + C</kbd> to stop it.</span></span> <span data-ttu-id="3f450-142">Le résultat suivant s’affiche :</span><span class="sxs-lookup"><span data-stu-id="3f450-142">You'll see the following output:</span></span>

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="3f450-143">Si vous envoyez un nombre à l’application sur la ligne de commande, l’application comptera uniquement jusqu’à ce montant puis se fermera.</span><span class="sxs-lookup"><span data-stu-id="3f450-143">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="3f450-144">Effectuez un test avec `dotnet run -- 5` pour compter jusqu’à cinq.</span><span class="sxs-lookup"><span data-stu-id="3f450-144">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!NOTE]
> <span data-ttu-id="3f450-145">Tous les paramètres après `--` sont transmis à votre application au lieu d’être transmis à la commande `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="3f450-145">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="3f450-146">Publier une application .NET Core</span><span class="sxs-lookup"><span data-stu-id="3f450-146">Publish .NET Core app</span></span>

<span data-ttu-id="3f450-147">Avant d’ajouter votre application .NET Core à l’image Docker, publiez-la.</span><span class="sxs-lookup"><span data-stu-id="3f450-147">Before you add your .NET Core app to the Docker image, publish it.</span></span> <span data-ttu-id="3f450-148">Vous souhaitez vous assurer que le conteneur exécute la version publiée de l’application quand elle est démarrée.</span><span class="sxs-lookup"><span data-stu-id="3f450-148">You want to make sure that the container runs the published version of the app when it's started.</span></span>

<span data-ttu-id="3f450-149">Dans le dossier de travail, accédez au dossier **app** contenant l’exemple de code source, puis exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="3f450-149">From the working folder, enter the **app** folder with the example source code and run the following command:</span></span>

```console
dotnet publish -c Release
```

<span data-ttu-id="3f450-150">Cette commande compile votre application dans le dossier **publish**.</span><span class="sxs-lookup"><span data-stu-id="3f450-150">This command compiles your app to the **publish** folder.</span></span> <span data-ttu-id="3f450-151">Le chemin du dossier **publish** à partir du dossier de travail doit être `.\app\bin\Release\netcoreapp2.2\publish\`</span><span class="sxs-lookup"><span data-stu-id="3f450-151">The path to the **publish** folder from the working folder should be `.\app\bin\Release\netcoreapp2.2\publish\`</span></span>

<span data-ttu-id="3f450-152">Obtenez une liste des répertoires du dossier de publication pour vérifier que le fichier **myapp.dll** a été créé.</span><span class="sxs-lookup"><span data-stu-id="3f450-152">Get a directory listing of the publish folder to verify that the **myapp.dll** was created.</span></span> <span data-ttu-id="3f450-153">Dans le dossier **app**, exécutez l’une des commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="3f450-153">From the **app** folder, run one of the following commands:</span></span>

```console
> dir bin\Release\netcoreapp2.2\publish
 Directory of C:\docker-working\app\bin\Release\netcoreapp2.2\publish

04/05/2019  11:00 AM    <DIR>          .
04/05/2019  11:00 AM    <DIR>          ..
04/05/2019  11:00 AM               447 myapp.deps.json
04/05/2019  11:00 AM             4,608 myapp.dll
04/05/2019  11:00 AM               448 myapp.pdb
04/05/2019  11:00 AM               154 myapp.runtimeconfig.json
```

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp2.2/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a><span data-ttu-id="3f450-154">Créer le Dockerfile</span><span class="sxs-lookup"><span data-stu-id="3f450-154">Create the Dockerfile</span></span>

<span data-ttu-id="3f450-155">Le fichier *Dockerfile* est utilisé par la commande `docker build` pour créer une image de conteneur.</span><span class="sxs-lookup"><span data-stu-id="3f450-155">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="3f450-156">Ce fichier est un fichier texte brut nommé *Dockerfile*, sans extension.</span><span class="sxs-lookup"><span data-stu-id="3f450-156">This file is a plaintext file named *Dockerfile* that does not have an extension.</span></span>

<span data-ttu-id="3f450-157">Dans votre terminal, accédez au dossier de travail que vous avez créé au début.</span><span class="sxs-lookup"><span data-stu-id="3f450-157">In your terminal, navigate up a directory to the working folder you created at the start.</span></span> <span data-ttu-id="3f450-158">Créez un fichier nommé *Dockerfile* dans votre dossier de travail et ouvrez-le dans un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="3f450-158">Create a file named *Dockerfile* in your working folder and open it in a text editor.</span></span> <span data-ttu-id="3f450-159">Ajoutez la commande suivante comme première ligne du fichier :</span><span class="sxs-lookup"><span data-stu-id="3f450-159">Add the following command as the first line of the file:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/core/runtime:2.2
```

<span data-ttu-id="3f450-160">La commande `FROM` indique à Docker d’extraire l’image marquée **2.2** du référentiel **mcr.microsoft.com/dotnet/core/runtime**.</span><span class="sxs-lookup"><span data-stu-id="3f450-160">The `FROM` command tells Docker to pull down the image tagged **2.2** from the **mcr.microsoft.com/dotnet/core/runtime** repository.</span></span> <span data-ttu-id="3f450-161">Veillez à extraire le runtime .NET Core correspondant au runtime ciblé par votre Kit SDK.</span><span class="sxs-lookup"><span data-stu-id="3f450-161">Make sure that you pull the .NET Core runtime that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="3f450-162">Par exemple, l’application créée dans la précédente section utilisait le Kit SDK .NET Core 2.2 et créait une application qui ciblait .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="3f450-162">For example, the app created in the previous section used the .NET Core 2.2 SDK and created an app that targeted .NET Core 2.2.</span></span> <span data-ttu-id="3f450-163">Ainsi, l’image de base mentionnée dans le *Dockerfile* est marquée **2.2**.</span><span class="sxs-lookup"><span data-stu-id="3f450-163">So the base image referred to in the *Dockerfile* is tagged with **2.2**.</span></span>

<span data-ttu-id="3f450-164">Enregistrez le fichier *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="3f450-164">Save the *Dockerfile* file.</span></span> <span data-ttu-id="3f450-165">La structure de répertoires du dossier de travail doit ressembler à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="3f450-165">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="3f450-166">Certains des fichiers et dossiers de niveau plus profond ont été supprimés pour économiser de l’espace dans l’article :</span><span class="sxs-lookup"><span data-stu-id="3f450-166">Some of the deeper-level files and folders have been cut to save space in the article:</span></span>

```
docker-working
│   Dockerfile
│   global.json
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    ├───bin
    │   └───Release
    │       └───netcoreapp2.2
    │           └───publish
    │                   myapp.deps.json
    │                   myapp.dll
    │                   myapp.pdb
    │                   myapp.runtimeconfig.json
    │
    └───obj
```

<span data-ttu-id="3f450-167">Dans votre terminal, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="3f450-167">From your terminal, run the following command:</span></span>

```console
docker build -t myimage -f Dockerfile .
```

<span data-ttu-id="3f450-168">Docker traitera chaque ligne du *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="3f450-168">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="3f450-169">L’élément `.` de la commande `docker build` indique à Docker d’utiliser le dossier actif pour rechercher un *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="3f450-169">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="3f450-170">Cette commande génère l’image et crée un référentiel local nommé **myimage** qui pointe vers cette image.</span><span class="sxs-lookup"><span data-stu-id="3f450-170">This command builds the image and creates a local repository named **myimage** that points to that image.</span></span> <span data-ttu-id="3f450-171">Une fois cette commande terminée, exécutez `docker images` pour afficher une liste des images installées :</span><span class="sxs-lookup"><span data-stu-id="3f450-171">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
myimage                                 latest              d51bb4452469        2 days ago          314MB
```

<span data-ttu-id="3f450-172">Notez que les deux images partagent la même valeur **IMAGE ID**.</span><span class="sxs-lookup"><span data-stu-id="3f450-172">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="3f450-173">La valeur est la même dans les deux images, car la seule commande dans le *Dockerfile* basait la nouvelle image sur une image existante.</span><span class="sxs-lookup"><span data-stu-id="3f450-173">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="3f450-174">Ajoutons deux commandes au *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="3f450-174">Let's add two commands to the *Dockerfile*.</span></span> <span data-ttu-id="3f450-175">Chaque commande crée une couche d’image avec la commande finale qui représente l’image vers laquelle pointera le référentiel **myimage**.</span><span class="sxs-lookup"><span data-stu-id="3f450-175">Each command creates a new image layer with the final command representing the image the **myimage** repository will point to.</span></span>

```dockerfile
COPY app/bin/Release/netcoreapp2.2/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

<span data-ttu-id="3f450-176">La commande `COPY` indique à Docker de copier le dossier spécifié sur votre ordinateur, dans un dossier du conteneur.</span><span class="sxs-lookup"><span data-stu-id="3f450-176">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="3f450-177">Dans cet exemple, le dossier **publish** est copié vers un dossier nommé **app** dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="3f450-177">In this example, the **publish** folder is copied to a folder named **app** in the container.</span></span>

<span data-ttu-id="3f450-178">La commande suivante, `ENTRYPOINT`, indique à Docker de configurer le conteneur afin de l’exécuter comme un fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="3f450-178">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="3f450-179">Au démarrage du conteneur, la commande `ENTRYPOINT` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="3f450-179">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="3f450-180">Lorsque cette commande se termine, le conteneur s’arrête automatiquement.</span><span class="sxs-lookup"><span data-stu-id="3f450-180">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="3f450-181">Dans votre terminal, exécutez `docker build -t myimage -f Dockerfile .` puis, une fois la commande terminée, exécutez `docker images`.</span><span class="sxs-lookup"><span data-stu-id="3f450-181">From your terminal, run `docker build -t myimage -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  819.7kB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/runtime:2.2
 ---> d51bb4452469
Step 2/3 : COPY app/bin/Release/netcoreapp2.2/publish/ app/
 ---> a1e98ac62017
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in f34da5c18e7c
Removing intermediate container f34da5c18e7c
 ---> ddcc6646461b
Successfully built ddcc6646461b
Successfully tagged myimage:latest

> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              ddcc6646461b        10 seconds ago      314MB
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
```

<span data-ttu-id="3f450-182">Chaque commande dans le *Dockerfile* a généré une couche et créé une valeur **IMAGE ID**.</span><span class="sxs-lookup"><span data-stu-id="3f450-182">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="3f450-183">La valeur **IMAGE ID** finale (la vôtre sera différente) est **ddcc6646461b**, et vous allez ensuite créer un conteneur basé sur cette image.</span><span class="sxs-lookup"><span data-stu-id="3f450-183">The final **IMAGE ID** (yours will be different) is **ddcc6646461b** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="3f450-184">Créer un conteneur</span><span class="sxs-lookup"><span data-stu-id="3f450-184">Create a container</span></span>

<span data-ttu-id="3f450-185">Maintenant que vous disposez d’une image qui contient votre application, vous pouvez créer un conteneur.</span><span class="sxs-lookup"><span data-stu-id="3f450-185">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="3f450-186">Vous pouvez créer un conteneur de deux manières.</span><span class="sxs-lookup"><span data-stu-id="3f450-186">You can create a container in two ways.</span></span> <span data-ttu-id="3f450-187">Tout d’abord, créez un conteneur arrêté.</span><span class="sxs-lookup"><span data-stu-id="3f450-187">First, create a new container that is stopped.</span></span>

```console
> docker create myimage
0e8f3c2ca32ce773712a5cca38750f41259a4e54e04bdf0946087e230ad7066c
```

<span data-ttu-id="3f450-188">La commande `docker create` ci-dessus crée un conteneur basé sur l’image **myimage**.</span><span class="sxs-lookup"><span data-stu-id="3f450-188">The `docker create` command from above will create a container based on the **myimage** image.</span></span> <span data-ttu-id="3f450-189">Le résultat de cette commande affiche la valeur **CONTAINER ID** (la vôtre sera différente) du conteneur créé.</span><span class="sxs-lookup"><span data-stu-id="3f450-189">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="3f450-190">Pour afficher une liste de *tous* les conteneurs, utilisez la commande `docker ps -a` :</span><span class="sxs-lookup"><span data-stu-id="3f450-190">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               boring_matsumoto
```

### <a name="manage-the-container"></a><span data-ttu-id="3f450-191">Gérer le conteneur</span><span class="sxs-lookup"><span data-stu-id="3f450-191">Manage the container</span></span>

<span data-ttu-id="3f450-192">Chaque conteneur reçoit un nom aléatoire que vous pouvez utiliser pour faire référence à cette instance de conteneur.</span><span class="sxs-lookup"><span data-stu-id="3f450-192">Each container is assigned a random name that you can use to refer to that container instance.</span></span> <span data-ttu-id="3f450-193">Par exemple, le conteneur créé automatiquement a choisi le nom **boring_matsumoto** (le vôtre sera différent), et ce nom peut être utilisé pour démarrer le conteneur.</span><span class="sxs-lookup"><span data-stu-id="3f450-193">For example, the container that was created automatically chose the name **boring_matsumoto** (yours will be different) and that name can be used to start the container.</span></span> <span data-ttu-id="3f450-194">Vous remplacez le nom automatique par une valeur spécifique à l’aide du paramètre `docker create --name`.</span><span class="sxs-lookup"><span data-stu-id="3f450-194">You override the automatic name with a specific one by using the `docker create --name` parameter.</span></span>

<span data-ttu-id="3f450-195">L’exemple suivant utilise la commande `docker start` pour démarrer le conteneur, puis la commande `docker ps` pour afficher uniquement les conteneurs en cours d’exécution :</span><span class="sxs-lookup"><span data-stu-id="3f450-195">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
> docker start boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           boring_matsumoto
```

<span data-ttu-id="3f450-196">De même, la commande `docker stop` arrêtera le conteneur.</span><span class="sxs-lookup"><span data-stu-id="3f450-196">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="3f450-197">L’exemple suivant utilise la commande `docker stop` pour arrêter le conteneur, puis la commande `docker ps` pour indiquer qu’aucun conteneur n’est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3f450-197">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running.</span></span>

```console
> docker stop boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="3f450-198">Se connecter à un conteneur</span><span class="sxs-lookup"><span data-stu-id="3f450-198">Connect to a container</span></span>

<span data-ttu-id="3f450-199">Lorsqu’un conteneur est en cours d’exécution, vous pouvez vous connecter à ce dernier pour afficher le résultat.</span><span class="sxs-lookup"><span data-stu-id="3f450-199">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="3f450-200">Utilisez les commandes `docker start` et `docker attach` pour démarrer le conteneur et observer le flux de sortie.</span><span class="sxs-lookup"><span data-stu-id="3f450-200">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="3f450-201">Dans cet exemple, la commande <kbd>CTRL + C</kbd> permet de se déconnecter du conteneur en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3f450-201">In this example, the <kbd>CTRL + C</kbd> command is used to detach from the running container.</span></span> <span data-ttu-id="3f450-202">Cela risque d’interrompre le processus dans le conteneur, ce qui arrêtera le conteneur.</span><span class="sxs-lookup"><span data-stu-id="3f450-202">This may actually end the process in the container, which will stop the container.</span></span> <span data-ttu-id="3f450-203">Le paramètre `--sig-proxy=false` garantit que la commande <kbd>Ctrl + C</kbd> n’arrêtera pas le processus dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="3f450-203">The `--sig-proxy=false` parameter ensures that <kbd>CTRL + C</kbd> won't stop the process in the container.</span></span>

<span data-ttu-id="3f450-204">Après vous être déconnecté du conteneur, reconnectez-vous pour vérifier qu’il est toujours en cours d’exécution et de comptage.</span><span class="sxs-lookup"><span data-stu-id="3f450-204">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```console
> docker start boring_matsumoto
boring_matsumoto

> docker attach --sig-proxy=false boring_matsumoto
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false boring_matsumoto
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="3f450-205">Supprimer un conteneur</span><span class="sxs-lookup"><span data-stu-id="3f450-205">Delete a container</span></span>

<span data-ttu-id="3f450-206">Dans le cadre de cet article, vous devez éviter de vous retrouver avec des conteneurs inactifs.</span><span class="sxs-lookup"><span data-stu-id="3f450-206">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="3f450-207">Supprimez le conteneur que vous avez créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="3f450-207">Delete the container you previously created.</span></span> <span data-ttu-id="3f450-208">Si le conteneur est en cours d’exécution, arrêtez-le.</span><span class="sxs-lookup"><span data-stu-id="3f450-208">If the container is running, stop it.</span></span>

```console
> docker stop boring_matsumoto
```

<span data-ttu-id="3f450-209">L’exemple suivant répertorie tous les conteneurs.</span><span class="sxs-lookup"><span data-stu-id="3f450-209">The following example lists all containers.</span></span> <span data-ttu-id="3f450-210">Il utilise ensuite la commande `docker rm` pour supprimer le conteneur, puis recherche une deuxième fois si des conteneurs sont en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3f450-210">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             boring_matsumoto

> docker rm boring_matsumoto
boring_matsumoto

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="3f450-211">Exécution unique</span><span class="sxs-lookup"><span data-stu-id="3f450-211">Single run</span></span>

<span data-ttu-id="3f450-212">Docker fournit la commande `docker run` pour créer et exécuter le conteneur comme une commande unique.</span><span class="sxs-lookup"><span data-stu-id="3f450-212">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="3f450-213">Cette commande vous évite de devoir exécuter `docker create` , puis `docker start`.</span><span class="sxs-lookup"><span data-stu-id="3f450-213">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="3f450-214">Vous pouvez également définir cette commande pour supprimer automatiquement le conteneur lorsque le conteneur s’arrête.</span><span class="sxs-lookup"><span data-stu-id="3f450-214">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="3f450-215">Par exemple, utilisez `docker run -it --rm` pour effectuer deux opérations : utiliser automatiquement le terminal actuel pour se connecter au conteneur, puis supprimer ce conteneur une fois qu’il est terminé :</span><span class="sxs-lookup"><span data-stu-id="3f450-215">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="3f450-216">Avec `docker run -it`, la commande <kbd>CTRL + C</kbd> interrompt le processus en cours d’exécution dans le conteneur, qui à son tour, arrête le conteneur.</span><span class="sxs-lookup"><span data-stu-id="3f450-216">With `docker run -it`, the <kbd>CTRL + C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="3f450-217">Comme le paramètre `--rm` a été fourni, le conteneur est automatiquement supprimé lorsque le processus est arrêté.</span><span class="sxs-lookup"><span data-stu-id="3f450-217">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="3f450-218">Vérifiez que l’élément suivant n’existe pas :</span><span class="sxs-lookup"><span data-stu-id="3f450-218">Verify that it does not exist:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="3f450-219">Modifier la commande ENTRYPOINT</span><span class="sxs-lookup"><span data-stu-id="3f450-219">Change the ENTRYPOINT</span></span>

<span data-ttu-id="3f450-220">La commande `docker run` vous permet également de modifier la commande `ENTRYPOINT` depuis le *Dockerfile* , puis d’exécuter un autre élément, mais uniquement pour ce conteneur.</span><span class="sxs-lookup"><span data-stu-id="3f450-220">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="3f450-221">Par exemple, utilisez la commande suivante pour exécuter `bash` ou `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="3f450-221">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="3f450-222">Modifiez la commande selon vos besoins.</span><span class="sxs-lookup"><span data-stu-id="3f450-222">Edit the command as necessary.</span></span>

#### <a name="windows"></a><span data-ttu-id="3f450-223">Windows</span><span class="sxs-lookup"><span data-stu-id="3f450-223">Windows</span></span>
<span data-ttu-id="3f450-224">Dans cet exemple, `ENTRYPOINT` est remplacé par `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="3f450-224">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="3f450-225">La combinaison de touches <kbd>CTRL + C</kbd> interrompt le processus et arrête le conteneur.</span><span class="sxs-lookup"><span data-stu-id="3f450-225"><kbd>CTRL + C</kbd> is pressed to end the process and stop the container.</span></span>

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

#### <a name="linux"></a><span data-ttu-id="3f450-226">Linux</span><span class="sxs-lookup"><span data-stu-id="3f450-226">Linux</span></span>

<span data-ttu-id="3f450-227">Dans cet exemple, `ENTRYPOINT` est remplacé par `bash`.</span><span class="sxs-lookup"><span data-stu-id="3f450-227">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="3f450-228">La commande `quit` est exécutée, ce qui interrompt le processus et arrête le conteneur.</span><span class="sxs-lookup"><span data-stu-id="3f450-228">The `quit` command is run which ends the process and stop the container.</span></span>

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a><span data-ttu-id="3f450-229">Commandes essentielles</span><span class="sxs-lookup"><span data-stu-id="3f450-229">Essential commands</span></span>

<span data-ttu-id="3f450-230">Docker propose différentes commandes qui couvrent vos besoins en matière de conteneurs et d’images.</span><span class="sxs-lookup"><span data-stu-id="3f450-230">Docker has many different commands that cover what you want to do with your container and images.</span></span> <span data-ttu-id="3f450-231">Ces commandes Docker sont essentielles à la gestion de vos conteneurs :</span><span class="sxs-lookup"><span data-stu-id="3f450-231">These Docker commands are essential to managing your containers:</span></span>

* [<span data-ttu-id="3f450-232">docker build</span><span class="sxs-lookup"><span data-stu-id="3f450-232">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="3f450-233">docker run</span><span class="sxs-lookup"><span data-stu-id="3f450-233">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="3f450-234">docker ps</span><span class="sxs-lookup"><span data-stu-id="3f450-234">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="3f450-235">docker stop</span><span class="sxs-lookup"><span data-stu-id="3f450-235">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="3f450-236">docker rm</span><span class="sxs-lookup"><span data-stu-id="3f450-236">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="3f450-237">docker rmi</span><span class="sxs-lookup"><span data-stu-id="3f450-237">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="3f450-238">docker image</span><span class="sxs-lookup"><span data-stu-id="3f450-238">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="3f450-239">Supprimer des ressources</span><span class="sxs-lookup"><span data-stu-id="3f450-239">Clean up resources</span></span>

<span data-ttu-id="3f450-240">Au cours de ce tutoriel, vous avez créé des conteneurs et des images.</span><span class="sxs-lookup"><span data-stu-id="3f450-240">During this tutorial you created containers and images.</span></span> <span data-ttu-id="3f450-241">Si vous le souhaitez, supprimez ces ressources.</span><span class="sxs-lookup"><span data-stu-id="3f450-241">If you want, delete these resources.</span></span> <span data-ttu-id="3f450-242">Utilisez les commandes suivantes pour</span><span class="sxs-lookup"><span data-stu-id="3f450-242">Use the following commands to</span></span>

01. <span data-ttu-id="3f450-243">Lister tous les conteneurs</span><span class="sxs-lookup"><span data-stu-id="3f450-243">List all containers</span></span>

    ```console
    > docker ps -a
    ```

02. <span data-ttu-id="3f450-244">Arrêtez les conteneurs en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3f450-244">Stop containers that are running.</span></span> <span data-ttu-id="3f450-245">`CONTAINER_NAME` représente le nom automatiquement attribué au conteneur.</span><span class="sxs-lookup"><span data-stu-id="3f450-245">The `CONTAINER_NAME` represents the name automatically assigned to the container.</span></span>

    ```console
    > docker stop CONTAINER_NAME
    ```

03. <span data-ttu-id="3f450-246">Supprimer le conteneur</span><span class="sxs-lookup"><span data-stu-id="3f450-246">Delete the container</span></span>

    ```console
    > docker rm CONTAINER_NAME
    ```

<span data-ttu-id="3f450-247">Supprimez ensuite toutes les images que vous ne souhaitez plus conserver sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3f450-247">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="3f450-248">Supprimez l’image créée par votre *Dockerfile*, puis l’image .NET Core sur laquelle le *Dockerfile* était basé.</span><span class="sxs-lookup"><span data-stu-id="3f450-248">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="3f450-249">Vous pouvez utiliser la valeur **IMAGE ID** ou la chaîne mise en forme **REPOSITORY:TAG**.</span><span class="sxs-lookup"><span data-stu-id="3f450-249">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/runtime:2.2
```

<span data-ttu-id="3f450-250">Utilisez la commande `docker images` pour afficher la liste des images installées.</span><span class="sxs-lookup"><span data-stu-id="3f450-250">Use the `docker images` command to see a list of images installed.</span></span>

> [!NOTE]
> <span data-ttu-id="3f450-251">Les fichiers image peuvent être volumineux.</span><span class="sxs-lookup"><span data-stu-id="3f450-251">Image files can be large.</span></span> <span data-ttu-id="3f450-252">En règle générale, vous supprimez les conteneurs temporaires que vous avez créés lors des tests et du développement de votre app.</span><span class="sxs-lookup"><span data-stu-id="3f450-252">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="3f450-253">Vous conservez normalement les images de base avec le runtime installé si vous envisagez de créer d’autres images basées sur ce runtime.</span><span class="sxs-lookup"><span data-stu-id="3f450-253">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3f450-254">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="3f450-254">Next steps</span></span>

* [<span data-ttu-id="3f450-255">Essayez le tutoriel sur le microservice ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="3f450-255">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
* [<span data-ttu-id="3f450-256">Passez en revue les services Azure qui prennent en charge des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="3f450-256">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
* [<span data-ttu-id="3f450-257">En savoir plus sur les commandes Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="3f450-257">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
* [<span data-ttu-id="3f450-258">Explorez les outils de conteneur pour Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3f450-258">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
