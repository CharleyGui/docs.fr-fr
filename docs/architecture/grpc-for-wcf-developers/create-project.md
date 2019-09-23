---
title: Créer un nouveau ASP.NET Core projet gRPC-gRPC pour les développeurs WCF
description: Découvrez comment créer un projet gRPC à l’aide de Visual Studio ou à partir de la ligne de commande.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: a0fcc3f9c4e32e87260a6bc79205c909ea3800e0
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184567"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a><span data-ttu-id="dc78f-103">Créer un projet de gRPC ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dc78f-103">Create a new ASP.NET Core gRPC project</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="dc78f-104">.Net Core est fourni avec un puissant outil CLI `dotnet`,, qui vous permet de créer et de gérer des projets et des solutions à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="dc78f-104">.NET Core comes with a powerful CLI tool, `dotnet`, which enables you to create and manage projects and solutions from the command line.</span></span> <span data-ttu-id="dc78f-105">L’outil est étroitement intégré à Visual Studio, de sorte que tout est également disponible par le biais de l’interface graphique familière.</span><span class="sxs-lookup"><span data-stu-id="dc78f-105">The tool is closely integrated with Visual Studio, so everything is also available through the familiar GUI interface.</span></span> <span data-ttu-id="dc78f-106">Ce chapitre présente les deux façons de créer un projet de ASP.NET Core gRPC : tout d’abord avec Visual Studio, puis avec le CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc78f-106">This chapter will show both ways to create a new ASP.NET Core gRPC project: first with Visual Studio, then with the .NET Core CLI.</span></span>

## <a name="create-the-project-using-visual-studio"></a><span data-ttu-id="dc78f-107">Créer le projet à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dc78f-107">Create the project using Visual Studio</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dc78f-108">Pour développer une application ASP.NET Core 3,0, vous avez besoin de Visual Studio 2019,3 ou version ultérieure avec la charge de travail **ASP.net et développement Web** installée.</span><span class="sxs-lookup"><span data-stu-id="dc78f-108">To develop any ASP.NET Core 3.0 app, you need Visual Studio 2019.3 or later with the **ASP.NET and web development** workload installed.</span></span>

<span data-ttu-id="dc78f-109">Créez une solution vide appelée **Traders** à partir du modèle de *solution vide* .</span><span class="sxs-lookup"><span data-stu-id="dc78f-109">Create an empty solution called **TraderSys** from the *Blank Solution* template.</span></span> <span data-ttu-id="dc78f-110">Ajoutez un dossier de solution `src`appelé, puis cliquez avec le bouton droit sur le dossier et choisissez **Ajouter** > un**nouveau projet** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="dc78f-110">Add a Solution Folder called `src`, then right-click on the folder and choose **Add** > **New Project** from the context menu.</span></span> <span data-ttu-id="dc78f-111">Entrez `grpc` dans la zone de recherche de modèle et vous devriez voir un modèle `gRPC Service`de projet appelé.</span><span class="sxs-lookup"><span data-stu-id="dc78f-111">Enter `grpc` in the template search box and you should see a project template called `gRPC Service`.</span></span>

![Boîte de dialogue Ajouter un nouveau projet avec le modèle de projet de service gRPC](media/create-project/new-grpc-project.png)

<span data-ttu-id="dc78f-113">Cliquez **sur suivant** pour passer à la boîte de dialogue **configurer** le projet `TraderSys.Portfolios`et nommez le `src` projet, puis ajoutez un sous-répertoire à l' **emplacement**.</span><span class="sxs-lookup"><span data-stu-id="dc78f-113">Click **Next** to continue to the **Configure project** dialog and name the project `TraderSys.Portfolios`, and add an `src` subdirectory to the **Location**.</span></span>

![Boîte de dialogue Configurer le projet](media/create-project/configure-project.png)

<span data-ttu-id="dc78f-115">Cliquez sur **suivant** pour accéder à la boîte de dialogue **nouveau projet gRPC** .</span><span class="sxs-lookup"><span data-stu-id="dc78f-115">Click **Next** to continue to the **New gRPC project** dialog.</span></span>

![Boîte de dialogue Nouveau projet gRPC](media/create-project/create-new-grpc-service.png)

<span data-ttu-id="dc78f-117">À l’heure actuelle, il existe des options limitées pour la création du service.</span><span class="sxs-lookup"><span data-stu-id="dc78f-117">At present, there are limited options for the service creation.</span></span> <span data-ttu-id="dc78f-118">La station d’accueil sera introduite plus tard dans le livre. n’activez pas cette case à cocher pour le moment et cliquez simplement sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="dc78f-118">Docker will be introduced later in the book, so leave that checkbox unchecked for now and just click **Create**.</span></span> <span data-ttu-id="dc78f-119">Votre premier projet ASP.NET Core 3,0 gRPC est généré et ajouté à la solution.</span><span class="sxs-lookup"><span data-stu-id="dc78f-119">Your first ASP.NET Core 3.0 gRPC project is generated and added to the solution.</span></span> <span data-ttu-id="dc78f-120">Si vous ne souhaitez pas savoir comment utiliser le `dotnet CLI`, passez à la section [nettoyer l’exemple de code](#clean-up-the-example-code) .</span><span class="sxs-lookup"><span data-stu-id="dc78f-120">If you don't want to know about working with the `dotnet CLI`, skip to the [Clean up the example code](#clean-up-the-example-code) section.</span></span>

## <a name="create-the-project-using-the-net-core-cli"></a><span data-ttu-id="dc78f-121">Créez le projet à l’aide de l’CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="dc78f-121">Create the project using the .NET Core CLI</span></span>

<span data-ttu-id="dc78f-122">Cette section décrit la création de solutions et de projets à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="dc78f-122">This section covers the creation of solutions and projects from the command line.</span></span>

<span data-ttu-id="dc78f-123">Créez la solution comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="dc78f-123">Create the solution as shown below.</span></span> <span data-ttu-id="dc78f-124">L' `-o` indicateur ( `--output`ou) spécifie le répertoire de sortie, qui sera créé dans le répertoire actif s’il n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="dc78f-124">The `-o` (or `--output`) flag specifies the output directory, which will be created in the current directory if it does not exist.</span></span> <span data-ttu-id="dc78f-125">La solution se verra attribuer le même nom que le répertoire, c.-à-d. `TraderSys.sln`. Vous pouvez fournir un autre nom à l' `-n` aide de `--name`l’indicateur (ou).</span><span class="sxs-lookup"><span data-stu-id="dc78f-125">The solution will be given the same name as the directory, i.e. `TraderSys.sln`. You can provide a different name using the `-n` (or `--name`) flag.</span></span>

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

<span data-ttu-id="dc78f-126">ASP.NET Core 3,0 est fourni avec un modèle CLI pour les services gRPC.</span><span class="sxs-lookup"><span data-stu-id="dc78f-126">ASP.NET Core 3.0 comes with a CLI template for gRPC services.</span></span> <span data-ttu-id="dc78f-127">Créez le projet à l’aide de ce modèle, en le `src` plaçant dans un sous-répertoire, comme la Convention pour les projets ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="dc78f-127">Create the new project using this template, putting it into an `src` subdirectory as is the convention for ASP.NET Core projects.</span></span> <span data-ttu-id="dc78f-128">Le projet est nommé d’après le répertoire (c’est-à-dire `TraderSys.Portfolios.csproj`), sauf si vous spécifiez un nom différent avec l' `-n` indicateur.</span><span class="sxs-lookup"><span data-stu-id="dc78f-128">The project will be named after the directory (i.e. `TraderSys.Portfolios.csproj`) unless you specify a different name with the `-n` flag.</span></span>

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

<span data-ttu-id="dc78f-129">Enfin, ajoutez le projet à la solution à l' `dotnet sln` aide de la commande.</span><span class="sxs-lookup"><span data-stu-id="dc78f-129">Finally, add the project to the solution using the `dotnet sln` command.</span></span>

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> <span data-ttu-id="dc78f-130">Étant donné que le répertoire donné ne contient `.csproj` qu’un seul fichier, vous pouvez vous contenter de spécifier uniquement le répertoire pour enregistrer la frappe.</span><span class="sxs-lookup"><span data-stu-id="dc78f-130">Since the given directory only contains a single `.csproj` file, you can get away with specifying just the directory to save typing.</span></span>

<span data-ttu-id="dc78f-131">Vous pouvez maintenant ouvrir cette solution dans Visual Studio 2019, Visual Studio Code ou dans l’éditeur de votre choix.</span><span class="sxs-lookup"><span data-stu-id="dc78f-131">You can now open this solution in Visual Studio 2019, Visual Studio Code, or whatever editor you prefer.</span></span>

## <a name="clean-up-the-example-code"></a><span data-ttu-id="dc78f-132">Nettoyer l’exemple de code</span><span class="sxs-lookup"><span data-stu-id="dc78f-132">Clean up the example code</span></span>

<span data-ttu-id="dc78f-133">Vous avez maintenant créé un exemple de service à l’aide du modèle gRPC, qui a été révisé précédemment dans le livre.</span><span class="sxs-lookup"><span data-stu-id="dc78f-133">You've now created an example service using the gRPC template, which was reviewed earlier in the book.</span></span> <span data-ttu-id="dc78f-134">Cela n’est pas utile dans notre contexte commercial boursier. nous allons donc modifier les éléments de notre premier projet.</span><span class="sxs-lookup"><span data-stu-id="dc78f-134">This isn't useful in our stock trading context, so we'll edit things for our first project.</span></span>

### <a name="rename-and-edit-the-proto-file"></a><span data-ttu-id="dc78f-135">Renommer et modifier le fichier proto</span><span class="sxs-lookup"><span data-stu-id="dc78f-135">Rename and edit the proto file</span></span>

<span data-ttu-id="dc78f-136">Continuez et renommez le `Protos/greet.proto` `Protos/portfolios.proto` fichier et ouvrez-le dans votre éditeur.</span><span class="sxs-lookup"><span data-stu-id="dc78f-136">Go ahead and rename the `Protos/greet.proto` file to `Protos/portfolios.proto` and open it in your editor.</span></span> <span data-ttu-id="dc78f-137">Tout supprimer après la `package` ligne, modifier les `option csharp_namespace`noms, `package` et `service` , et supprimer le service par `SayHello` défaut, de sorte que le code ressemble à ceci.</span><span class="sxs-lookup"><span data-stu-id="dc78f-137">Delete everything after the `package` line, then change the `option csharp_namespace`, `package` and `service` names, and remove the default `SayHello` service, so the code looks like this.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> <span data-ttu-id="dc78f-138">Le modèle n’ajoute pas `Protos` la partie espace de noms par défaut, mais il facilite la conservation des classes générées par gRPC et de vos propres classes clairement séparées dans votre code.</span><span class="sxs-lookup"><span data-stu-id="dc78f-138">The template doesn't add the `Protos` namespace part by default, but adding it makes it easier to keep gRPC-generated classes and your own classes clearly separated in your code.</span></span>

<span data-ttu-id="dc78f-139">Si vous renommez `greet.proto` le fichier dans un environnement de développement intégré (IDE) tel que Visual Studio, une référence à ce fichier est automatiquement `.csproj` mise à jour dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="dc78f-139">If you rename the `greet.proto` file in an integrated development environment (IDE) like Visual Studio, a reference to this file is automatically updated in the `.csproj` file.</span></span> <span data-ttu-id="dc78f-140">Mais dans d’autres éditeurs, tels que Visual Studio Code, cette référence n’est pas mise à jour automatiquement. vous devez donc modifier le fichier projet manuellement.</span><span class="sxs-lookup"><span data-stu-id="dc78f-140">But in some other editor, such as Visual Studio Code, this reference isn't updated automatically, so you need to edit the project file manually.</span></span>

<span data-ttu-id="dc78f-141">Dans les cibles de génération gRPC, il existe `Protobuf` un élément item qui vous permet de `.proto` spécifier les fichiers qui doivent être compilés et la forme de génération de code requise (c’est-à-dire « Server » ou « client »).</span><span class="sxs-lookup"><span data-stu-id="dc78f-141">In the gRPC build targets, there's a `Protobuf` item element that lets you specify which `.proto` files should be compiled and which form of code generation is required (that is, "Server" or "Client").</span></span>

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a><span data-ttu-id="dc78f-142">Renommer la classe GreeterService</span><span class="sxs-lookup"><span data-stu-id="dc78f-142">Rename the GreeterService class</span></span>

<span data-ttu-id="dc78f-143">La `GreeterService` classe se trouve dans `Services` le dossier et hérite `Greeter.GreeterBase`de.</span><span class="sxs-lookup"><span data-stu-id="dc78f-143">The `GreeterService` class is in the `Services` folder and inherits from `Greeter.GreeterBase`.</span></span> <span data-ttu-id="dc78f-144">Renommez- `PortfolioService` le et remplacez la classe de `Portfolios.PortfoliosBase`base par.</span><span class="sxs-lookup"><span data-stu-id="dc78f-144">Rename it to `PortfolioService` and change the base class to `Portfolios.PortfoliosBase`.</span></span> <span data-ttu-id="dc78f-145">Supprimez `override` les méthodes.</span><span class="sxs-lookup"><span data-stu-id="dc78f-145">Delete the `override` methods.</span></span>

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

<span data-ttu-id="dc78f-146">Il y a eu une référence `GreeterService` à la classe `Configure` dans la méthode `Startup` de la classe.</span><span class="sxs-lookup"><span data-stu-id="dc78f-146">There was a reference to the `GreeterService` class in the `Configure` method in the `Startup` class.</span></span> <span data-ttu-id="dc78f-147">Si vous avez utilisé la refactorisation pour renommer la classe, cette référence doit avoir été mise à jour automatiquement.</span><span class="sxs-lookup"><span data-stu-id="dc78f-147">If you used refactoring to rename the class, this reference should have been updated automatically.</span></span> <span data-ttu-id="dc78f-148">Toutefois, si vous ne l’avez pas fait, vous devez le modifier manuellement.</span><span class="sxs-lookup"><span data-stu-id="dc78f-148">However, if you didn't, you need to edit it manually.</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

<span data-ttu-id="dc78f-149">Dans la section suivante, nous ajouterons des fonctionnalités à ce nouveau service.</span><span class="sxs-lookup"><span data-stu-id="dc78f-149">In the next section, we'll add functionality to this new service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="dc78f-150">[Précédent](migrate-wcf-to-grpc.md)
>[Suivant](migrate-request-reply.md)</span><span class="sxs-lookup"><span data-stu-id="dc78f-150">[Previous](migrate-wcf-to-grpc.md)
[Next](migrate-request-reply.md)</span></span>
