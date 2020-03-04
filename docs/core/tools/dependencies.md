---
title: Gérer les dépendances dans .NET Core
description: Explique comment gérer les dépendances de projet pour une application .NET Core.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: 367be7eb04d58bffc0846de1d035a5801e8d9376
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157243"
---
# <a name="manage-dependencies-in-net-core-applications"></a><span data-ttu-id="3fd8b-103">Gérer les dépendances dans les applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="3fd8b-103">Manage dependencies in .NET Core applications</span></span>

<span data-ttu-id="3fd8b-104">Cet article explique comment ajouter et supprimer des dépendances en modifiant le fichier projet ou à l’aide de l’interface CLI.</span><span class="sxs-lookup"><span data-stu-id="3fd8b-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="3fd8b-105">Élément \<PackageReference ></span><span class="sxs-lookup"><span data-stu-id="3fd8b-105">The \<PackageReference> element</span></span>

<span data-ttu-id="3fd8b-106">L’élément du fichier de projet `<PackageReference>` a la structure suivante :</span><span class="sxs-lookup"><span data-stu-id="3fd8b-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="3fd8b-107">L’attribut `Include` spécifie l’ID du package à ajouter au projet.</span><span class="sxs-lookup"><span data-stu-id="3fd8b-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="3fd8b-108">L’attribut `Version` spécifie la version à récupérer.</span><span class="sxs-lookup"><span data-stu-id="3fd8b-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="3fd8b-109">Les versions sont spécifiées en fonction des [règles de version de NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="3fd8b-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="3fd8b-110">Si vous n’êtes pas familiarisé avec la syntaxe des fichiers projet, consultez la documentation de référence sur les [projets MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="3fd8b-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="3fd8b-111">Utilisez des conditions pour ajouter une dépendance qui est disponible uniquement dans une cible spécifique, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3fd8b-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="3fd8b-112">La dépendance dans l’exemple précédent sera valide uniquement si la génération se produit pour cette cible donnée.</span><span class="sxs-lookup"><span data-stu-id="3fd8b-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="3fd8b-113">La `$(TargetFramework)` dans la condition est une propriété MSBuild qui est définie dans le projet.</span><span class="sxs-lookup"><span data-stu-id="3fd8b-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="3fd8b-114">Pour la plupart des applications .NET Core courantes, vous n’avez pas besoin de le faire.</span><span class="sxs-lookup"><span data-stu-id="3fd8b-114">For most common .NET Core applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="3fd8b-115">Ajouter une dépendance en modifiant le fichier projet</span><span class="sxs-lookup"><span data-stu-id="3fd8b-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="3fd8b-116">Pour ajouter une dépendance, ajoutez un élément `<PackageReference>` à l’intérieur d’un élément `<ItemGroup>`.</span><span class="sxs-lookup"><span data-stu-id="3fd8b-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="3fd8b-117">Vous pouvez ajouter à un `<ItemGroup>` existant ou en créer un nouveau.</span><span class="sxs-lookup"><span data-stu-id="3fd8b-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="3fd8b-118">L’exemple suivant utilise le projet d’application console par défaut qui est créé par `dotnet new console`:</span><span class="sxs-lookup"><span data-stu-id="3fd8b-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

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

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="3fd8b-119">Ajouter une dépendance à l’aide de l’interface CLI</span><span class="sxs-lookup"><span data-stu-id="3fd8b-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="3fd8b-120">Pour ajouter une dépendance, exécutez la commande [dotnet add package](dotnet-add-package.md) , comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3fd8b-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="3fd8b-121">Supprimer une dépendance en modifiant le fichier projet</span><span class="sxs-lookup"><span data-stu-id="3fd8b-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="3fd8b-122">Pour supprimer une dépendance, supprimez son élément `<PackageReference>` du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="3fd8b-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="3fd8b-123">Supprimer une dépendance à l’aide de l’interface CLI</span><span class="sxs-lookup"><span data-stu-id="3fd8b-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="3fd8b-124">Pour supprimer une dépendance, exécutez la commande [dotnet remove package](dotnet-remove-package.md) , comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3fd8b-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="3fd8b-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fd8b-125">See also</span></span>

* [<span data-ttu-id="3fd8b-126">Packages NuGet dans les fichiers projet</span><span class="sxs-lookup"><span data-stu-id="3fd8b-126">NuGet packages in project files</span></span>](../project-sdk/msbuild-props.md#nuget-packages)
* <span data-ttu-id="3fd8b-127">[commande dotnet list package](dotnet-remove-package.md)</span><span class="sxs-lookup"><span data-stu-id="3fd8b-127">[dotnet list package command](dotnet-remove-package.md)</span></span>
