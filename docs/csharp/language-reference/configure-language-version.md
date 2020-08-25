---
title: Gestion des versions du langage C# - Guide C#
description: Découvrez comment la version du langage C# est déterminée en fonction de votre projet et des raisons qui sous-tendent ce choix. Découvrez comment remplacer manuellement la valeur par défaut.
ms.custom: updateeachrelease
ms.date: 05/20/2020
ms.openlocfilehash: 24797c564890b034683d2989010bc694aabc423c
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811949"
---
# <a name="c-language-versioning"></a><span data-ttu-id="641dc-104">Gestion des versions du langage C#</span><span class="sxs-lookup"><span data-stu-id="641dc-104">C# language versioning</span></span>

<span data-ttu-id="641dc-105">Le compilateur C# le plus récent détermine une version du langage par défaut en fonction du ou des frameworks cibles de votre projet.</span><span class="sxs-lookup"><span data-stu-id="641dc-105">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="641dc-106">Visual Studio ne fournit pas d’interface utilisateur pour modifier la valeur, mais vous pouvez la modifier en modifiant le fichier *csproj* .</span><span class="sxs-lookup"><span data-stu-id="641dc-106">Visual Studio doesn't provide a UI to change the value, but you can change it by editing the *csproj* file.</span></span> <span data-ttu-id="641dc-107">Le choix de la valeur par défaut garantit que vous utilisez la dernière version de langage compatible avec votre Framework cible.</span><span class="sxs-lookup"><span data-stu-id="641dc-107">The choice of default ensures that you use the latest language version compatible with your target framework.</span></span> <span data-ttu-id="641dc-108">Vous bénéficiez d’un accès aux fonctionnalités de langage les plus récentes compatibles avec la cible de votre projet.</span><span class="sxs-lookup"><span data-stu-id="641dc-108">You benefit from access to the latest language features compatible with your project's target.</span></span> <span data-ttu-id="641dc-109">Ce choix par défaut garantit également que vous n’utilisez pas un langage qui requiert des types ou un comportement d’exécution non disponible dans votre version cible de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="641dc-109">This default choice also ensures you don't use a language that requires types or runtime behavior not available in your target framework.</span></span> <span data-ttu-id="641dc-110">Si vous choisissez une version de langue plus récente que la valeur par défaut, il est difficile de diagnostiquer les erreurs de compilation et d’exécution.</span><span class="sxs-lookup"><span data-stu-id="641dc-110">Choosing a language version newer than the default can cause hard to diagnose compile-time and runtime errors.</span></span>

<span data-ttu-id="641dc-111">Les règles de cet article s’appliquent au compilateur fourni avec Visual Studio 2019 ou le kit de développement logiciel (SDK) .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="641dc-111">The rules in this article apply to the compiler delivered with Visual Studio 2019 or the .NET Core 3.0 SDK.</span></span> <span data-ttu-id="641dc-112">Les compilateurs C# qui sont installés en même temps que Visual Studio 2017 ou les versions antérieures du kit SDK .NET Core ciblent C# 7.0 par défaut.</span><span class="sxs-lookup"><span data-stu-id="641dc-112">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span>

<span data-ttu-id="641dc-113">C# 8,0 (et versions ultérieures) est pris en charge uniquement sur .NET Core 3. x et les versions plus récentes.</span><span class="sxs-lookup"><span data-stu-id="641dc-113">C# 8.0 (and higher) is supported only on .NET Core 3.x and newer versions.</span></span> <span data-ttu-id="641dc-114">La plupart des fonctionnalités les plus récentes requièrent des fonctionnalités de bibliothèque et d’exécution introduites dans .NET Core 3. x :</span><span class="sxs-lookup"><span data-stu-id="641dc-114">Many of the newest features require library and runtime features introduced in .NET Core 3.x:</span></span>

- <span data-ttu-id="641dc-115">L’implémentation de l' [interface par défaut](../whats-new/csharp-8.md#default-interface-methods) nécessite de nouvelles fonctionnalités dans le CLR .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="641dc-115">[Default interface implementation](../whats-new/csharp-8.md#default-interface-methods) requires new features in the .NET Core 3.0 CLR.</span></span>
- <span data-ttu-id="641dc-116">Les [flux asynchrones](../whats-new/csharp-8.md#asynchronous-streams) requièrent les nouveaux types <xref:System.IAsyncDisposable?displayProperty=nameWithType> , <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType> et <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="641dc-116">[Async streams](../whats-new/csharp-8.md#asynchronous-streams) require the new types <xref:System.IAsyncDisposable?displayProperty=nameWithType>, <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>, and <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="641dc-117">Les [index et les plages](../whats-new/csharp-8.md#indices-and-ranges) nécessitent les nouveaux types <xref:System.Index?displayProperty=nameWithType> et <xref:System.Range?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="641dc-117">[Indices and ranges](../whats-new/csharp-8.md#indices-and-ranges) require the new types <xref:System.Index?displayProperty=nameWithType> and <xref:System.Range?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="641dc-118">Les [types de référence Nullable](../whats-new/csharp-8.md#nullable-reference-types) utilisent plusieurs [attributs](attributes/nullable-analysis.md) pour fournir de meilleurs avertissements.</span><span class="sxs-lookup"><span data-stu-id="641dc-118">[Nullable reference types](../whats-new/csharp-8.md#nullable-reference-types) make use of several [attributes](attributes/nullable-analysis.md) to provide better warnings.</span></span> <span data-ttu-id="641dc-119">Ces attributs ont été ajoutés dans .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="641dc-119">Those attributes were added in .NET Core 3.0.</span></span> <span data-ttu-id="641dc-120">D’autres frameworks cibles n’ont pas été annotés avec l’un de ces attributs.</span><span class="sxs-lookup"><span data-stu-id="641dc-120">Other target frameworks haven't been annotated with any of these attributes.</span></span> <span data-ttu-id="641dc-121">Cela signifie que les avertissements Nullable peuvent ne pas refléter avec précision les problèmes potentiels.</span><span class="sxs-lookup"><span data-stu-id="641dc-121">That means nullable warnings may not accurately reflect potential issues.</span></span>

## <a name="defaults"></a><span data-ttu-id="641dc-122">Valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="641dc-122">Defaults</span></span>

<span data-ttu-id="641dc-123">Le compilateur détermine une valeur par défaut en fonction de ces règles :</span><span class="sxs-lookup"><span data-stu-id="641dc-123">The compiler determines a default based on these rules:</span></span>

| <span data-ttu-id="641dc-124">Version cible de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="641dc-124">Target framework</span></span> | <span data-ttu-id="641dc-125">version</span><span class="sxs-lookup"><span data-stu-id="641dc-125">version</span></span> | <span data-ttu-id="641dc-126">Version du langage C# par défaut</span><span class="sxs-lookup"><span data-stu-id="641dc-126">C# language version default</span></span> |
|------------------|---------|-----------------------------|
| <span data-ttu-id="641dc-127">.NET Core</span><span class="sxs-lookup"><span data-stu-id="641dc-127">.NET Core</span></span>        | <span data-ttu-id="641dc-128">3.x</span><span class="sxs-lookup"><span data-stu-id="641dc-128">3.x</span></span>     | <span data-ttu-id="641dc-129">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="641dc-129">C# 8.0</span></span>                      |
| <span data-ttu-id="641dc-130">.NET Core</span><span class="sxs-lookup"><span data-stu-id="641dc-130">.NET Core</span></span>        | <span data-ttu-id="641dc-131">2.x</span><span class="sxs-lookup"><span data-stu-id="641dc-131">2.x</span></span>     | <span data-ttu-id="641dc-132">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="641dc-132">C# 7.3</span></span>                      |
| <span data-ttu-id="641dc-133">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="641dc-133">.NET Standard</span></span>    | <span data-ttu-id="641dc-134">2.1</span><span class="sxs-lookup"><span data-stu-id="641dc-134">2.1</span></span>     | <span data-ttu-id="641dc-135">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="641dc-135">C# 8.0</span></span>                      |
| <span data-ttu-id="641dc-136">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="641dc-136">.NET Standard</span></span>    | <span data-ttu-id="641dc-137">2.0</span><span class="sxs-lookup"><span data-stu-id="641dc-137">2.0</span></span>     | <span data-ttu-id="641dc-138">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="641dc-138">C# 7.3</span></span>                      |
| <span data-ttu-id="641dc-139">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="641dc-139">.NET Standard</span></span>    | <span data-ttu-id="641dc-140">1.x</span><span class="sxs-lookup"><span data-stu-id="641dc-140">1.x</span></span>     | <span data-ttu-id="641dc-141">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="641dc-141">C# 7.3</span></span>                      |
| <span data-ttu-id="641dc-142">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="641dc-142">.NET Framework</span></span>   | <span data-ttu-id="641dc-143">all</span><span class="sxs-lookup"><span data-stu-id="641dc-143">all</span></span>     | <span data-ttu-id="641dc-144">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="641dc-144">C# 7.3</span></span>                      |

<span data-ttu-id="641dc-145">Lorsqu’il s’agit d’une préversion cible pour laquelle il existe une préversion du langage correspondante, c’est cette dernière qui est utilisée.</span><span class="sxs-lookup"><span data-stu-id="641dc-145">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="641dc-146">Vous utilisez les fonctionnalités les plus récentes avec cette préversion dans n’importe quel environnement, sans affecter les projets qui ciblent une version .NET Core publiée.</span><span class="sxs-lookup"><span data-stu-id="641dc-146">You use the latest features with that preview in any environment, without affecting projects that target a released .NET Core version.</span></span>

> [!TIP]
> <span data-ttu-id="641dc-147">Pour connaître la version linguistique que vous utilisez actuellement, mettez- `#error version` la (respecte la casse) dans votre code.</span><span class="sxs-lookup"><span data-stu-id="641dc-147">To know what language version you're currently using, put `#error version` (case sensitive) in your code.</span></span> <span data-ttu-id="641dc-148">Ainsi, le compilateur produit un diagnostic, CS8304, avec un message contenant la version du compilateur utilisée et la version de langage actuellement sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="641dc-148">This makes the compiler produce a diagnostic, CS8304, with a message containing the compiler version being used and the current selected language version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="641dc-149">Remplacer les valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="641dc-149">Override a default</span></span>

<span data-ttu-id="641dc-150">Si vous devez spécifier votre version C# explicitement, vous pouvez le faire de plusieurs façons :</span><span class="sxs-lookup"><span data-stu-id="641dc-150">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="641dc-151">Modifiez manuellement votre [fichier projet](#edit-the-project-file).</span><span class="sxs-lookup"><span data-stu-id="641dc-151">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="641dc-152">Définissez la version du langage [pour plusieurs projets d’un sous-répertoire](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="641dc-152">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="641dc-153">Configurez l' [ `-langversion` option du compilateur](compiler-options/langversion-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="641dc-153">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md).</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="641dc-154">Modifier le fichier projet</span><span class="sxs-lookup"><span data-stu-id="641dc-154">Edit the project file</span></span>

<span data-ttu-id="641dc-155">Vous pouvez définir la version du langage dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="641dc-155">You can set the language version in your project file.</span></span> <span data-ttu-id="641dc-156">Par exemple, si vous souhaitez accéder explicitement aux fonctionnalités d’évaluation, ajoutez un élément comme suit :</span><span class="sxs-lookup"><span data-stu-id="641dc-156">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="641dc-157">La valeur `preview` utilise la dernière préversion disponible du langage C# que prend en charge votre compilateur.</span><span class="sxs-lookup"><span data-stu-id="641dc-157">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="641dc-158">Configurer plusieurs projets</span><span class="sxs-lookup"><span data-stu-id="641dc-158">Configure multiple projects</span></span>

<span data-ttu-id="641dc-159">Pour configurer plusieurs projets, vous pouvez créer un fichier **Directory. Build. props** qui contient l' `<LangVersion>` élément.</span><span class="sxs-lookup"><span data-stu-id="641dc-159">To configure multiple projects, you can create a **Directory.Build.props** file that contains the `<LangVersion>` element.</span></span> <span data-ttu-id="641dc-160">En règle générale, vous faites cela dans votre répertoire de solution.</span><span class="sxs-lookup"><span data-stu-id="641dc-160">You typically do that in your solution directory.</span></span> <span data-ttu-id="641dc-161">Ajoutez le code suivant à un fichier **Directory. Build. props** dans le répertoire de votre solution :</span><span class="sxs-lookup"><span data-stu-id="641dc-161">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="641dc-162">Les builds dans tous les sous-répertoires du répertoire contenant ce fichier utiliseront la version d’évaluation en C#.</span><span class="sxs-lookup"><span data-stu-id="641dc-162">Builds in all subdirectories of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="641dc-163">Pour plus d’informations, consultez l’article sur [Personnaliser votre build](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="641dc-163">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="641dc-164">Informations de référence sur la version du langage C#</span><span class="sxs-lookup"><span data-stu-id="641dc-164">C# language version reference</span></span>

<span data-ttu-id="641dc-165">Le tableau suivant montre toutes les versions actuelles du langage C#.</span><span class="sxs-lookup"><span data-stu-id="641dc-165">The following table shows all current C# language versions.</span></span> <span data-ttu-id="641dc-166">Votre compilateur peut ne pas nécessairement comprendre chaque valeur si elle est plus ancienne.</span><span class="sxs-lookup"><span data-stu-id="641dc-166">Your compiler may not necessarily understand every value if it's older.</span></span> <span data-ttu-id="641dc-167">Si vous installez .NET Core 3,0 ou une version ultérieure, vous avez accès à tout ce qui est listé.</span><span class="sxs-lookup"><span data-stu-id="641dc-167">If you install .NET Core 3.0 or later, then you have access to everything listed.</span></span>

[!INCLUDE [langversion-table](includes/langversion-table.md)]

> [!TIP]
> <span data-ttu-id="641dc-168">Ouvrez le [invite de commandes développeur pour Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), puis exécutez la commande suivante pour afficher la liste des versions de langue disponibles sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="641dc-168">Open the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), and run the following command to see the listing of language versions available on your machine.</span></span>
>
> ```CMD
> csc -langversion:?
> ```
>
> <span data-ttu-id="641dc-169">En cas de question de l’option [de compilation-langversion](compiler-options/langversion-compiler-option.md) comme ceci, imprimera un résultat similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="641dc-169">Questioning the [-langversion](compiler-options/langversion-compiler-option.md) compile option like this, will print something similar to the following:</span></span>
>
> ```CMD
> Supported language versions:
> default
> 1
> 2
> 3
> 4
> 5
> 6
> 7.0
> 7.1
> 7.2
> 7.3
> 8.0 (default)
> latestmajor
> preview
> latest
> ```
