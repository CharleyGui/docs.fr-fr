---
title: ''
description: ''
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: ''
ms.openlocfilehash: 667b2d4d68edd82a4d18c370e45ea18f4d4b379a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702839"
---
# <a name="manage-dependencies-in-net-core-applications"></a><span data-ttu-id="102dc-101">Gérer les dépendances dans les applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="102dc-101">Manage dependencies in .NET Core applications</span></span>

<span data-ttu-id="102dc-102">Cet article explique comment ajouter et supprimer des dépendances en modifiant le fichier projet ou à l’aide de l’interface CLI.</span><span class="sxs-lookup"><span data-stu-id="102dc-102">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="102dc-103">\<Élément PackageReference></span><span class="sxs-lookup"><span data-stu-id="102dc-103">The \<PackageReference> element</span></span>

<span data-ttu-id="102dc-104">L' `<PackageReference>` élément du fichier projet a la structure suivante :</span><span class="sxs-lookup"><span data-stu-id="102dc-104">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="102dc-105">L' `Include` attribut spécifie l’ID du package à ajouter au projet.</span><span class="sxs-lookup"><span data-stu-id="102dc-105">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="102dc-106">L' `Version` attribut spécifie la version à récupérer.</span><span class="sxs-lookup"><span data-stu-id="102dc-106">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="102dc-107">Les versions sont spécifiées en fonction des [règles de version de NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="102dc-107">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="102dc-108">Si vous n’êtes pas familiarisé avec la syntaxe des fichiers projet, consultez la documentation de référence sur les [projets MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="102dc-108">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="102dc-109">Utilisez des conditions pour ajouter une dépendance qui est disponible uniquement dans une cible spécifique, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="102dc-109">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="102dc-110">La dépendance dans l’exemple précédent sera valide uniquement si la génération se produit pour cette cible donnée.</span><span class="sxs-lookup"><span data-stu-id="102dc-110">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="102dc-111">`$(TargetFramework)`Dans la condition, il s’agit d’une propriété MSBuild qui est définie dans le projet.</span><span class="sxs-lookup"><span data-stu-id="102dc-111">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="102dc-112">Pour la plupart des applications .NET Core courantes, vous n’avez pas besoin de le faire.</span><span class="sxs-lookup"><span data-stu-id="102dc-112">For most common .NET Core applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="102dc-113">Ajouter une dépendance en modifiant le fichier projet</span><span class="sxs-lookup"><span data-stu-id="102dc-113">Add a dependency by editing the project file</span></span>

<span data-ttu-id="102dc-114">Pour ajouter une dépendance, ajoutez un `<PackageReference>` élément à l’intérieur d’un `<ItemGroup>` élément.</span><span class="sxs-lookup"><span data-stu-id="102dc-114">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="102dc-115">Vous pouvez ajouter à un existant `<ItemGroup>` ou en créer un nouveau.</span><span class="sxs-lookup"><span data-stu-id="102dc-115">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="102dc-116">L’exemple suivant utilise le projet d’application console par défaut qui est créé par `dotnet new console` :</span><span class="sxs-lookup"><span data-stu-id="102dc-116">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

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

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="102dc-117">Ajouter une dépendance à l’aide de l’interface CLI</span><span class="sxs-lookup"><span data-stu-id="102dc-117">Add a dependency by using the CLI</span></span>

<span data-ttu-id="102dc-118">Pour ajouter une dépendance, exécutez la [dotnet add package](dotnet-add-package.md) commande, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="102dc-118">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="102dc-119">Supprimer une dépendance en modifiant le fichier projet</span><span class="sxs-lookup"><span data-stu-id="102dc-119">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="102dc-120">Pour supprimer une dépendance, supprimez son `<PackageReference>` élément du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="102dc-120">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="102dc-121">Supprimer une dépendance à l’aide de l’interface CLI</span><span class="sxs-lookup"><span data-stu-id="102dc-121">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="102dc-122">Pour supprimer une dépendance, exécutez la [dotnet remove package](dotnet-remove-package.md) commande, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="102dc-122">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="102dc-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="102dc-123">See also</span></span>

* [<span data-ttu-id="102dc-124">Références de package dans les fichiers projet</span><span class="sxs-lookup"><span data-stu-id="102dc-124">Package references in project files</span></span>](../project-sdk/msbuild-props.md#reference-properties-and-items)
* <span data-ttu-id="102dc-125">[dotnet list packagecommande](dotnet-list-package.md)</span><span class="sxs-lookup"><span data-stu-id="102dc-125">[dotnet list package command](dotnet-list-package.md)</span></span>
