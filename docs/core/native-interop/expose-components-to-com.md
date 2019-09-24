---
title: Exposition de composants .NET Core à COM
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 8f9624414a2b423bd43e8790d11b70ae1ca6286d
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216226"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="f78f8-102">Exposition de composants .NET Core à COM</span><span class="sxs-lookup"><span data-stu-id="f78f8-102">Exposing .NET Core components to COM</span></span>

<span data-ttu-id="f78f8-103">Dans .NET Core, le processus d’exposition de vos objets .NET à COM a été considérablement simplifié par rapport au .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f78f8-103">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="f78f8-104">Le processus suivant vous guide tout au long de l’exposition d’une classe à COM.</span><span class="sxs-lookup"><span data-stu-id="f78f8-104">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="f78f8-105">Ce didacticiel vous montre comment effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f78f8-105">This tutorial shows you how to:</span></span>

- <span data-ttu-id="f78f8-106">Exposer une classe à COM à partir de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f78f8-106">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="f78f8-107">Générer un serveur COM dans le cadre de la génération de votre bibliothèque .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f78f8-107">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="f78f8-108">Générer automatiquement un manifeste de serveur côte à côte pour COM sans registre.</span><span class="sxs-lookup"><span data-stu-id="f78f8-108">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f78f8-109">Prérequis</span><span class="sxs-lookup"><span data-stu-id="f78f8-109">Prerequisites</span></span>

- <span data-ttu-id="f78f8-110">Installez le [Kit de développement logiciel (SDK) .net Core 3,0](https://dotnet.microsoft.com/download) ou une version plus récente.</span><span class="sxs-lookup"><span data-stu-id="f78f8-110">Install [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="f78f8-111">Créer la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="f78f8-111">Create the library</span></span>

<span data-ttu-id="f78f8-112">La première étape consiste à créer la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="f78f8-112">The first step is to create the library.</span></span>

1. <span data-ttu-id="f78f8-113">Créez un nouveau dossier et, dans ce dossier, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="f78f8-113">Create a new folder, and in that folder run the following command:</span></span>
    
    ```dotnetcli
    dotnet new classlib
    ```

2. <span data-ttu-id="f78f8-114">Ouvrez `Class1.cs`.</span><span class="sxs-lookup"><span data-stu-id="f78f8-114">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="f78f8-115">Ajoutez `using System.Runtime.InteropServices;` en haut du fichier.</span><span class="sxs-lookup"><span data-stu-id="f78f8-115">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="f78f8-116">Créez une interface nommée `IServer`.</span><span class="sxs-lookup"><span data-stu-id="f78f8-116">Create an interface named `IServer`.</span></span> <span data-ttu-id="f78f8-117">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="f78f8-117">For example:</span></span>

   [!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]

5. <span data-ttu-id="f78f8-118">Ajoutez l’attribut `[Guid("<IID>")]` à l’interface, avec le GUID d’interface pour l’interface COM que vous implémentez.</span><span class="sxs-lookup"><span data-stu-id="f78f8-118">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="f78f8-119">Par exemple, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span><span class="sxs-lookup"><span data-stu-id="f78f8-119">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="f78f8-120">Notez que ce GUID doit être unique, car il s’agit du seul identificateur de cette interface pour COM.</span><span class="sxs-lookup"><span data-stu-id="f78f8-120">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="f78f8-121">Dans Visual Studio, vous pouvez générer un GUID en accédant à Outils > Créer un GUID pour ouvrir l’outil Créer un GUID.</span><span class="sxs-lookup"><span data-stu-id="f78f8-121">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="f78f8-122">Ajoutez l’attribut `[InterfaceType]` à l’interface et spécifiez les interfaces COM de base que votre interface doit implémenter.</span><span class="sxs-lookup"><span data-stu-id="f78f8-122">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="f78f8-123">Créez une classe nommée `Server` qui implémente `IServer`.</span><span class="sxs-lookup"><span data-stu-id="f78f8-123">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="f78f8-124">Ajoutez l’attribut `[Guid("<CLSID>")]` à la classe, avec le GUID de l’identificateur de classe pour la classe COM que vous implémentez.</span><span class="sxs-lookup"><span data-stu-id="f78f8-124">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="f78f8-125">Par exemple, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span><span class="sxs-lookup"><span data-stu-id="f78f8-125">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="f78f8-126">Comme avec le GUID d’interface, ce GUID doit être unique, car il est le seul identificateur de cette interface pour COM.</span><span class="sxs-lookup"><span data-stu-id="f78f8-126">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="f78f8-127">Ajoutez l’attribut `[ComVisible(true)]` à la fois à l’interface et à la classe.</span><span class="sxs-lookup"><span data-stu-id="f78f8-127">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f78f8-128">Contrairement au .NET Framework, .NET Core vous oblige à spécifier le CLSID des classes que vous voulez rendre activables via COM.</span><span class="sxs-lookup"><span data-stu-id="f78f8-128">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="f78f8-129">Générer l’hôte COM</span><span class="sxs-lookup"><span data-stu-id="f78f8-129">Generate the COM host</span></span>

1. <span data-ttu-id="f78f8-130">Ouvrez le fichier projet `.csproj` et ajoutez `<EnableComHosting>true</EnableComHosting>` à l’intérieur d’une balise `<PropertyGroup></PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="f78f8-130">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="f78f8-131">Générez le projet.</span><span class="sxs-lookup"><span data-stu-id="f78f8-131">Build the project.</span></span>

<span data-ttu-id="f78f8-132">La sortie résultante a un fichier `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` et `ProjectName.comhost.dll`.</span><span class="sxs-lookup"><span data-stu-id="f78f8-132">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="f78f8-133">Inscrire l’hôte COM pour COM</span><span class="sxs-lookup"><span data-stu-id="f78f8-133">Register the COM host for COM</span></span>

<span data-ttu-id="f78f8-134">Ouvrez une invite de commandes avec élévation de privilèges et exécutez `regsvr32 ProjectName.comhost.dll`.</span><span class="sxs-lookup"><span data-stu-id="f78f8-134">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="f78f8-135">Ceci inscrit tous vos objets .NET exposés auprès de COM.</span><span class="sxs-lookup"><span data-stu-id="f78f8-135">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="f78f8-136">Activation de COM sans registre</span><span class="sxs-lookup"><span data-stu-id="f78f8-136">Enabling RegFree COM</span></span>

1. <span data-ttu-id="f78f8-137">Ouvrez le fichier projet `.csproj` et ajoutez `<EnableRegFreeCom>true</EnableRegFreeCom>` à l’intérieur d’une balise `<PropertyGroup></PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="f78f8-137">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="f78f8-138">Générez le projet.</span><span class="sxs-lookup"><span data-stu-id="f78f8-138">Build the project.</span></span>

<span data-ttu-id="f78f8-139">La sortie résultante a un fichier `ProjectName.X.manifest`.</span><span class="sxs-lookup"><span data-stu-id="f78f8-139">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="f78f8-140">Ce fichier est le manifeste côte à côte à utiliser avec COM sans registre.</span><span class="sxs-lookup"><span data-stu-id="f78f8-140">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="f78f8-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="f78f8-141">Sample</span></span>

<span data-ttu-id="f78f8-142">Un [exemple de serveur COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) entièrement fonctionnel se trouve dans le dépôt dotnet/samples sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="f78f8-142">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="f78f8-143">Remarques supplémentaires</span><span class="sxs-lookup"><span data-stu-id="f78f8-143">Additional notes</span></span>

<span data-ttu-id="f78f8-144">Contrairement au .NET Framework, .NET Core ne prend pas en charge la génération d’une bibliothèque de types COM à partir d’un assembly .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f78f8-144">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="f78f8-145">Vous devez écrire manuellement un fichier IDL ou un en-tête C++ pour les déclarations natives de vos interfaces.</span><span class="sxs-lookup"><span data-stu-id="f78f8-145">You will either have to manually write an IDL file or a C++ header for the native declarations of your interfaces.</span></span>

<span data-ttu-id="f78f8-146">En outre, le chargement du .NET Framework et de .NET Core dans le même processus n’est pas pris en charge : par conséquent, le chargement d’un serveur COM .NET Core dans un processus client COM .NET Framework ou vice versa n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f78f8-146">Additionally, loading both .NET Framework and .NET Core into the same process is unsupported, and as a result loading a .NET Core COM server into a .NET Framework COM client process or vice versa is not supported.</span></span>
