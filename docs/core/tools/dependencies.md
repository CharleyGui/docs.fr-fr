---
title: Gérer les dépendances dans .NET Core
description: Explique comment gérer les dépendances du projet pour une application .NET Core.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: 367be7eb04d58bffc0846de1d035a5801e8d9376
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399146"
---
# <a name="manage-dependencies-in-net-core-applications"></a><span data-ttu-id="d6651-103">Gérer les dépendances dans les applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="d6651-103">Manage dependencies in .NET Core applications</span></span>

<span data-ttu-id="d6651-104">Cet article explique comment ajouter et supprimer les dépendances en éditant le fichier de projet ou en utilisant l’IRTC.</span><span class="sxs-lookup"><span data-stu-id="d6651-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="d6651-105">L’élément \<de> de la conclusion de paquet</span><span class="sxs-lookup"><span data-stu-id="d6651-105">The \<PackageReference> element</span></span>

<span data-ttu-id="d6651-106">L’élément `<PackageReference>` de dossier de projet a la structure suivante :</span><span class="sxs-lookup"><span data-stu-id="d6651-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="d6651-107">L’attribut `Include` spécifie l’ID de l’ensemble à ajouter au projet.</span><span class="sxs-lookup"><span data-stu-id="d6651-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="d6651-108">L’attribut `Version` spécifie la version à obtenir.</span><span class="sxs-lookup"><span data-stu-id="d6651-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="d6651-109">Les versions sont spécifiées selon [les règles de la version NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="d6651-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="d6651-110">Si vous n’êtes pas familier avec la syntaxe de fichier de projet, consultez la documentation de référence du [projet MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="d6651-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="d6651-111">Utilisez les conditions pour ajouter une dépendance qui n’est disponible que dans une cible spécifique, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d6651-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="d6651-112">La dépendance dans l’exemple précédent ne sera valable que si la construction se produit pour cette cible donnée.</span><span class="sxs-lookup"><span data-stu-id="d6651-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="d6651-113">Le `$(TargetFramework)` dans l’état est une propriété MSBuild qui est mis dans le projet.</span><span class="sxs-lookup"><span data-stu-id="d6651-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="d6651-114">Pour la plupart des applications .NET Core courantes, vous n’avez pas besoin de le faire.</span><span class="sxs-lookup"><span data-stu-id="d6651-114">For most common .NET Core applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="d6651-115">Ajouter une dépendance en éditant le fichier du projet</span><span class="sxs-lookup"><span data-stu-id="d6651-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="d6651-116">Pour ajouter une dépendance, ajoutez un `<PackageReference>` élément à l’intérieur d’un `<ItemGroup>` élément.</span><span class="sxs-lookup"><span data-stu-id="d6651-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="d6651-117">Vous pouvez ajouter `<ItemGroup>` à un existant ou en créer un nouveau.</span><span class="sxs-lookup"><span data-stu-id="d6651-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="d6651-118">L’exemple suivant utilise le projet d’application de console par défaut qui est créé par `dotnet new console`:</span><span class="sxs-lookup"><span data-stu-id="d6651-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

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

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="d6651-119">Ajouter une dépendance en utilisant le CLI</span><span class="sxs-lookup"><span data-stu-id="d6651-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="d6651-120">Pour ajouter une dépendance, exécutez la [dotnet add package](dotnet-add-package.md) commande, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d6651-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="d6651-121">Supprimer une dépendance en modifiant le fichier du projet</span><span class="sxs-lookup"><span data-stu-id="d6651-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="d6651-122">Pour supprimer une dépendance, retirez son `<PackageReference>` élément du fichier de projet.</span><span class="sxs-lookup"><span data-stu-id="d6651-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="d6651-123">Supprimer une dépendance en utilisant l’IMC</span><span class="sxs-lookup"><span data-stu-id="d6651-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="d6651-124">Pour éliminer une dépendance, exécutez la [dotnet remove package](dotnet-remove-package.md) commande, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d6651-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="d6651-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6651-125">See also</span></span>

* [<span data-ttu-id="d6651-126">Paquets NuGet dans les fichiers du projet</span><span class="sxs-lookup"><span data-stu-id="d6651-126">NuGet packages in project files</span></span>](../project-sdk/msbuild-props.md#nuget-packages)
* <span data-ttu-id="d6651-127">[dotnet list packageCommande](dotnet-remove-package.md)</span><span class="sxs-lookup"><span data-stu-id="d6651-127">[dotnet list package command](dotnet-remove-package.md)</span></span>
