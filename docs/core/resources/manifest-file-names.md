---
title: Comment MSBuild génère des noms de fichiers manifestes
description: Décrit les facteurs qui influencent le nom d’un fichier manifeste de ressources généré par MSBuild au moment de la compilation.
ms.date: 05/08/2020
ms.topic: conceptual
ms.openlocfilehash: 383bf6a077b0631e70ddaa4721b20e992127a73c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83232325"
---
# <a name="how-resource-manifest-files-are-named"></a><span data-ttu-id="c978d-103">Nom des fichiers manifestes de ressources</span><span class="sxs-lookup"><span data-stu-id="c978d-103">How resource manifest files are named</span></span>

<span data-ttu-id="c978d-104">Lorsque MSBuild compile un projet .NET Core, les fichiers de ressources XML, qui ont l’extension de fichier *. resx* , sont convertis en fichiers *. Resources* binaires.</span><span class="sxs-lookup"><span data-stu-id="c978d-104">When MSBuild compiles a .NET Core project, XML resource files, which have the *.resx* file extension, are converted into binary *.resources* files.</span></span> <span data-ttu-id="c978d-105">Les fichiers binaires sont incorporés dans la sortie du compilateur et peuvent être lus par le <xref:System.Resources.ResourceManager> .</span><span class="sxs-lookup"><span data-stu-id="c978d-105">The binary files are embedded into the output of the compiler and can be read by the <xref:System.Resources.ResourceManager>.</span></span> <span data-ttu-id="c978d-106">Cet article explique comment MSBuild choisit un nom pour chaque fichier *. Resources* .</span><span class="sxs-lookup"><span data-stu-id="c978d-106">This article describes how MSBuild chooses a name for each *.resources* file.</span></span>

> [!TIP]
> <span data-ttu-id="c978d-107">Si vous ajoutez explicitement un élément de ressource à votre fichier projet et qu’il est également [inclus avec le modèles glob par défaut pour .net Core](../project-sdk/overview.md#default-compilation-includes), vous obtiendrez une erreur de Build.</span><span class="sxs-lookup"><span data-stu-id="c978d-107">If you explicitly add a resource item to your project file, and it's also [included with the default include globs for .NET Core](../project-sdk/overview.md#default-compilation-includes), you will get a build error.</span></span> <span data-ttu-id="c978d-108">Pour inclure manuellement les fichiers de ressources en tant qu' `EmbeddedResource` éléments, affectez la valeur `EnableDefaultEmbeddedResourceItems` false à la propriété.</span><span class="sxs-lookup"><span data-stu-id="c978d-108">To manually include resource files as `EmbeddedResource` items, set the `EnableDefaultEmbeddedResourceItems` property to false.</span></span>

## <a name="default-name"></a><span data-ttu-id="c978d-109">Nom par défaut</span><span class="sxs-lookup"><span data-stu-id="c978d-109">Default name</span></span>

<span data-ttu-id="c978d-110">Dans .NET Core 3,0 et versions ultérieures, le nom par défaut d’un manifeste de ressource est utilisé lorsque les deux conditions suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="c978d-110">In .NET Core 3.0 and later, the default name for a resource manifest is used when both of the following conditions are met:</span></span>

- <span data-ttu-id="c978d-111">Le fichier de ressources n’est pas explicitement inclus dans le fichier projet en tant qu' `EmbeddedResource` élément avec les `LogicalName` `ManifestResourceName` `DependentUpon` métadonnées, ou.</span><span class="sxs-lookup"><span data-stu-id="c978d-111">The resource file is not explicitly included in the project file as an `EmbeddedResource` item with `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata.</span></span>
- <span data-ttu-id="c978d-112">La `EmbeddedResourceUseDependentUponConvention` propriété n’a pas la valeur `false` dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="c978d-112">The `EmbeddedResourceUseDependentUponConvention` property is not set to `false` in the project file.</span></span> <span data-ttu-id="c978d-113">Par défaut, cette propriété est définie sur `true`.</span><span class="sxs-lookup"><span data-stu-id="c978d-113">By default, this property is set to `true`.</span></span> <span data-ttu-id="c978d-114">Pour plus d’informations, consultez [EmbeddedResourceUseDependentUponConvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention).</span><span class="sxs-lookup"><span data-stu-id="c978d-114">For more information, see [EmbeddedResourceUseDependentUponConvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention).</span></span>

<span data-ttu-id="c978d-115">Si le fichier de ressources est colocalisé avec un fichier source (*. cs* ou *. vb*) du même nom de fichier racine, le nom complet du premier type défini dans le fichier source est utilisé pour le nom du fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="c978d-115">If the resource file is colocated with a source file (*.cs* or *.vb*) of the same root file name, the full name of the first type that's defined in the source file is used for the manifest file name.</span></span> <span data-ttu-id="c978d-116">Par exemple, si `MyNamespace.Form1` est le premier type défini dans *Form1.cs*et que *Form1.cs* est colocalisé avec *Form1. resx*, le nom du manifeste généré pour ce fichier de ressources est *MyNamespace. Form1. Resources*.</span><span class="sxs-lookup"><span data-stu-id="c978d-116">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, and *Form1.cs* is colocated with *Form1.resx*, the generated manifest name for that resource file is *MyNamespace.Form1.resources*.</span></span>

## <a name="logicalname-metadata"></a><span data-ttu-id="c978d-117">Métadonnées LogicalName</span><span class="sxs-lookup"><span data-stu-id="c978d-117">LogicalName metadata</span></span>

<span data-ttu-id="c978d-118">Si un fichier de ressources est explicitement inclus dans le fichier projet en tant qu' `EmbeddedResource` élément avec des `LogicalName` métadonnées, la `LogicalName` valeur est utilisée comme nom de manifeste.</span><span class="sxs-lookup"><span data-stu-id="c978d-118">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `LogicalName` metadata, the `LogicalName` value is used as the manifest name.</span></span> <span data-ttu-id="c978d-119">`LogicalName`est prioritaire sur toutes les autres métadonnées ou paramètres.</span><span class="sxs-lookup"><span data-stu-id="c978d-119">`LogicalName` takes precedence over any other metadata or setting.</span></span>

<span data-ttu-id="c978d-120">Par exemple, le nom du manifeste du fichier de ressources qui est défini dans l’extrait de code du fichier projet suivant est *nom. Resources*.</span><span class="sxs-lookup"><span data-stu-id="c978d-120">For example, the manifest name for the resource file that's defined in the following project file snippet is *SomeName.resources*.</span></span>

```xml
<EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
```

<span data-ttu-id="c978d-121">-ou-</span><span class="sxs-lookup"><span data-stu-id="c978d-121">-or-</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
```

## <a name="manifestresourcename-metadata"></a><span data-ttu-id="c978d-122">Métadonnées ManifestResourceName</span><span class="sxs-lookup"><span data-stu-id="c978d-122">ManifestResourceName metadata</span></span>

<span data-ttu-id="c978d-123">Si un fichier de ressources est explicitement inclus dans le fichier projet en tant qu' `EmbeddedResource` élément avec des `ManifestResourceName` métadonnées (et qu' `LogicalName` il est absent), la `ManifestResourceName` valeur, associée à l’extension de fichier *. Resources*, est utilisée comme nom de fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="c978d-123">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `ManifestResourceName` metadata (and `LogicalName` is absent), the `ManifestResourceName` value, combined with the file extension *.resources*, is used as the manifest file name.</span></span>

<span data-ttu-id="c978d-124">Par exemple, le nom du manifeste du fichier de ressources qui est défini dans l’extrait de code du fichier projet suivant est *nom. Resources*.</span><span class="sxs-lookup"><span data-stu-id="c978d-124">For example, the manifest name for the resource file that's defined in the following project file snippet is *SomeName.resources*.</span></span>

```xml
<EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
```

<span data-ttu-id="c978d-125">Le nom du manifeste pour le fichier de ressources défini dans l’extrait de code du fichier projet suivant est *somename.fr-fr. Resources*.</span><span class="sxs-lookup"><span data-stu-id="c978d-125">The manifest name for the resource file that's defined in the following project file snippet is *SomeName.fr-FR.resources*.</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
```

## <a name="dependentupon-metadata"></a><span data-ttu-id="c978d-126">Métadonnées DependentUpon</span><span class="sxs-lookup"><span data-stu-id="c978d-126">DependentUpon metadata</span></span>

<span data-ttu-id="c978d-127">Si un fichier de ressources est explicitement inclus dans le fichier projet en tant qu' `EmbeddedResource` élément avec des `DependentUpon` métadonnées (et `LogicalName` et `ManifestResourceName` sont absents), les informations du fichier source défini par `DependentUpon` sont utilisées pour le nom de fichier manifeste de la ressource.</span><span class="sxs-lookup"><span data-stu-id="c978d-127">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `DependentUpon` metadata (and `LogicalName` and `ManifestResourceName` are absent), information from the source file defined by `DependentUpon` is used for the resource manifest file name.</span></span> <span data-ttu-id="c978d-128">Plus précisément, le nom du premier type défini dans le fichier source est utilisé dans le nom du manifeste comme suit : *namespace. ClassName \[ . Culture]. Resources*.</span><span class="sxs-lookup"><span data-stu-id="c978d-128">Specifically, the name of the first type that's defined in the source file is used in the manifest name as follows: *Namespace.Classname\[.Culture].resources*.</span></span>

<span data-ttu-id="c978d-129">Par exemple, le nom du manifeste pour le fichier de ressources qui est défini dans l’extrait de code du fichier projet suivant est *namespace. ClassName. Resources* (où `Namespace.Classname` est la première classe qui est définie dans *myTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="c978d-129">For example, the manifest name for the resource file that's defined in the following project file snippet is *Namespace.Classname.resources* (where `Namespace.Classname` is the first class that's defined in *MyTypes.cs*).</span></span>

```xml
<EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
```

<span data-ttu-id="c978d-130">Le nom du manifeste pour le fichier de ressources défini dans l’extrait de code du fichier projet suivant est *namespace.ClassName.fr-fr. Resources* (où `Namespace.Classname` est la première classe définie dans *myTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="c978d-130">The manifest name for the resource file that's defined in the following project file snippet is *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the first class that's defined in *MyTypes.cs*).</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
```

## <a name="embeddedresourceusedependentuponconvention-property"></a><span data-ttu-id="c978d-131">Propriété EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="c978d-131">EmbeddedResourceUseDependentUponConvention property</span></span>

<span data-ttu-id="c978d-132">Si `EmbeddedResourceUseDependentUponConvention` a la valeur `false` dans le fichier projet, chaque nom de fichier manifeste de ressource est basé sur l’espace de noms racine du projet et le chemin d’accès relatif de la racine du projet au fichier *. resx* .</span><span class="sxs-lookup"><span data-stu-id="c978d-132">If `EmbeddedResourceUseDependentUponConvention` is set to `false` in the project file, each resource manifest file name is based off the root namespace for the project and the relative path from the project root to the *.resx* file.</span></span> <span data-ttu-id="c978d-133">Plus précisément, le nom du fichier manifeste de la ressource générée est *RootNamespace. RelativePathWithDotsForSlashes. \[ Culture.] ressources*.</span><span class="sxs-lookup"><span data-stu-id="c978d-133">More specifically, the generated resource manifest file name is *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span></span> <span data-ttu-id="c978d-134">Il s’agit également de la logique utilisée pour générer les noms des manifestes dans les versions de .NET Core antérieures à 3,0.</span><span class="sxs-lookup"><span data-stu-id="c978d-134">This is also the logic used to generate manifest names in .NET Core versions prior to 3.0.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="c978d-135">Si `RootNamespace` n’est pas défini, le nom du projet est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="c978d-135">If `RootNamespace` is not defined, it defaults to the project name.</span></span>
> - <span data-ttu-id="c978d-136">Si `LogicalName` `ManifestResourceName` `DependentUpon` les métadonnées, ou sont spécifiées pour un `EmbeddedResource` élément dans le fichier projet, cette règle de nommage ne s’applique pas à ce fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="c978d-136">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item in the project file, this naming rule does not apply to that resource file.</span></span>

## <a name="see-also"></a><span data-ttu-id="c978d-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c978d-137">See also</span></span>

- [<span data-ttu-id="c978d-138">Fonctionnement de l’attribution de noms aux ressources de manifeste</span><span class="sxs-lookup"><span data-stu-id="c978d-138">How Manifest Resource Naming Works</span></span>](https://gist.github.com/BenVillalobos/041673b9a73bec60fdc3bf0f86fae62a)
- [<span data-ttu-id="c978d-139">Propriétés MSBuild pour les projets kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="c978d-139">MSBuild properties for .NET Core SDK projects</span></span>](../project-sdk/msbuild-props.md)
- [<span data-ttu-id="c978d-140">Modifications avec rupture MSBuild</span><span class="sxs-lookup"><span data-stu-id="c978d-140">MSBuild breaking changes</span></span>](../compatibility/msbuild.md)
