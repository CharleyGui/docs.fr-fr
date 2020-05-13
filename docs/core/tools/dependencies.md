---
title: Gérer les dépendances dans .NET Core
description: Explique comment gérer les dépendances de projet pour une application .NET Core.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: b77acc7d4f03a45784f753d3daaa9810f110a6ac
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205953"
---
# <a name="manage-dependencies-in-net-core-applications"></a><span data-ttu-id="2e9ad-103">Gérer les dépendances dans les applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="2e9ad-103">Manage dependencies in .NET Core applications</span></span>

<span data-ttu-id="2e9ad-104">Cet article explique comment ajouter et supprimer des dépendances en modifiant le fichier projet ou à l’aide de l’interface CLI.</span><span class="sxs-lookup"><span data-stu-id="2e9ad-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="2e9ad-105">\<Élément PackageReference></span><span class="sxs-lookup"><span data-stu-id="2e9ad-105">The \<PackageReference> element</span></span>

<span data-ttu-id="2e9ad-106">L' `<PackageReference>` élément du fichier projet a la structure suivante :</span><span class="sxs-lookup"><span data-stu-id="2e9ad-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="2e9ad-107">L' `Include` attribut spécifie l’ID du package à ajouter au projet.</span><span class="sxs-lookup"><span data-stu-id="2e9ad-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="2e9ad-108">L' `Version` attribut spécifie la version à récupérer.</span><span class="sxs-lookup"><span data-stu-id="2e9ad-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="2e9ad-109">Les versions sont spécifiées en fonction des [règles de version de NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="2e9ad-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="2e9ad-110">Si vous n’êtes pas familiarisé avec la syntaxe des fichiers projet, consultez la documentation de référence sur les [projets MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="2e9ad-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="2e9ad-111">Utilisez des conditions pour ajouter une dépendance qui est disponible uniquement dans une cible spécifique, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="2e9ad-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="2e9ad-112">La dépendance dans l’exemple précédent sera valide uniquement si la génération se produit pour cette cible donnée.</span><span class="sxs-lookup"><span data-stu-id="2e9ad-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="2e9ad-113">`$(TargetFramework)`Dans la condition, il s’agit d’une propriété MSBuild qui est définie dans le projet.</span><span class="sxs-lookup"><span data-stu-id="2e9ad-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="2e9ad-114">Pour la plupart des applications .NET Core courantes, vous n’avez pas besoin de le faire.</span><span class="sxs-lookup"><span data-stu-id="2e9ad-114">For most common .NET Core applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="2e9ad-115">Ajouter une dépendance en modifiant le fichier projet</span><span class="sxs-lookup"><span data-stu-id="2e9ad-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="2e9ad-116">Pour ajouter une dépendance, ajoutez un `<PackageReference>` élément à l’intérieur d’un `<ItemGroup>` élément.</span><span class="sxs-lookup"><span data-stu-id="2e9ad-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="2e9ad-117">Vous pouvez ajouter à un existant `<ItemGroup>` ou en créer un nouveau.</span><span class="sxs-lookup"><span data-stu-id="2e9ad-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="2e9ad-118">L’exemple suivant utilise le projet d’application console par défaut qui est créé par `dotnet new console` :</span><span class="sxs-lookup"><span data-stu-id="2e9ad-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

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

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="2e9ad-119">Ajouter une dépendance à l’aide de l’interface CLI</span><span class="sxs-lookup"><span data-stu-id="2e9ad-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="2e9ad-120">Pour ajouter une dépendance, exécutez la [dotnet add package](dotnet-add-package.md) commande, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="2e9ad-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="2e9ad-121">Supprimer une dépendance en modifiant le fichier projet</span><span class="sxs-lookup"><span data-stu-id="2e9ad-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="2e9ad-122">Pour supprimer une dépendance, supprimez son `<PackageReference>` élément du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="2e9ad-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="2e9ad-123">Supprimer une dépendance à l’aide de l’interface CLI</span><span class="sxs-lookup"><span data-stu-id="2e9ad-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="2e9ad-124">Pour supprimer une dépendance, exécutez la [dotnet remove package](dotnet-remove-package.md) commande, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="2e9ad-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="2e9ad-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e9ad-125">See also</span></span>

* [<span data-ttu-id="2e9ad-126">Références de package dans les fichiers projet</span><span class="sxs-lookup"><span data-stu-id="2e9ad-126">Package references in project files</span></span>](../project-sdk/msbuild-props.md#reference-properties-and-items)
* <span data-ttu-id="2e9ad-127">[dotnet list packagecommande](dotnet-remove-package.md)</span><span class="sxs-lookup"><span data-stu-id="2e9ad-127">[dotnet list package command](dotnet-remove-package.md)</span></span>
