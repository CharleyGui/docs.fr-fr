---
title: Exposer les composants de base .NET à COM
description: Ce tutoriel vous montre comment exposer une classe à COM de .NET Core. Vous générez un serveur COM et un manifeste de serveur côte à côte pour Le COM sans enregistrement.
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 98d303c99693a8aadb23da509a700772db69c0e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146656"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="ba142-104">Exposer les composants de base .NET à COM</span><span class="sxs-lookup"><span data-stu-id="ba142-104">Exposing .NET Core components to COM</span></span>

<span data-ttu-id="ba142-105">Dans .NET Core, le processus d’exposition de vos objets .NET à COM a été considérablement simplifié par rapport au .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ba142-105">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="ba142-106">Le processus suivant vous guide tout au long de l’exposition d’une classe à COM.</span><span class="sxs-lookup"><span data-stu-id="ba142-106">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="ba142-107">Ce didacticiel vous explique les procédures suivantes :</span><span class="sxs-lookup"><span data-stu-id="ba142-107">This tutorial shows you how to:</span></span>

- <span data-ttu-id="ba142-108">Exposer une classe à COM à partir de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ba142-108">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="ba142-109">Générer un serveur COM dans le cadre de la génération de votre bibliothèque .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ba142-109">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="ba142-110">Générer automatiquement un manifeste de serveur côte à côte pour COM sans registre.</span><span class="sxs-lookup"><span data-stu-id="ba142-110">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ba142-111">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="ba142-111">Prerequisites</span></span>

- <span data-ttu-id="ba142-112">Installez [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) ou une version plus récente.</span><span class="sxs-lookup"><span data-stu-id="ba142-112">Install [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="ba142-113">Créer la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="ba142-113">Create the library</span></span>

<span data-ttu-id="ba142-114">La première étape consiste à créer la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="ba142-114">The first step is to create the library.</span></span>

1. <span data-ttu-id="ba142-115">Créez un nouveau dossier et, dans ce dossier, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ba142-115">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new classlib
    ```

2. <span data-ttu-id="ba142-116">Ouvrez `Class1.cs`.</span><span class="sxs-lookup"><span data-stu-id="ba142-116">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="ba142-117">Ajoutez `using System.Runtime.InteropServices;` en haut du fichier.</span><span class="sxs-lookup"><span data-stu-id="ba142-117">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="ba142-118">Créez une interface nommée `IServer`.</span><span class="sxs-lookup"><span data-stu-id="ba142-118">Create an interface named `IServer`.</span></span> <span data-ttu-id="ba142-119">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ba142-119">For example:</span></span>

   ```csharp
   using System;
   using System.Runtime.InteropServices;

   [ComVisible(true)]
   [Guid(ContractGuids.ServerInterface)]
   [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
   public interface IServer
   {
       /// <summary>
       /// Compute the value of the constant Pi.
       /// </summary>
       double ComputePi();
   }
   ```

5. <span data-ttu-id="ba142-120">Ajoutez l’attribut `[Guid("<IID>")]` à l’interface, avec le GUID d’interface pour l’interface COM que vous implémentez.</span><span class="sxs-lookup"><span data-stu-id="ba142-120">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="ba142-121">Par exemple : `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span><span class="sxs-lookup"><span data-stu-id="ba142-121">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="ba142-122">Notez que ce GUID doit être unique, car il s’agit du seul identificateur de cette interface pour COM.</span><span class="sxs-lookup"><span data-stu-id="ba142-122">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="ba142-123">Dans Visual Studio, vous pouvez générer un GUID en accédant à Outils > Créer un GUID pour ouvrir l’outil Créer un GUID.</span><span class="sxs-lookup"><span data-stu-id="ba142-123">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="ba142-124">Ajoutez l’attribut `[InterfaceType]` à l’interface et spécifiez les interfaces COM de base que votre interface doit implémenter.</span><span class="sxs-lookup"><span data-stu-id="ba142-124">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="ba142-125">Créez une classe nommée `Server` qui implémente `IServer`.</span><span class="sxs-lookup"><span data-stu-id="ba142-125">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="ba142-126">Ajoutez l’attribut `[Guid("<CLSID>")]` à la classe, avec le GUID de l’identificateur de classe pour la classe COM que vous implémentez.</span><span class="sxs-lookup"><span data-stu-id="ba142-126">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="ba142-127">Par exemple : `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span><span class="sxs-lookup"><span data-stu-id="ba142-127">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="ba142-128">Comme avec le GUID d’interface, ce GUID doit être unique, car il est le seul identificateur de cette interface pour COM.</span><span class="sxs-lookup"><span data-stu-id="ba142-128">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="ba142-129">Ajoutez l’attribut `[ComVisible(true)]` à la fois à l’interface et à la classe.</span><span class="sxs-lookup"><span data-stu-id="ba142-129">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ba142-130">Contrairement au .NET Framework, .NET Core vous oblige à spécifier le CLSID des classes que vous voulez rendre activables via COM.</span><span class="sxs-lookup"><span data-stu-id="ba142-130">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="ba142-131">Générer l’hôte COM</span><span class="sxs-lookup"><span data-stu-id="ba142-131">Generate the COM host</span></span>

1. <span data-ttu-id="ba142-132">Ouvrez le fichier projet `.csproj` et ajoutez `<EnableComHosting>true</EnableComHosting>` à l’intérieur d’une balise `<PropertyGroup></PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="ba142-132">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="ba142-133">Créez le projet.</span><span class="sxs-lookup"><span data-stu-id="ba142-133">Build the project.</span></span>

<span data-ttu-id="ba142-134">La sortie résultante a un fichier `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` et `ProjectName.comhost.dll`.</span><span class="sxs-lookup"><span data-stu-id="ba142-134">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="ba142-135">Inscrire l’hôte COM pour COM</span><span class="sxs-lookup"><span data-stu-id="ba142-135">Register the COM host for COM</span></span>

<span data-ttu-id="ba142-136">Ouvrez une invite de commandes avec élévation de privilèges et exécutez `regsvr32 ProjectName.comhost.dll`.</span><span class="sxs-lookup"><span data-stu-id="ba142-136">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="ba142-137">Ceci inscrit tous vos objets .NET exposés auprès de COM.</span><span class="sxs-lookup"><span data-stu-id="ba142-137">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="ba142-138">Activation de COM sans registre</span><span class="sxs-lookup"><span data-stu-id="ba142-138">Enabling RegFree COM</span></span>

1. <span data-ttu-id="ba142-139">Ouvrez le fichier projet `.csproj` et ajoutez `<EnableRegFreeCom>true</EnableRegFreeCom>` à l’intérieur d’une balise `<PropertyGroup></PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="ba142-139">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="ba142-140">Créez le projet.</span><span class="sxs-lookup"><span data-stu-id="ba142-140">Build the project.</span></span>

<span data-ttu-id="ba142-141">La sortie résultante a un fichier `ProjectName.X.manifest`.</span><span class="sxs-lookup"><span data-stu-id="ba142-141">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="ba142-142">Ce fichier est le manifeste côte à côte à utiliser avec COM sans registre.</span><span class="sxs-lookup"><span data-stu-id="ba142-142">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="ba142-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="ba142-143">Sample</span></span>

<span data-ttu-id="ba142-144">Un [exemple de serveur COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) entièrement fonctionnel se trouve dans le dépôt dotnet/samples sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="ba142-144">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="ba142-145">Remarques supplémentaires</span><span class="sxs-lookup"><span data-stu-id="ba142-145">Additional notes</span></span>

<span data-ttu-id="ba142-146">Contrairement au .NET Framework, .NET Core ne prend pas en charge la génération d’une bibliothèque de types COM à partir d’un assembly .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ba142-146">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="ba142-147">L’orientation est soit d’écrire manuellement un fichier IDL ou un en-tête C /C pour les déclarations natives des interfaces COM.</span><span class="sxs-lookup"><span data-stu-id="ba142-147">The guidance is to either manually write an IDL file or a C/C++ header for the native declarations of the COM interfaces.</span></span>

<span data-ttu-id="ba142-148">En outre, le chargement à la fois .NET Framework et .NET Core dans le même processus a des limitations diagnostiques.</span><span class="sxs-lookup"><span data-stu-id="ba142-148">Additionally, loading both .NET Framework and .NET Core into the same process does have diagnostic limitations.</span></span> <span data-ttu-id="ba142-149">La principale limitation est le débogage des composants gérés car il n’est pas possible de déboguer à la fois .NET Framework et .NET Core en même temps.</span><span class="sxs-lookup"><span data-stu-id="ba142-149">The primary limitation is the debugging of managed components as it is not possible to debug both .NET Framework and .NET Core at the same time.</span></span> <span data-ttu-id="ba142-150">En outre, les deux instances de temps d’exécution ne partagent pas les assemblages gérés.</span><span class="sxs-lookup"><span data-stu-id="ba142-150">In addition, the two runtime instances don't share managed assemblies.</span></span> <span data-ttu-id="ba142-151">Cela signifie qu’il n’est pas possible de partager les types .NET réels à travers les deux temps d’exécution et au lieu de cela toutes les interactions doivent être limitées aux contrats d’interface COM exposés.</span><span class="sxs-lookup"><span data-stu-id="ba142-151">This means that it isn't possible to share actual .NET types across the two runtimes and instead all interactions must be restricted to the exposed COM interface contracts.</span></span>
