---
title: Gestion des versions du langage C# - Guide C#
description: Découvrez comment la version du langage C# est déterminée en fonction de votre projet, et les différentes valeurs que vous pouvez y ajuster manuellement.
ms.date: 07/10/2019
ms.openlocfilehash: fae36f5305e23fbfa1c55c5881e37391670f93ab
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040348"
---
# <a name="c-language-versioning"></a><span data-ttu-id="91b7f-103">Gestion des versions du langage C#</span><span class="sxs-lookup"><span data-stu-id="91b7f-103">C# language versioning</span></span>

<span data-ttu-id="91b7f-104">Le compilateur C# le plus récent détermine une version du langage par défaut en fonction du ou des frameworks cibles de votre projet.</span><span class="sxs-lookup"><span data-stu-id="91b7f-104">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="91b7f-105">La raison est que le langage C# peut avoir des fonctionnalités qui reposent sur des types ou des composants d’exécution qui ne sont pas disponibles dans chaque implémentation .NET.</span><span class="sxs-lookup"><span data-stu-id="91b7f-105">This is because the C# language may have features that rely on types or runtime components that are not available in every .NET implementation.</span></span> <span data-ttu-id="91b7f-106">Cela garantit aussi que quelle que soit la cible sur laquelle votre projet est créé, vous obtenez la version de langage compatible la plus récente par défaut.</span><span class="sxs-lookup"><span data-stu-id="91b7f-106">This also ensures that for whatever target your project is built against, you get the highest compatible language version by default.</span></span>

<span data-ttu-id="91b7f-107">Les règles mentionnées dans cet article s’appliquent au compilateur fourni avec Visual Studio 2019 ou le kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="91b7f-107">The rules in this article apply to the compiler delivered with Visual Studio 2019, or the .NET Core 3.0 SDK.</span></span> <span data-ttu-id="91b7f-108">Les compilateurs C# qui sont installés en même temps que Visual Studio 2017 ou les versions antérieures du kit SDK .NET Core ciblent C# 7.0 par défaut.</span><span class="sxs-lookup"><span data-stu-id="91b7f-108">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span> 

## <a name="defaults"></a><span data-ttu-id="91b7f-109">Valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="91b7f-109">Defaults</span></span>

<span data-ttu-id="91b7f-110">Le compilateur détermine une valeur par défaut en fonction de ces règles :</span><span class="sxs-lookup"><span data-stu-id="91b7f-110">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="91b7f-111">Version cible de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="91b7f-111">Target framework</span></span>|<span data-ttu-id="91b7f-112">version</span><span class="sxs-lookup"><span data-stu-id="91b7f-112">version</span></span>|<span data-ttu-id="91b7f-113">Version du langage C# par défaut</span><span class="sxs-lookup"><span data-stu-id="91b7f-113">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="91b7f-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="91b7f-114">.NET Core</span></span>|<span data-ttu-id="91b7f-115">3.x</span><span class="sxs-lookup"><span data-stu-id="91b7f-115">3.x</span></span>|<span data-ttu-id="91b7f-116">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="91b7f-116">C# 8.0</span></span>|
|<span data-ttu-id="91b7f-117">.NET Core</span><span class="sxs-lookup"><span data-stu-id="91b7f-117">.NET Core</span></span>|<span data-ttu-id="91b7f-118">2.x</span><span class="sxs-lookup"><span data-stu-id="91b7f-118">2.x</span></span>|<span data-ttu-id="91b7f-119">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="91b7f-119">C# 7.3</span></span>|
|<span data-ttu-id="91b7f-120">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="91b7f-120">.NET Standard</span></span>|<span data-ttu-id="91b7f-121">all</span><span class="sxs-lookup"><span data-stu-id="91b7f-121">all</span></span>|<span data-ttu-id="91b7f-122">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="91b7f-122">C# 7.3</span></span>|
|<span data-ttu-id="91b7f-123">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="91b7f-123">.NET Framework</span></span>|<span data-ttu-id="91b7f-124">all</span><span class="sxs-lookup"><span data-stu-id="91b7f-124">all</span></span>|<span data-ttu-id="91b7f-125">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="91b7f-125">C# 7.3</span></span>|

## <a name="default-for-previews"></a><span data-ttu-id="91b7f-126">Valeur par défaut pour les préversions</span><span class="sxs-lookup"><span data-stu-id="91b7f-126">Default for previews</span></span>

<span data-ttu-id="91b7f-127">Lorsqu’il s’agit d’une préversion cible pour laquelle il existe une préversion du langage correspondante, c’est cette dernière qui est utilisée.</span><span class="sxs-lookup"><span data-stu-id="91b7f-127">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="91b7f-128">Vous avez ainsi l’assurance de pouvoir utiliser les fonctionnalités les plus récentes dont le fonctionnement est garanti avec cette préversion dans n’importe quel environnement sans affecter vos projets qui ciblent une version finale de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="91b7f-128">This ensures that you can use the latest features that are guaranteed to work with that preview in any environment without affecting your projects that target a released .NET Core version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="91b7f-129">Remplacer les valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="91b7f-129">Override a default</span></span>

<span data-ttu-id="91b7f-130">Si vous devez spécifier votre version C# explicitement, vous pouvez le faire de plusieurs façons :</span><span class="sxs-lookup"><span data-stu-id="91b7f-130">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="91b7f-131">Modifiez manuellement votre [fichier projet](#edit-the-project-file).</span><span class="sxs-lookup"><span data-stu-id="91b7f-131">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="91b7f-132">Définissez la version du langage [pour plusieurs projets d’un sous-répertoire](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="91b7f-132">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="91b7f-133">Configurez l’option de compilateur [`-langversion` ](compiler-options/langversion-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="91b7f-133">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md)</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="91b7f-134">Modifier le fichier projet</span><span class="sxs-lookup"><span data-stu-id="91b7f-134">Edit the project file</span></span>

<span data-ttu-id="91b7f-135">Vous pouvez définir la version du langage dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="91b7f-135">You can set the language version in your project file.</span></span> <span data-ttu-id="91b7f-136">Par exemple, si vous souhaitez accéder explicitement aux fonctionnalités d’évaluation, ajoutez un élément comme suit :</span><span class="sxs-lookup"><span data-stu-id="91b7f-136">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="91b7f-137">La valeur `preview` utilise la dernière préversion disponible du langage C# que prend en charge votre compilateur.</span><span class="sxs-lookup"><span data-stu-id="91b7f-137">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="91b7f-138">Configurer plusieurs projets</span><span class="sxs-lookup"><span data-stu-id="91b7f-138">Configure multiple projects</span></span>

<span data-ttu-id="91b7f-139">Vous pouvez créer un fichier **Directory.Build.props** contenant l’élément `<LangVersion>` pour configurer plusieurs répertoires.</span><span class="sxs-lookup"><span data-stu-id="91b7f-139">You can create a **Directory.Build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="91b7f-140">En règle générale, vous faites cela dans votre répertoire de solution.</span><span class="sxs-lookup"><span data-stu-id="91b7f-140">You typically do that in your solution directory.</span></span> <span data-ttu-id="91b7f-141">Ajoutez le code suivant à un fichier **Directory.build.props** dans votre répertoire de solution :</span><span class="sxs-lookup"><span data-stu-id="91b7f-141">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="91b7f-142">Maintenant, les builds de chaque sous-répertoire du répertoire contenant ce fichier vont utiliser la préversion de C#.</span><span class="sxs-lookup"><span data-stu-id="91b7f-142">Now, builds in every subdirectory of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="91b7f-143">Pour plus d’informations, consultez l’article sur [Personnaliser votre build](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="91b7f-143">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="91b7f-144">Informations de référence sur la version du langage C#</span><span class="sxs-lookup"><span data-stu-id="91b7f-144">C# language version reference</span></span>

<span data-ttu-id="91b7f-145">Le tableau suivant montre toutes les versions actuelles du langage C#.</span><span class="sxs-lookup"><span data-stu-id="91b7f-145">The following table shows all current C# language versions.</span></span> <span data-ttu-id="91b7f-146">Votre compilateur peut ne pas nécessairement comprendre chaque valeur si celle-ci est plus ancienne.</span><span class="sxs-lookup"><span data-stu-id="91b7f-146">Your compiler may not necessarily understand every value if it is older.</span></span> <span data-ttu-id="91b7f-147">Si vous installez .NET Core 3.0, vous avez accès à toutes les versions listées.</span><span class="sxs-lookup"><span data-stu-id="91b7f-147">If you install .NET Core 3.0, then you will have access to everything listed.</span></span>

|<span data-ttu-id="91b7f-148">Value</span><span class="sxs-lookup"><span data-stu-id="91b7f-148">Value</span></span>|<span data-ttu-id="91b7f-149">Signification</span><span class="sxs-lookup"><span data-stu-id="91b7f-149">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="91b7f-150">preview</span><span class="sxs-lookup"><span data-stu-id="91b7f-150">preview</span></span>|<span data-ttu-id="91b7f-151">Le compilateur accepte toute la syntaxe de langage valide de la dernière préversion.</span><span class="sxs-lookup"><span data-stu-id="91b7f-151">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="91b7f-152">latest</span><span class="sxs-lookup"><span data-stu-id="91b7f-152">latest</span></span>|<span data-ttu-id="91b7f-153">Le compilateur accepte la syntaxe de la dernière version publiée du compilateur (versions mineures incluses).</span><span class="sxs-lookup"><span data-stu-id="91b7f-153">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="91b7f-154">latestMajor</span><span class="sxs-lookup"><span data-stu-id="91b7f-154">latestMajor</span></span>|<span data-ttu-id="91b7f-155">Le compilateur accepte la syntaxe de la dernière version principale publiée du compilateur.</span><span class="sxs-lookup"><span data-stu-id="91b7f-155">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="91b7f-156">8.0</span><span class="sxs-lookup"><span data-stu-id="91b7f-156">8.0</span></span>|<span data-ttu-id="91b7f-157">Le compilateur accepte uniquement la syntaxe incluse dans C# 8.0 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="91b7f-157">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="91b7f-158">7.3</span><span class="sxs-lookup"><span data-stu-id="91b7f-158">7.3</span></span>|<span data-ttu-id="91b7f-159">Le compilateur accepte uniquement la syntaxe incluse dans C# 7.3 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="91b7f-159">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="91b7f-160">7.2</span><span class="sxs-lookup"><span data-stu-id="91b7f-160">7.2</span></span>|<span data-ttu-id="91b7f-161">Le compilateur accepte uniquement la syntaxe incluse dans C# 7.2 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="91b7f-161">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="91b7f-162">7.1</span><span class="sxs-lookup"><span data-stu-id="91b7f-162">7.1</span></span>|<span data-ttu-id="91b7f-163">Le compilateur accepte uniquement la syntaxe incluse dans C# 7.1 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="91b7f-163">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="91b7f-164">7</span><span class="sxs-lookup"><span data-stu-id="91b7f-164">7</span></span>|<span data-ttu-id="91b7f-165">Le compilateur accepte uniquement la syntaxe incluse dans C# 7.0 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="91b7f-165">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="91b7f-166">6</span><span class="sxs-lookup"><span data-stu-id="91b7f-166">6</span></span>|<span data-ttu-id="91b7f-167">Le compilateur accepte uniquement la syntaxe incluse dans C# 6.0 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="91b7f-167">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="91b7f-168">5</span><span class="sxs-lookup"><span data-stu-id="91b7f-168">5</span></span>|<span data-ttu-id="91b7f-169">Le compilateur accepte uniquement la syntaxe incluse dans C# 5.0 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="91b7f-169">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="91b7f-170">4</span><span class="sxs-lookup"><span data-stu-id="91b7f-170">4</span></span>|<span data-ttu-id="91b7f-171">Le compilateur accepte uniquement la syntaxe incluse dans C# 4.0 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="91b7f-171">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="91b7f-172">3</span><span class="sxs-lookup"><span data-stu-id="91b7f-172">3</span></span>|<span data-ttu-id="91b7f-173">Le compilateur accepte uniquement la syntaxe incluse dans C# 3.0 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="91b7f-173">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="91b7f-174">ISO-2</span><span class="sxs-lookup"><span data-stu-id="91b7f-174">ISO-2</span></span>|<span data-ttu-id="91b7f-175">Le compilateur accepte uniquement la syntaxe incluse dans ISO/IEC 23270:2006 C# (2.0)</span><span class="sxs-lookup"><span data-stu-id="91b7f-175">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="91b7f-176">ISO-1</span><span class="sxs-lookup"><span data-stu-id="91b7f-176">ISO-1</span></span>|<span data-ttu-id="91b7f-177">Le compilateur accepte uniquement la syntaxe incluse dans ISO/IEC 23270:2003 C# (1.0/1.2)</span><span class="sxs-lookup"><span data-stu-id="91b7f-177">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
