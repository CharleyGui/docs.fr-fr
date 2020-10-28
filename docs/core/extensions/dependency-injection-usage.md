---
title: Utiliser l’injection de dépendances dans .NET
description: Découvrez comment utiliser l’injection de dépendances dans vos applications .NET.
author: IEvangelist
ms.author: dapine
ms.date: 09/23/2020
ms.topic: tutorial
no-loc:
- ':::no-loc(Transient):::'
- ':::no-loc(Scoped):::'
- ':::no-loc(Singleton):::'
- ':::no-loc(Example):::'
ms.openlocfilehash: 589e15736c07b465fda308b04c91384a2502755c
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888584"
---
# <a name="tutorial-use-dependency-injection-in-net"></a><span data-ttu-id="f22d6-103">Didacticiel : utiliser l’injection de dépendances dans .NET</span><span class="sxs-lookup"><span data-stu-id="f22d6-103">Tutorial: Use dependency injection in .NET</span></span>

<span data-ttu-id="f22d6-104">Ce didacticiel montre comment utiliser [l’injection de dépendances (di) dans .net](dependency-injection.md).</span><span class="sxs-lookup"><span data-stu-id="f22d6-104">This tutorial shows how to use [dependency injection (DI) in .NET](dependency-injection.md).</span></span> <span data-ttu-id="f22d6-105">Avec les *extensions Microsoft* , di est un citoyen de première classe dans lequel les services sont ajoutés et configurés dans un <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> .</span><span class="sxs-lookup"><span data-stu-id="f22d6-105">With *Microsoft Extensions* , DI is a first-class citizen where services are added and configured in an <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="f22d6-106">L' <xref:Microsoft.Extensions.Hosting.IHost> interface expose l' <xref:System.IServiceProvider> instance, qui joue le rôle de conteneur de tous les services inscrits.</span><span class="sxs-lookup"><span data-stu-id="f22d6-106">The <xref:Microsoft.Extensions.Hosting.IHost> interface exposes the <xref:System.IServiceProvider> instance, which acts as a container of all the registered services.</span></span>

<span data-ttu-id="f22d6-107">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="f22d6-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="f22d6-108">Créer une application console .NET qui utilise l’injection de dépendances</span><span class="sxs-lookup"><span data-stu-id="f22d6-108">Create a .NET console app that uses dependency injection</span></span>
> - <span data-ttu-id="f22d6-109">Créer et configurer un [hôte générique](generic-host.md)</span><span class="sxs-lookup"><span data-stu-id="f22d6-109">Build and configure a [Generic Host](generic-host.md)</span></span>
> - <span data-ttu-id="f22d6-110">Écrire plusieurs interfaces et implémentations correspondantes</span><span class="sxs-lookup"><span data-stu-id="f22d6-110">Write several interfaces and corresponding implementations</span></span>
> - <span data-ttu-id="f22d6-111">Utiliser la durée de vie et l’étendue du service pour DI</span><span class="sxs-lookup"><span data-stu-id="f22d6-111">Use service lifetime and scoping for DI</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f22d6-112">Prérequis</span><span class="sxs-lookup"><span data-stu-id="f22d6-112">Prerequisites</span></span>

- <span data-ttu-id="f22d6-113">[.Net Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="f22d6-113">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or later.</span></span>
- <span data-ttu-id="f22d6-114">Vous êtes familiarisé avec la création d’applications .NET et l’installation de packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="f22d6-114">Familiarity with creating new .NET applications and installing NuGet packages.</span></span>

## <a name="create-a-new-console-application"></a><span data-ttu-id="f22d6-115">Créer une application console</span><span class="sxs-lookup"><span data-stu-id="f22d6-115">Create a new console application</span></span>

<span data-ttu-id="f22d6-116">À l’aide de la commande [dotnet New](../tools/dotnet-new.md) ou de l’Assistant Nouveau projet IDE, créez une nouvelle application console .NET nommée **ConsoleDI. :::no-loc(Example):::** .</span><span class="sxs-lookup"><span data-stu-id="f22d6-116">Using either the [dotnet new](../tools/dotnet-new.md) command or an IDE new project wizard, create a new .NET console application named **ConsoleDI.:::no-loc(Example):::** .</span></span> <span data-ttu-id="f22d6-117">Ajoutez le package NuGet [Microsoft. extensions. Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) au projet.</span><span class="sxs-lookup"><span data-stu-id="f22d6-117">Add the [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet package to the project.</span></span>

## <a name="add-interfaces"></a><span data-ttu-id="f22d6-118">Ajouter des interfaces</span><span class="sxs-lookup"><span data-stu-id="f22d6-118">Add interfaces</span></span>

<span data-ttu-id="f22d6-119">Ajoutez les interfaces suivantes au répertoire racine du projet :</span><span class="sxs-lookup"><span data-stu-id="f22d6-119">Add the following interfaces to the project root directory:</span></span>

<span data-ttu-id="f22d6-120">*IOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="f22d6-120">*IOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/IOperation.cs":::

<span data-ttu-id="f22d6-121">L' `IOperation` interface définit une seule `OperationId` propriété.</span><span class="sxs-lookup"><span data-stu-id="f22d6-121">The `IOperation` interface defines a single `OperationId` property.</span></span>

<span data-ttu-id="f22d6-122">*Je :::no-loc(Transient)::: operation.cs*</span><span class="sxs-lookup"><span data-stu-id="f22d6-122">*I:::no-loc(Transient):::Operation.cs*</span></span>

<span data-ttu-id="f22d6-123">::: code Language = "CSharp" source = "extraits/configuration/console-di/I :::no-loc(Transient)::: operation.cs" :::</span><span class="sxs-lookup"><span data-stu-id="f22d6-123">:::code language="csharp" source="snippets/configuration/console-di/I:::no-loc(Transient):::Operation.cs":::</span></span>

<span data-ttu-id="f22d6-124">*Je :::no-loc(Scoped)::: operation.cs*</span><span class="sxs-lookup"><span data-stu-id="f22d6-124">*I:::no-loc(Scoped):::Operation.cs*</span></span>

<span data-ttu-id="f22d6-125">::: code Language = "CSharp" source = "extraits/configuration/console-di/I :::no-loc(Scoped)::: operation.cs" :::</span><span class="sxs-lookup"><span data-stu-id="f22d6-125">:::code language="csharp" source="snippets/configuration/console-di/I:::no-loc(Scoped):::Operation.cs":::</span></span>

<span data-ttu-id="f22d6-126">*Je :::no-loc(Singleton)::: operation.cs*</span><span class="sxs-lookup"><span data-stu-id="f22d6-126">*I:::no-loc(Singleton):::Operation.cs*</span></span>

<span data-ttu-id="f22d6-127">::: code Language = "CSharp" source = "extraits/configuration/console-di/I :::no-loc(Singleton)::: operation.cs" :::</span><span class="sxs-lookup"><span data-stu-id="f22d6-127">:::code language="csharp" source="snippets/configuration/console-di/I:::no-loc(Singleton):::Operation.cs":::</span></span>

<span data-ttu-id="f22d6-128">Toutes les sous-interfaces de `IOperation` nom leur durée de vie de service prévue.</span><span class="sxs-lookup"><span data-stu-id="f22d6-128">All of the subinterfaces of `IOperation` name their intended service lifetime.</span></span> <span data-ttu-id="f22d6-129">Par exemple, « :::no-loc(Transient)::: » ou «» :::no-loc(Singleton)::: .</span><span class="sxs-lookup"><span data-stu-id="f22d6-129">For example, ":::no-loc(Transient):::" or ":::no-loc(Singleton):::".</span></span>

## <a name="add-default-implementation"></a><span data-ttu-id="f22d6-130">Ajouter une implémentation par défaut</span><span class="sxs-lookup"><span data-stu-id="f22d6-130">Add default implementation</span></span>

<span data-ttu-id="f22d6-131">Ajoutez l’implémentation par défaut suivante pour les diverses opérations :</span><span class="sxs-lookup"><span data-stu-id="f22d6-131">Add the following default implementation for the various operations:</span></span>

<span data-ttu-id="f22d6-132">*DefaultOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="f22d6-132">*DefaultOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/DefaultOperation.cs":::

<span data-ttu-id="f22d6-133">`DefaultOperation`Implémente toutes les interfaces de marqueur nommées et initialise la `OperationId` propriété avec les quatre derniers caractères d’un nouvel identificateur global unique (Guid).</span><span class="sxs-lookup"><span data-stu-id="f22d6-133">The `DefaultOperation` implements all of the named marker interfaces and initializes the `OperationId` property to the last four characters of a new globally unique identifier (GUID).</span></span>

## <a name="add-service-that-requires-di"></a><span data-ttu-id="f22d6-134">Ajouter un service qui requiert DI</span><span class="sxs-lookup"><span data-stu-id="f22d6-134">Add service that requires DI</span></span>

<span data-ttu-id="f22d6-135">Ajoutez l’objet logger d’opération suivant, qui agit en tant que service à l’application console :</span><span class="sxs-lookup"><span data-stu-id="f22d6-135">Add the following operation logger object, which acts as a service to the console app:</span></span>

<span data-ttu-id="f22d6-136">*OperationLogger.cs*</span><span class="sxs-lookup"><span data-stu-id="f22d6-136">*OperationLogger.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/OperationLogger.cs":::

<span data-ttu-id="f22d6-137">Le `OperationLogger` définit un constructeur qui requiert chacune des interfaces de marqueur susmentionnées, autrement dit ; `I:::no-loc(Transient):::Operation` , `I:::no-loc(Scoped):::Operation` et `I:::no-loc(Singleton):::Operation` .</span><span class="sxs-lookup"><span data-stu-id="f22d6-137">The `OperationLogger` defines a constructor that requires each of the aforementioned marker interfaces, that is; `I:::no-loc(Transient):::Operation`, `I:::no-loc(Scoped):::Operation`, and `I:::no-loc(Singleton):::Operation`.</span></span> <span data-ttu-id="f22d6-138">L’objet expose une méthode unique qui permet au consommateur d’enregistrer les opérations avec un `scope` paramètre donné.</span><span class="sxs-lookup"><span data-stu-id="f22d6-138">The object exposes a single method that allows the consumer to log the operations with a given `scope` parameter.</span></span> <span data-ttu-id="f22d6-139">Lorsqu’elle est appelée, la `LogOperations` méthode journalise l’identificateur unique de chaque opération avec la chaîne et le message de l’étendue.</span><span class="sxs-lookup"><span data-stu-id="f22d6-139">When invoked, the `LogOperations` method logs each operation's unique identifier with the scope string and message.</span></span>

## <a name="register-services-for-di"></a><span data-ttu-id="f22d6-140">Inscrire des services pour DI</span><span class="sxs-lookup"><span data-stu-id="f22d6-140">Register services for DI</span></span>

<span data-ttu-id="f22d6-141">Mettez à jour *Program.cs* avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="f22d6-141">Update *Program.cs* with the following code:</span></span>

:::code language="csharp" source="snippets/configuration/console-di/Program.cs" range="1-18,35-60" highlight="22-26":::

<span data-ttu-id="f22d6-142">L’application :</span><span class="sxs-lookup"><span data-stu-id="f22d6-142">The app:</span></span>

- <span data-ttu-id="f22d6-143">Crée une <xref:Microsoft.Extensions.Hosting.IHostBuilder> instance avec les [paramètres de binder par défaut](generic-host.md#default-builder-settings).</span><span class="sxs-lookup"><span data-stu-id="f22d6-143">Creates an <xref:Microsoft.Extensions.Hosting.IHostBuilder> instance with the [default binder settings](generic-host.md#default-builder-settings).</span></span>
- <span data-ttu-id="f22d6-144">Configure les services et les ajoute avec leur durée de vie de service correspondante.</span><span class="sxs-lookup"><span data-stu-id="f22d6-144">Configures services and adds them with their corresponding service lifetime.</span></span>
- <span data-ttu-id="f22d6-145">Appelle <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> et assigne une instance de <xref:Microsoft.Extensions.Hosting.IHost> .</span><span class="sxs-lookup"><span data-stu-id="f22d6-145">Calls <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> and assigns an instance of <xref:Microsoft.Extensions.Hosting.IHost>.</span></span>
- <span data-ttu-id="f22d6-146">Appelle `ExemplifyScoping` , en passant le <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f22d6-146">Calls `ExemplifyScoping`, passing in the <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType>.</span></span>

## <a name="conclusion"></a><span data-ttu-id="f22d6-147">Conclusion</span><span class="sxs-lookup"><span data-stu-id="f22d6-147">Conclusion</span></span>

<span data-ttu-id="f22d6-148">L’application affiche une sortie similaire à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f22d6-148">The app displays output similar to the following example:</span></span>

```console
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): I:::no-loc(Transient):::Operation [ 80f4...Always different        ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): I:::no-loc(Scoped):::Operation    [ c878...Changes only with scope ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): I:::no-loc(Singleton):::Operation [ 1586...Always the same         ]
...
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): I:::no-loc(Transient):::Operation [ f3c0...Always different        ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): I:::no-loc(Scoped):::Operation    [ c878...Changes only with scope ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): I:::no-loc(Singleton):::Operation [ 1586...Always the same         ]

Scope 2-Call 1 .GetRequiredService<OperationLogger>(): I:::no-loc(Transient):::Operation [ f9af...Always different        ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): I:::no-loc(Scoped):::Operation    [ 2bd0...Changes only with scope ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): I:::no-loc(Singleton):::Operation [ 1586...Always the same         ]
...
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): I:::no-loc(Transient):::Operation [ fa65...Always different        ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): I:::no-loc(Scoped):::Operation    [ 2bd0...Changes only with scope ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): I:::no-loc(Singleton):::Operation [ 1586...Always the same         ]
```

<span data-ttu-id="f22d6-149">À partir de la sortie de l’application, vous pouvez voir que :</span><span class="sxs-lookup"><span data-stu-id="f22d6-149">From the app output, you can see that:</span></span>

- <span data-ttu-id="f22d6-150">:::no-loc(Transient)::: les opérations sont toujours différentes, une nouvelle instance est créée avec chaque récupération du service.</span><span class="sxs-lookup"><span data-stu-id="f22d6-150">:::no-loc(Transient)::: operations are always different, a new instance is created with every retrieval of the service.</span></span>
- <span data-ttu-id="f22d6-151">:::no-loc(Scoped)::: les opérations changent uniquement avec une nouvelle étendue, mais sont la même instance au sein d’une étendue.</span><span class="sxs-lookup"><span data-stu-id="f22d6-151">:::no-loc(Scoped)::: operations change only with a new scope, but are the same instance within a scope.</span></span>
- <span data-ttu-id="f22d6-152">:::no-loc(Singleton)::: les opérations sont toujours les mêmes, une nouvelle instance n’est créée qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="f22d6-152">:::no-loc(Singleton)::: operations are always the same, a new instance is only created once.</span></span>

## <a name="see-also"></a><span data-ttu-id="f22d6-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f22d6-153">See also</span></span>

* [<span data-ttu-id="f22d6-154">Recommandations relatives à l’injection de dépendances</span><span class="sxs-lookup"><span data-stu-id="f22d6-154">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
* [<span data-ttu-id="f22d6-155">Injection de dépendances dans ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f22d6-155">Dependency injection in ASP.NET Core</span></span>](/aspnet/core/fundamentals/dependency-injection)
