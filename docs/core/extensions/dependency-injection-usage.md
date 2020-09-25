---
title: Utiliser l’injection de dépendances dans .NET
description: Découvrez comment utiliser l’injection de dépendances dans vos applications .NET.
author: IEvangelist
ms.author: dapine
ms.date: 09/23/2020
ms.topic: tutorial
ms.openlocfilehash: f2298cb0be6d555a7636903dc251f022a6a62a43
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247893"
---
# <a name="tutorial-use-dependency-injection-in-net"></a><span data-ttu-id="4454a-103">Didacticiel : utiliser l’injection de dépendances dans .NET</span><span class="sxs-lookup"><span data-stu-id="4454a-103">Tutorial: Use dependency injection in .NET</span></span>

<span data-ttu-id="4454a-104">Ce didacticiel montre comment utiliser [l’injection de dépendances (di) dans .net](dependency-injection.md).</span><span class="sxs-lookup"><span data-stu-id="4454a-104">This tutorial shows how to use [dependency injection (DI) in .NET](dependency-injection.md).</span></span> <span data-ttu-id="4454a-105">Avec les *extensions Microsoft*, di est un citoyen de première classe dans lequel les services sont ajoutés et configurés dans un <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> .</span><span class="sxs-lookup"><span data-stu-id="4454a-105">With *Microsoft Extensions*, DI is a first-class citizen where services are added and configured in an <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="4454a-106">L' <xref:Microsoft.Extensions.Hosting.IHost> interface expose l' <xref:System.IServiceProvider> instance, qui joue le rôle de conteneur de tous les services inscrits.</span><span class="sxs-lookup"><span data-stu-id="4454a-106">The <xref:Microsoft.Extensions.Hosting.IHost> interface exposes the <xref:System.IServiceProvider> instance, which acts as a container of all the registered services.</span></span>

<span data-ttu-id="4454a-107">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="4454a-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="4454a-108">Créer une application console .NET qui utilise l’injection de dépendances</span><span class="sxs-lookup"><span data-stu-id="4454a-108">Create a .NET console app that uses dependency injection</span></span>
> - <span data-ttu-id="4454a-109">Créer et configurer un [hôte générique](generic-host.md)</span><span class="sxs-lookup"><span data-stu-id="4454a-109">Build and configure a [Generic Host](generic-host.md)</span></span>
> - <span data-ttu-id="4454a-110">Écrire plusieurs interfaces et implémentations correspondantes</span><span class="sxs-lookup"><span data-stu-id="4454a-110">Write several interfaces and corresponding implementations</span></span>
> - <span data-ttu-id="4454a-111">Utiliser la durée de vie et l’étendue du service pour DI</span><span class="sxs-lookup"><span data-stu-id="4454a-111">Use service lifetime and scoping for DI</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4454a-112">Prérequis</span><span class="sxs-lookup"><span data-stu-id="4454a-112">Prerequisites</span></span>

- <span data-ttu-id="4454a-113">[Kit de développement logiciel (SDK) .net Core 3,1](https://dotnet.microsoft.com/download/dotnet-core) ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="4454a-113">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="4454a-114">Un environnement de développement intégré (IDE), [Visual Studio, Visual Studio code ou Visual Studio pour Mac](https://visualstudio.microsoft.com) sont tous des choix valides.</span><span class="sxs-lookup"><span data-stu-id="4454a-114">An Integrated Development Environment (IDE), [Visual Studio, Visual Studio Code, or Visual Studio for Mac](https://visualstudio.microsoft.com) are all valid choices.</span></span>
- <span data-ttu-id="4454a-115">Vous êtes familiarisé avec la création d’applications .NET et l’installation de packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="4454a-115">Familiarity with creating new .NET applications and installing NuGet packages.</span></span>

## <a name="create-a-new-console-application"></a><span data-ttu-id="4454a-116">Créer une application console</span><span class="sxs-lookup"><span data-stu-id="4454a-116">Create a new console application</span></span>

<span data-ttu-id="4454a-117">À l’aide de la commande [dotnet New](../tools/dotnet-new.md) ou de l’Assistant Nouveau projet IDE, créez une nouvelle application console .NET nommée **ConsoleDI. example**.</span><span class="sxs-lookup"><span data-stu-id="4454a-117">Using either the [dotnet new](../tools/dotnet-new.md) command or an IDE new project wizard, create a new .NET console application named **ConsoleDI.Example**.</span></span> <span data-ttu-id="4454a-118">Ajoutez le package NuGet [Microsoft. extensions. Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) au projet.</span><span class="sxs-lookup"><span data-stu-id="4454a-118">Add the [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet package to the project.</span></span>

## <a name="add-interfaces"></a><span data-ttu-id="4454a-119">Ajouter des interfaces</span><span class="sxs-lookup"><span data-stu-id="4454a-119">Add interfaces</span></span>

<span data-ttu-id="4454a-120">Ajoutez les interfaces suivantes au répertoire racine du projet :</span><span class="sxs-lookup"><span data-stu-id="4454a-120">Add the following interfaces to the project root directory:</span></span>

<span data-ttu-id="4454a-121">*IOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="4454a-121">*IOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/IOperation.cs":::

<span data-ttu-id="4454a-122">L' `IOperation` interface définit une seule `OperationId` propriété.</span><span class="sxs-lookup"><span data-stu-id="4454a-122">The `IOperation` interface defines a single `OperationId` property.</span></span>

<span data-ttu-id="4454a-123">*ITransientOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="4454a-123">*ITransientOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/ITransientOperation.cs":::

<span data-ttu-id="4454a-124">*IScopedOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="4454a-124">*IScopedOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/IScopedOperation.cs":::

<span data-ttu-id="4454a-125">*ISingletonOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="4454a-125">*ISingletonOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/ISingletonOperation.cs":::

<span data-ttu-id="4454a-126">Toutes les sous-interfaces de `IOperation` nom leur durée de vie de service prévue.</span><span class="sxs-lookup"><span data-stu-id="4454a-126">All of the subinterfaces of `IOperation` name their intended service lifetime.</span></span> <span data-ttu-id="4454a-127">Par exemple, « Transient » ou « singleton ».</span><span class="sxs-lookup"><span data-stu-id="4454a-127">For example, "Transient" or "Singleton".</span></span>

## <a name="add-default-implementation"></a><span data-ttu-id="4454a-128">Ajouter une implémentation par défaut</span><span class="sxs-lookup"><span data-stu-id="4454a-128">Add default implementation</span></span>

<span data-ttu-id="4454a-129">Ajoutez l’implémentation par défaut suivante pour les diverses opérations :</span><span class="sxs-lookup"><span data-stu-id="4454a-129">Add the following default implementation for the various operations:</span></span>

<span data-ttu-id="4454a-130">*DefaultOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="4454a-130">*DefaultOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/DefaultOperation.cs":::

<span data-ttu-id="4454a-131">`DefaultOperation`Implémente toutes les interfaces nommées/de marqueur et initialise la `OperationId` propriété aux quatre derniers caractères d’un nouvel identificateur global unique (Guid).</span><span class="sxs-lookup"><span data-stu-id="4454a-131">The `DefaultOperation` implements all of the named/marker interfaces and initializes the `OperationId` property to the last four characters of a new globally unique identifier (GUID).</span></span>

## <a name="add-service-that-requires-di"></a><span data-ttu-id="4454a-132">Ajouter un service qui requiert DI</span><span class="sxs-lookup"><span data-stu-id="4454a-132">Add service that requires DI</span></span>

<span data-ttu-id="4454a-133">Ajoutez l’objet logger d’opération suivant, qui agit en tant que service à votre application console :</span><span class="sxs-lookup"><span data-stu-id="4454a-133">Add the following operation logger object, which acts as a service to your console application:</span></span>

<span data-ttu-id="4454a-134">*OperationLogger.cs*</span><span class="sxs-lookup"><span data-stu-id="4454a-134">*OperationLogger.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/OperationLogger.cs":::

<span data-ttu-id="4454a-135">Le `OperationLogger` définit un constructeur qui requiert chacune des interfaces de marqueur susmentionnées, autrement dit ; `ITransientOperation` , `IScopedOperation` et `ISingletonOperation` .</span><span class="sxs-lookup"><span data-stu-id="4454a-135">The `OperationLogger` defines a constructor that requires each of the aforementioned marker interfaces, that is; `ITransientOperation`, `IScopedOperation`, and `ISingletonOperation`.</span></span> <span data-ttu-id="4454a-136">L’objet expose une méthode unique qui permet au consommateur d’enregistrer les opérations avec un `scope` paramètre donné.</span><span class="sxs-lookup"><span data-stu-id="4454a-136">The object exposes a single method that allows the consumer to log the operations with a given `scope` parameter.</span></span> <span data-ttu-id="4454a-137">Lorsqu’elle est appelée, la `LogOperations` méthode enregistre l’identificateur unique de chaque opération avec la chaîne et le message de l’étendue.</span><span class="sxs-lookup"><span data-stu-id="4454a-137">When invoked, the `LogOperations` method will log each operation's unique identifier with the scope string and message.</span></span>

## <a name="register-services-for-di"></a><span data-ttu-id="4454a-138">Inscrire des services pour DI</span><span class="sxs-lookup"><span data-stu-id="4454a-138">Register services for DI</span></span>

<span data-ttu-id="4454a-139">Enfin, mettez à jour le fichier *Program.cs* pour qu’il corresponde à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="4454a-139">Finally, update the *Program.cs* file to match following:</span></span>

:::code language="csharp" source="snippets/configuration/console-di/Program.cs" range="1-18,35-60" highlight="22-26":::

<span data-ttu-id="4454a-140">L’application :</span><span class="sxs-lookup"><span data-stu-id="4454a-140">The application:</span></span>

- <span data-ttu-id="4454a-141">Crée une <xref:Microsoft.Extensions.Hosting.IHostBuilder> instance avec les [paramètres de binder par défaut](generic-host.md#default-builder-settings).</span><span class="sxs-lookup"><span data-stu-id="4454a-141">Creates an <xref:Microsoft.Extensions.Hosting.IHostBuilder> instance with the [default binder settings](generic-host.md#default-builder-settings).</span></span>
- <span data-ttu-id="4454a-142">Configure les services et les ajoute avec leur durée de vie de service correspondante.</span><span class="sxs-lookup"><span data-stu-id="4454a-142">Configures services and adds them with their corresponding service lifetime.</span></span>
- <span data-ttu-id="4454a-143">Appelle <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> et assigne une instance de <xref:Microsoft.Extensions.Hosting.IHost> .</span><span class="sxs-lookup"><span data-stu-id="4454a-143">Calls <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> and assigns an instance of <xref:Microsoft.Extensions.Hosting.IHost>.</span></span>
- <span data-ttu-id="4454a-144">Appelle `ExemplifyScoping` , en passant le <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4454a-144">Calls `ExemplifyScoping`, passing in the <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType>.</span></span>

## <a name="conclusion"></a><span data-ttu-id="4454a-145">Conclusion</span><span class="sxs-lookup"><span data-stu-id="4454a-145">Conclusion</span></span>

<span data-ttu-id="4454a-146">L’application produit une sortie similaire à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4454a-146">The application produces output similar to the following example:</span></span>

```console
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ 80f4...Always different        ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ f3c0...Always different        ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]

Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ f9af...Always different        ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ fa65...Always different        ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
```

<span data-ttu-id="4454a-147">À partir de la sortie de l’application, vous pouvez voir que :</span><span class="sxs-lookup"><span data-stu-id="4454a-147">From the application output, you can see that:</span></span>

- <span data-ttu-id="4454a-148">Les opérations transitoires sont toujours différentes, ce qui signifie qu’une nouvelle instance est créée avec chaque récupération du service.</span><span class="sxs-lookup"><span data-stu-id="4454a-148">Transient operations are always different, meaning a new instance is created with every retrieval of the service.</span></span>
- <span data-ttu-id="4454a-149">Les opérations délimitées changent uniquement avec une nouvelle étendue, mais sont la même instance au sein d’une étendue.</span><span class="sxs-lookup"><span data-stu-id="4454a-149">Scoped operations change only with a new scope, but are the same instance within a scope.</span></span>
- <span data-ttu-id="4454a-150">Les opérations Singleton sont toujours les mêmes, ce qui signifie qu’une nouvelle instance n’est créée qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="4454a-150">Singleton operations are always the same, meaning a new instance is only created once.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4454a-151">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="4454a-151">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4454a-152">Instructions relatives à l’injection de dépendances</span><span class="sxs-lookup"><span data-stu-id="4454a-152">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
