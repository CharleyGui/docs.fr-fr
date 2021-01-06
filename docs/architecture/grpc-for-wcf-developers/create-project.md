---
title: Créer un nouveau ASP.NET Core projet gRPC-gRPC pour les développeurs WCF
description: Découvrez comment créer un projet gRPC à l’aide de Visual Studio ou de la ligne de commande.
ms.date: 12/15/2020
ms.openlocfilehash: 960725a9507797f43b2c15283e384b0ad827c2b1
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938652"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a><span data-ttu-id="2833d-103">Créer un projet gRPC ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2833d-103">Create a new ASP.NET Core gRPC project</span></span>

<span data-ttu-id="2833d-104">Le kit de développement logiciel (SDK) .NET est fourni avec un puissant outil CLI, `dotnet` , qui vous permet de créer et de gérer des projets et des solutions à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="2833d-104">The .NET SDK comes with a powerful CLI tool, `dotnet`, which enables you to create and manage projects and solutions from the command line.</span></span> <span data-ttu-id="2833d-105">Le kit de développement logiciel (SDK) est étroitement intégré à Visual Studio, de sorte que tout est également disponible par le biais de l’interface utilisateur graphique familière.</span><span class="sxs-lookup"><span data-stu-id="2833d-105">The SDK is closely integrated with Visual Studio, so everything is also available through the familiar graphical user interface.</span></span> <span data-ttu-id="2833d-106">Ce chapitre présente les deux façons de créer un nouveau ASP.NET Core projet gRPC.</span><span class="sxs-lookup"><span data-stu-id="2833d-106">This chapter shows both ways to create a new ASP.NET Core gRPC project.</span></span>

## <a name="create-the-project-by-using-visual-studio"></a><span data-ttu-id="2833d-107">Créer le projet à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2833d-107">Create the project by using Visual Studio</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2833d-108">Pour développer une application ASP.NET Core 5,0, vous avez besoin de Visual Studio 2019 version 16,3 ou ultérieure, avec la charge de travail **ASP.net et développement Web** installée.</span><span class="sxs-lookup"><span data-stu-id="2833d-108">To develop any ASP.NET Core 5.0 app, you need Visual Studio 2019 version 16.3 or later, with the **ASP.NET and web development** workload installed.</span></span>

<span data-ttu-id="2833d-109">Créez une solution vide appelée **Traders** à partir du modèle de *solution vide* .</span><span class="sxs-lookup"><span data-stu-id="2833d-109">Create an empty solution called **TraderSys** from the *Blank Solution* template.</span></span> <span data-ttu-id="2833d-110">Ajoutez un dossier de solution appelé `src` .</span><span class="sxs-lookup"><span data-stu-id="2833d-110">Add a solution folder called `src`.</span></span> <span data-ttu-id="2833d-111">Ensuite, cliquez avec le bouton droit sur le dossier et choisissez **Ajouter**  >  **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="2833d-111">Then, right-click on the folder and choose **Add** > **New Project**.</span></span> <span data-ttu-id="2833d-112">Entrez `grpc` dans la zone de recherche du modèle, et un modèle de projet doit s’afficher `gRPC Service` .</span><span class="sxs-lookup"><span data-stu-id="2833d-112">Enter `grpc` in the template search box, and you should see a project template called `gRPC Service`.</span></span>

![Capture d’écran de la boîte de dialogue Ajouter un nouveau projet](media/create-project/new-grpc-project.png)

<span data-ttu-id="2833d-114">Sélectionnez **suivant** pour passer à la boîte de dialogue **configurer votre nouveau projet** .</span><span class="sxs-lookup"><span data-stu-id="2833d-114">Select **Next** to continue to the **Configure your new project** dialog box.</span></span> <span data-ttu-id="2833d-115">Nommez le projet `TraderSys.Portfolios` et ajoutez un `src` sous-répertoire à l' **emplacement**.</span><span class="sxs-lookup"><span data-stu-id="2833d-115">Name the project `TraderSys.Portfolios` and add an `src` subdirectory to the **Location**.</span></span>

![Capture d’écran de la boîte de dialogue Configurer votre nouveau projet](media/create-project/configure-project.png)

<span data-ttu-id="2833d-117">Sélectionnez **suivant** pour accéder à la boîte de dialogue **créer un service gRPC** .</span><span class="sxs-lookup"><span data-stu-id="2833d-117">Select **Next** to continue to the **Create a new gRPC service** dialog box.</span></span>

![Capture d’écran de la boîte de dialogue créer un service gRPC](media/create-project/create-new-grpc-service-v2.png)

<span data-ttu-id="2833d-119">À l’heure actuelle, vous disposez d’options limitées pour la création du service.</span><span class="sxs-lookup"><span data-stu-id="2833d-119">At present, you have limited options for the service creation.</span></span> <span data-ttu-id="2833d-120">L’arrimeur sera présenté plus tard, donc pour l’instant, laissez cette option désélectionnée.</span><span class="sxs-lookup"><span data-stu-id="2833d-120">Docker will be introduced later, so for now, leave that option unselected.</span></span> <span data-ttu-id="2833d-121">Sélectionnez simplement **créer**.</span><span class="sxs-lookup"><span data-stu-id="2833d-121">Just select **Create**.</span></span> <span data-ttu-id="2833d-122">Votre premier projet ASP.NET Core 5,0 gRPC est généré et ajouté à la solution.</span><span class="sxs-lookup"><span data-stu-id="2833d-122">Your first ASP.NET Core 5.0 gRPC project is generated and added to the solution.</span></span> <span data-ttu-id="2833d-123">Si vous ne souhaitez pas savoir comment utiliser le `dotnet CLI` , passez à la section [nettoyer l’exemple de code](#clean-up-the-example-code) .</span><span class="sxs-lookup"><span data-stu-id="2833d-123">If you don't want to know about working with the `dotnet CLI`, skip to the [Clean up the example code](#clean-up-the-example-code) section.</span></span>

## <a name="create-the-project-by-using-the-net-cli"></a><span data-ttu-id="2833d-124">Créer le projet à l’aide de l’interface CLI .NET</span><span class="sxs-lookup"><span data-stu-id="2833d-124">Create the project by using the .NET CLI</span></span>

<span data-ttu-id="2833d-125">Cette section décrit la création de solutions et de projets à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="2833d-125">This section covers the creation of solutions and projects from the command line.</span></span>

<span data-ttu-id="2833d-126">Créez la solution comme indiqué dans la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="2833d-126">Create the solution as shown in the following command.</span></span> <span data-ttu-id="2833d-127">L' `-o` indicateur (ou `--output` ) spécifie le répertoire de sortie, qui est créé dans le répertoire actif s’il n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="2833d-127">The `-o` (or `--output`) flag specifies the output directory, which is created in the current directory if it doesn't already exist.</span></span> <span data-ttu-id="2833d-128">La solution porte le même nom que le répertoire : `TraderSys.sln` .</span><span class="sxs-lookup"><span data-stu-id="2833d-128">The solution has the same name as the directory: `TraderSys.sln`.</span></span> <span data-ttu-id="2833d-129">Vous pouvez fournir un autre nom à l’aide de l' `-n` indicateur (ou `--name` ).</span><span class="sxs-lookup"><span data-stu-id="2833d-129">You can provide a different name by using the `-n` (or `--name`) flag.</span></span>

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

<span data-ttu-id="2833d-130">ASP.NET Core 5,0 est fourni avec un modèle CLI pour les services gRPC.</span><span class="sxs-lookup"><span data-stu-id="2833d-130">ASP.NET Core 5.0 comes with a CLI template for gRPC services.</span></span> <span data-ttu-id="2833d-131">Créez le nouveau projet à l’aide de ce modèle, en le plaçant dans un `src` sous-répertoire comme conventionnel pour les projets ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="2833d-131">Create the new project by using this template, putting it into an `src` subdirectory as is conventional for ASP.NET Core projects.</span></span> <span data-ttu-id="2833d-132">Le projet est nommé d’après le répertoire ( `TraderSys.Portfolios.csproj` ), sauf si vous spécifiez un nom différent avec l' `-n` indicateur.</span><span class="sxs-lookup"><span data-stu-id="2833d-132">The project is named after the directory (`TraderSys.Portfolios.csproj`), unless you specify a different name with the `-n` flag.</span></span>

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

<span data-ttu-id="2833d-133">Enfin, ajoutez le projet à la solution à l’aide de la `dotnet sln` commande :</span><span class="sxs-lookup"><span data-stu-id="2833d-133">Finally, add the project to the solution by using the `dotnet sln` command:</span></span>

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> <span data-ttu-id="2833d-134">Étant donné que le répertoire particulier contient un seul `.csproj` fichier, vous pouvez spécifier uniquement le répertoire pour enregistrer la frappe.</span><span class="sxs-lookup"><span data-stu-id="2833d-134">Because the particular directory only contains a single `.csproj` file, you can specify just the directory, to save typing.</span></span>

<span data-ttu-id="2833d-135">Vous pouvez maintenant ouvrir cette solution dans Visual Studio 2019, Visual Studio Code ou dans l’éditeur de votre choix.</span><span class="sxs-lookup"><span data-stu-id="2833d-135">You can now open this solution in Visual Studio 2019, Visual Studio Code, or whatever editor you prefer.</span></span>

## <a name="clean-up-the-example-code"></a><span data-ttu-id="2833d-136">Nettoyer l’exemple de code</span><span class="sxs-lookup"><span data-stu-id="2833d-136">Clean up the example code</span></span>

<span data-ttu-id="2833d-137">Vous avez maintenant créé un exemple de service à l’aide du modèle gRPC, qui a été révisé précédemment dans le livre.</span><span class="sxs-lookup"><span data-stu-id="2833d-137">You've now created an example service by using the gRPC template, which was reviewed earlier in the book.</span></span> <span data-ttu-id="2833d-138">Ce code n’est pas utile dans notre contexte commercial des actions. nous allons donc modifier les éléments de notre premier projet.</span><span class="sxs-lookup"><span data-stu-id="2833d-138">This code isn't useful in our stock trading context, so we'll edit things for our first project.</span></span>

### <a name="rename-and-edit-the-proto-file"></a><span data-ttu-id="2833d-139">Renommer et modifier le fichier proto</span><span class="sxs-lookup"><span data-stu-id="2833d-139">Rename and edit the proto file</span></span>

<span data-ttu-id="2833d-140">Continuez et renommez le `Protos/greet.proto` fichier `Protos/portfolios.proto` , puis ouvrez-le dans votre éditeur.</span><span class="sxs-lookup"><span data-stu-id="2833d-140">Go ahead and rename the `Protos/greet.proto` file to `Protos/portfolios.proto`, and open it in your editor.</span></span> <span data-ttu-id="2833d-141">Supprimer tout après la `package` ligne.</span><span class="sxs-lookup"><span data-stu-id="2833d-141">Delete everything after the `package` line.</span></span> <span data-ttu-id="2833d-142">Modifiez ensuite les `option csharp_namespace` `package` noms, et `service` , et supprimez le `SayHello` service par défaut.</span><span class="sxs-lookup"><span data-stu-id="2833d-142">Then change the `option csharp_namespace`, `package` and `service` names, and remove the default `SayHello` service.</span></span> <span data-ttu-id="2833d-143">Le code ressemble maintenant à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="2833d-143">The code now looks like the following:</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> <span data-ttu-id="2833d-144">Le modèle n’ajoute pas la `Protos` partie espace de noms par défaut, mais il facilite la conservation des classes générées par gRPC et de vos propres classes clairement séparées dans votre code.</span><span class="sxs-lookup"><span data-stu-id="2833d-144">The template doesn't add the `Protos` namespace part by default, but adding it makes it easier to keep gRPC-generated classes and your own classes clearly separated in your code.</span></span>

<span data-ttu-id="2833d-145">Si vous renommez le `greet.proto` fichier dans un environnement de développement intégré (IDE) tel que Visual Studio, une référence à ce fichier est automatiquement mise à jour dans le `.csproj` fichier.</span><span class="sxs-lookup"><span data-stu-id="2833d-145">If you rename the `greet.proto` file in an integrated development environment (IDE) like Visual Studio, a reference to this file is automatically updated in the `.csproj` file.</span></span> <span data-ttu-id="2833d-146">Mais dans d’autres éditeurs, tels que Visual Studio Code, cette référence n’est pas mise à jour automatiquement. vous devez donc modifier le fichier projet manuellement.</span><span class="sxs-lookup"><span data-stu-id="2833d-146">But in some other editor, such as Visual Studio Code, this reference isn't updated automatically, so you need to edit the project file manually.</span></span>

<span data-ttu-id="2833d-147">Dans les cibles de génération gRPC, il existe un `Protobuf` élément item qui vous permet de spécifier les `.proto` fichiers qui doivent être compilés et la forme de génération de code requise (autrement dit, « Server » ou « client »).</span><span class="sxs-lookup"><span data-stu-id="2833d-147">In the gRPC build targets, there's a `Protobuf` item element that lets you specify which `.proto` files should be compiled, and which form of code generation is required (that is, "Server" or "Client").</span></span>

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a><span data-ttu-id="2833d-148">Renommer la `GreeterService` classe</span><span class="sxs-lookup"><span data-stu-id="2833d-148">Rename the `GreeterService` class</span></span>

<span data-ttu-id="2833d-149">La `GreeterService` classe se trouve dans le `Services` dossier et hérite de `Greeter.GreeterBase` .</span><span class="sxs-lookup"><span data-stu-id="2833d-149">The `GreeterService` class is in the `Services` folder and inherits from `Greeter.GreeterBase`.</span></span> <span data-ttu-id="2833d-150">Renommez- `PortfolioService` le et remplacez la classe de base par `Portfolios.PortfoliosBase` .</span><span class="sxs-lookup"><span data-stu-id="2833d-150">Rename it to `PortfolioService`, and change the base class to `Portfolios.PortfoliosBase`.</span></span> <span data-ttu-id="2833d-151">Supprimez les `override` méthodes.</span><span class="sxs-lookup"><span data-stu-id="2833d-151">Delete the `override` methods.</span></span>

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

<span data-ttu-id="2833d-152">Il y a eu une référence à la `GreeterService` classe dans la `Configure` méthode de la `Startup` classe.</span><span class="sxs-lookup"><span data-stu-id="2833d-152">There was a reference to the `GreeterService` class in the `Configure` method in the `Startup` class.</span></span> <span data-ttu-id="2833d-153">Si vous avez utilisé la refactorisation pour renommer la classe, cette référence doit avoir été mise à jour automatiquement.</span><span class="sxs-lookup"><span data-stu-id="2833d-153">If you used refactoring to rename the class, this reference should have been updated automatically.</span></span> <span data-ttu-id="2833d-154">Toutefois, si vous ne l’avez pas fait, vous devez le modifier manuellement.</span><span class="sxs-lookup"><span data-stu-id="2833d-154">However, if you didn't, you need to edit it manually.</span></span>

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

<span data-ttu-id="2833d-155">Dans la section suivante, nous ajouterons des fonctionnalités à ce nouveau service.</span><span class="sxs-lookup"><span data-stu-id="2833d-155">In the next section, we'll add functionality to this new service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2833d-156">[Précédent](migrate-wcf-to-grpc.md) 
> [Suivant](migrate-request-reply.md)</span><span class="sxs-lookup"><span data-stu-id="2833d-156">[Previous](migrate-wcf-to-grpc.md)
[Next](migrate-request-reply.md)</span></span>
