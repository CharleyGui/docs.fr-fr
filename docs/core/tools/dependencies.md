---
title: Gérer les dépendances dans .NET
description: Explique comment gérer les dépendances de projet pour une application .NET.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.topic: how-to
ms.date: 01/28/2021
ms.openlocfilehash: 9f5f814d0b4dc7aa3ff1a938c172475169a55bf2
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216126"
---
# <a name="manage-dependencies-in-net-applications"></a><span data-ttu-id="e0837-103">Gérer les dépendances dans les applications .NET</span><span class="sxs-lookup"><span data-stu-id="e0837-103">Manage dependencies in .NET applications</span></span>

<span data-ttu-id="e0837-104">Cet article explique comment ajouter et supprimer des dépendances en modifiant le fichier projet ou à l’aide de l’interface CLI.</span><span class="sxs-lookup"><span data-stu-id="e0837-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="e0837-105">Élément \<PackageReference></span><span class="sxs-lookup"><span data-stu-id="e0837-105">The \<PackageReference> element</span></span>

<span data-ttu-id="e0837-106">L' `<PackageReference>` élément du fichier projet a la structure suivante :</span><span class="sxs-lookup"><span data-stu-id="e0837-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="e0837-107">L' `Include` attribut spécifie l’ID du package à ajouter au projet.</span><span class="sxs-lookup"><span data-stu-id="e0837-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="e0837-108">L' `Version` attribut spécifie la version à récupérer.</span><span class="sxs-lookup"><span data-stu-id="e0837-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="e0837-109">Les versions sont spécifiées en fonction des [règles de version de NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="e0837-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="e0837-110">Si vous n’êtes pas familiarisé avec la syntaxe des fichiers projet, consultez la documentation de référence sur les [projets MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="e0837-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="e0837-111">Utilisez des conditions pour ajouter une dépendance qui est disponible uniquement dans une cible spécifique, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e0837-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="e0837-112">La dépendance dans l’exemple précédent sera valide uniquement si la génération se produit pour cette cible donnée.</span><span class="sxs-lookup"><span data-stu-id="e0837-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="e0837-113">`$(TargetFramework)`Dans la condition, il s’agit d’une propriété MSBuild qui est définie dans le projet.</span><span class="sxs-lookup"><span data-stu-id="e0837-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="e0837-114">Pour la plupart des applications .NET courantes, vous n’avez pas besoin de le faire.</span><span class="sxs-lookup"><span data-stu-id="e0837-114">For most common .NET applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="e0837-115">Ajouter une dépendance en modifiant le fichier projet</span><span class="sxs-lookup"><span data-stu-id="e0837-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="e0837-116">Pour ajouter une dépendance, ajoutez un `<PackageReference>` élément à l’intérieur d’un `<ItemGroup>` élément.</span><span class="sxs-lookup"><span data-stu-id="e0837-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="e0837-117">Vous pouvez ajouter à un existant `<ItemGroup>` ou en créer un nouveau.</span><span class="sxs-lookup"><span data-stu-id="e0837-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="e0837-118">L’exemple suivant utilise le projet d’application console par défaut qui est créé par `dotnet new console` :</span><span class="sxs-lookup"><span data-stu-id="e0837-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore" Version="3.1.2" />
  </ItemGroup>

</Project>
```

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="e0837-119">Ajouter une dépendance à l’aide de l’interface CLI</span><span class="sxs-lookup"><span data-stu-id="e0837-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="e0837-120">Pour ajouter une dépendance, exécutez la [dotnet add package](dotnet-add-package.md) commande, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e0837-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="e0837-121">Supprimer une dépendance en modifiant le fichier projet</span><span class="sxs-lookup"><span data-stu-id="e0837-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="e0837-122">Pour supprimer une dépendance, supprimez son `<PackageReference>` élément du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="e0837-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="e0837-123">Supprimer une dépendance à l’aide de l’interface CLI</span><span class="sxs-lookup"><span data-stu-id="e0837-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="e0837-124">Pour supprimer une dépendance, exécutez la [dotnet remove package](dotnet-remove-package.md) commande, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e0837-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="e0837-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0837-125">See also</span></span>

* [<span data-ttu-id="e0837-126">Références de package dans les fichiers projet</span><span class="sxs-lookup"><span data-stu-id="e0837-126">Package references in project files</span></span>](../project-sdk/msbuild-props.md#reference-properties-and-items)
* [<span data-ttu-id="e0837-127">dotnet list package commande</span><span class="sxs-lookup"><span data-stu-id="e0837-127">dotnet list package command</span></span>](dotnet-list-package.md)
