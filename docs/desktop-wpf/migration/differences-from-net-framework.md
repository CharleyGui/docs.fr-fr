---
title: Différences entre .NET Framework et .NET Core
description: Décrit les différences entre la mise en œuvre du cadre .NET de Windows Presentation Foundation (WPF) et .NET Core WPF. Lorsque vous migrez votre application, vous devez tenir compte de ces incompatibilités.
author: thraka
ms.date: 09/21/2019
ms.author: adegeo
ms.openlocfilehash: 341e576f17c522fbcbb9c417176e9d4a13ab1b18
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82072206"
---
# <a name="differences-in-wpf"></a><span data-ttu-id="b2901-104">Différences dans WPF</span><span class="sxs-lookup"><span data-stu-id="b2901-104">Differences in WPF</span></span>

<span data-ttu-id="b2901-105">Cet article décrit les différences entre Windows Presentation Foundation (WPF) sur .NET Core et .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b2901-105">This article describes the differences between Windows Presentation Foundation (WPF) on .NET Core and .NET Framework.</span></span> <span data-ttu-id="b2901-106">WPF pour .NET Core est un [cadre open-source](https://github.com/dotnet/wpf) fourche à partir du WPF original pour le code source cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="b2901-106">WPF for .NET Core is an [open-source framework](https://github.com/dotnet/wpf) forked from the original WPF for .NET Framework source code.</span></span>

<span data-ttu-id="b2901-107">Il ya quelques caractéristiques de .NET Framework que .NET Core ne prend pas en charge.</span><span class="sxs-lookup"><span data-stu-id="b2901-107">There are a few features of .NET Framework that .NET Core doesn't support.</span></span> <span data-ttu-id="b2901-108">Pour plus d’informations sur les technologies non-supportées, voir [.NET Technologies du Cadre indisponibles sur .NET Core](../../core/porting/net-framework-tech-unavailable.md).</span><span class="sxs-lookup"><span data-stu-id="b2901-108">For more information on unsupported technologies, see [.NET Framework technologies unavailable on .NET Core](../../core/porting/net-framework-tech-unavailable.md).</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a><span data-ttu-id="b2901-109">Projets de style SDK</span><span class="sxs-lookup"><span data-stu-id="b2901-109">SDK-style projects</span></span>

<span data-ttu-id="b2901-110">.NET Core utilise des fichiers de projets de style SDK.</span><span class="sxs-lookup"><span data-stu-id="b2901-110">.NET Core uses SDK-style project files.</span></span> <span data-ttu-id="b2901-111">Ces fichiers de projet sont différents des fichiers traditionnels du projet cadre .NET gérés par Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b2901-111">These project files are different from the traditional .NET Framework project files managed by Visual Studio.</span></span> <span data-ttu-id="b2901-112">Pour migrer vos applications .NET Framework WPF vers .NET Core, vous devez convertir vos projets.</span><span class="sxs-lookup"><span data-stu-id="b2901-112">To migrate your .NET Framework WPF apps to .NET Core, you must convert your projects.</span></span> <span data-ttu-id="b2901-113">Pour plus d’informations, voir [les applications Migrate WPF à .NET Core 3.0](convert-project-from-net-framework.md).</span><span class="sxs-lookup"><span data-stu-id="b2901-113">For more information, see [Migrate WPF apps to .NET Core 3.0](convert-project-from-net-framework.md).</span></span>

## <a name="nuget-package-references"></a><span data-ttu-id="b2901-114">Références du package NuGet</span><span class="sxs-lookup"><span data-stu-id="b2901-114">NuGet package references</span></span>

<span data-ttu-id="b2901-115">Si votre application .NET Framework répertorie ses dépendances NuGet [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) dans un fichier *packages.config,* migrez vers le format :</span><span class="sxs-lookup"><span data-stu-id="b2901-115">If your .NET Framework app lists its NuGet dependencies in a *packages.config* file, migrate to the [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) format:</span></span>

1. <span data-ttu-id="b2901-116">Dans Visual Studio, ouvrez la vitre **Solution Explorer.**</span><span class="sxs-lookup"><span data-stu-id="b2901-116">In Visual Studio, open the **Solution Explorer** pane.</span></span>
1. <span data-ttu-id="b2901-117">Dans votre projet WPF, right-click **packages.config** > **Migrate packages.config à PackageReference**.</span><span class="sxs-lookup"><span data-stu-id="b2901-117">In your WPF project, right-click **packages.config** > **Migrate packages.config to PackageReference**.</span></span>

![Mise à niveau vers PackageReference](media/differences-from-net-framework/package-reference-migration.png)

<span data-ttu-id="b2901-119">Un dialogue apparaîtra montrant les dépendances NuGet calculées de haut niveau et demandant quels autres paquets NuGet devraient être promus au plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="b2901-119">A dialog will appear showing calculated top-level NuGet dependencies and asking which other NuGet packages should be promoted to top level.</span></span> <span data-ttu-id="b2901-120">Sélectionnez **OK** et le fichier *packages.config* sera `<PackageReference>` supprimé du projet et des éléments seront ajoutés au fichier du projet.</span><span class="sxs-lookup"><span data-stu-id="b2901-120">Select **OK** and the *packages.config* file will be removed from the project and `<PackageReference>` elements will be added to the project file.</span></span>

<span data-ttu-id="b2901-121">Lorsque votre `<PackageReference>`projet utilise, les paquets ne sont pas stockés localement dans un dossier *Paquets,* ils sont stockés dans le monde entier.</span><span class="sxs-lookup"><span data-stu-id="b2901-121">When your project uses `<PackageReference>`, packages aren't stored locally in a *Packages* folder, they're stored globally.</span></span> <span data-ttu-id="b2901-122">Ouvrez le fichier `<Analyzer>` de projet et supprimez tous les éléments qui se référaient au dossier *Paquets.*</span><span class="sxs-lookup"><span data-stu-id="b2901-122">Open the project file and remove any `<Analyzer>` elements that referred to the *Packages* folder.</span></span> <span data-ttu-id="b2901-123">Ces analyseurs sont automatiquement inclus dans les références du paquet NuGet.</span><span class="sxs-lookup"><span data-stu-id="b2901-123">These analyzers are automatically included with the NuGet package references.</span></span>

## <a name="code-access-security"></a><span data-ttu-id="b2901-124">Sécurité d'accès du code</span><span class="sxs-lookup"><span data-stu-id="b2901-124">Code Access Security</span></span>

<span data-ttu-id="b2901-125">Code Access Security (CAS) n’est pas pris en charge par .NET Core ou WPF pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b2901-125">Code Access Security (CAS) is not supported by .NET Core or WPF for .NET Core.</span></span> <span data-ttu-id="b2901-126">Toutes les fonctionnalités liées à la SAE sont traitées en supposant une pleine confiance.</span><span class="sxs-lookup"><span data-stu-id="b2901-126">All CAS-related functionality is treated under the assumption of full-trust.</span></span> <span data-ttu-id="b2901-127">WPF pour .NET Core supprime le code lié à la SAE.</span><span class="sxs-lookup"><span data-stu-id="b2901-127">WPF for .NET Core removes CAS-related code.</span></span> <span data-ttu-id="b2901-128">La surface publique de l’API de ces types existe toujours pour s’assurer que les appels dans ces types réussissent.</span><span class="sxs-lookup"><span data-stu-id="b2901-128">The public API surface of these types still exists to ensure that calls into these types succeed.</span></span>

<span data-ttu-id="b2901-129">Les types de CAS définis publiquement ont été déplacés hors des assemblées du WPF pour se rendre aux assemblées de la bibliothèque Core .NET.</span><span class="sxs-lookup"><span data-stu-id="b2901-129">Publicly defined CAS-related types were moved out of the WPF assemblies and into the Core .NET library assemblies.</span></span> <span data-ttu-id="b2901-130">Les assemblages WPF ont le type-forwarding réglé à la nouvelle position des types déplacés.</span><span class="sxs-lookup"><span data-stu-id="b2901-130">The WPF assemblies have type-forwarding set to the new location of the moved types.</span></span>

| <span data-ttu-id="b2901-131">Assemblage de source</span><span class="sxs-lookup"><span data-stu-id="b2901-131">Source assembly</span></span> | <span data-ttu-id="b2901-132">Assemblage cible</span><span class="sxs-lookup"><span data-stu-id="b2901-132">Target assembly</span></span> | <span data-ttu-id="b2901-133">Type</span><span class="sxs-lookup"><span data-stu-id="b2901-133">Type</span></span>                |
| --------------- | --------------- | ------------------- |
| <span data-ttu-id="b2901-134">*WindowsBase.dll*</span><span class="sxs-lookup"><span data-stu-id="b2901-134">*WindowsBase.dll*</span></span> | <span data-ttu-id="b2901-135">*System.security.Permissions.dll*</span><span class="sxs-lookup"><span data-stu-id="b2901-135">*System.Security.Permissions.dll*</span></span> | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| <span data-ttu-id="b2901-136">*System.Xaml.dll*</span><span class="sxs-lookup"><span data-stu-id="b2901-136">*System.Xaml.dll*</span></span> | <span data-ttu-id="b2901-137">*System.security.Permissions.dll*</span><span class="sxs-lookup"><span data-stu-id="b2901-137">*System.Security.Permissions.dll*</span></span> | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| <span data-ttu-id="b2901-138">*System.Xaml.dll*</span><span class="sxs-lookup"><span data-stu-id="b2901-138">*System.Xaml.dll*</span></span> | <span data-ttu-id="b2901-139">*System.Windows.Extension.dll*</span><span class="sxs-lookup"><span data-stu-id="b2901-139">*System.Windows.Extension.dll*</span></span>    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> <span data-ttu-id="b2901-140">Afin de minimiser le frottement du portage, la fonctionnalité de stockage et `XamlAccessLevel` de récupération des informations relatives aux propriétés suivantes a été conservée dans le type.</span><span class="sxs-lookup"><span data-stu-id="b2901-140">In order to minimize porting friction, the functionality for storing and retrieving information related to the following properties was retained in the `XamlAccessLevel` type.</span></span>
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a><span data-ttu-id="b2901-141">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="b2901-141">Next steps</span></span>

- [<span data-ttu-id="b2901-142">Apprenez à porter une application .NET Framework WPF à .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b2901-142">Learn how to port a .NET Framework WPF app to .NET Core.</span></span>](convert-project-from-net-framework.md)
