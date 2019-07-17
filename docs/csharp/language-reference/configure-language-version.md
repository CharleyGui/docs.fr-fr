---
title: Gestion des versions du langage C# - Guide C#
description: Découvrez comment la version du langage C# est déterminée en fonction de votre projet, et les différentes valeurs que vous pouvez y ajuster manuellement.
ms.date: 07/10/2019
ms.openlocfilehash: 2d593ca0588f291c61cdf52fbc1eb60a1f3f7ecb
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859602"
---
# <a name="c-language-versioning"></a><span data-ttu-id="f7f30-103">Gestion des versions du langage C#</span><span class="sxs-lookup"><span data-stu-id="f7f30-103">C# language versioning</span></span>

<span data-ttu-id="f7f30-104">Le compilateur C# détermine une version du langage par défaut en fonction du ou des versions cibles de .NET Framework du projet concerné.</span><span class="sxs-lookup"><span data-stu-id="f7f30-104">The C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="f7f30-105">La raison est que le langage C# peut avoir des fonctionnalités qui reposent sur des types ou des composants d’exécution qui ne sont pas disponibles dans chaque implémentation .NET.</span><span class="sxs-lookup"><span data-stu-id="f7f30-105">This is because the C# language may have features that rely on types or runtime components that are not available in every .NET implementation.</span></span> <span data-ttu-id="f7f30-106">Cela garantit aussi que quelle que soit la cible sur laquelle votre projet est créé, vous obtenez la version de langage compatible la plus récente par défaut.</span><span class="sxs-lookup"><span data-stu-id="f7f30-106">This also ensures that for whatever target your project is built against, you get the highest compatible language version by default.</span></span>

## <a name="defaults"></a><span data-ttu-id="f7f30-107">Valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="f7f30-107">Defaults</span></span>

<span data-ttu-id="f7f30-108">Le compilateur détermine une valeur par défaut en fonction de ces règles :</span><span class="sxs-lookup"><span data-stu-id="f7f30-108">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="f7f30-109">Version cible de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f7f30-109">Target framework</span></span>|<span data-ttu-id="f7f30-110">version</span><span class="sxs-lookup"><span data-stu-id="f7f30-110">version</span></span>|<span data-ttu-id="f7f30-111">Version du langage C# par défaut</span><span class="sxs-lookup"><span data-stu-id="f7f30-111">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="f7f30-112">.NET Core</span><span class="sxs-lookup"><span data-stu-id="f7f30-112">.NET Core</span></span>|<span data-ttu-id="f7f30-113">3.x</span><span class="sxs-lookup"><span data-stu-id="f7f30-113">3.x</span></span>|<span data-ttu-id="f7f30-114">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="f7f30-114">C# 8.0</span></span>|
|<span data-ttu-id="f7f30-115">.NET Core</span><span class="sxs-lookup"><span data-stu-id="f7f30-115">.NET Core</span></span>|<span data-ttu-id="f7f30-116">2.x</span><span class="sxs-lookup"><span data-stu-id="f7f30-116">2.x</span></span>|<span data-ttu-id="f7f30-117">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="f7f30-117">C# 7.3</span></span>|
|<span data-ttu-id="f7f30-118">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="f7f30-118">.NET Standard</span></span>|<span data-ttu-id="f7f30-119">all</span><span class="sxs-lookup"><span data-stu-id="f7f30-119">all</span></span>|<span data-ttu-id="f7f30-120">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="f7f30-120">C# 7.3</span></span>|
|<span data-ttu-id="f7f30-121">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="f7f30-121">.NET Framework</span></span>|<span data-ttu-id="f7f30-122">all</span><span class="sxs-lookup"><span data-stu-id="f7f30-122">all</span></span>|<span data-ttu-id="f7f30-123">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="f7f30-123">C# 7.3</span></span>|

## <a name="default-for-previews"></a><span data-ttu-id="f7f30-124">Valeur par défaut pour les préversions</span><span class="sxs-lookup"><span data-stu-id="f7f30-124">Default for previews</span></span>

<span data-ttu-id="f7f30-125">Lorsqu’il s’agit d’une préversion cible pour laquelle il existe une préversion du langage correspondante, c’est cette dernière qui est utilisée.</span><span class="sxs-lookup"><span data-stu-id="f7f30-125">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="f7f30-126">Vous avez ainsi l’assurance de pouvoir utiliser les fonctionnalités les plus récentes dont le fonctionnement est garanti avec cette préversion dans n’importe quel environnement sans affecter vos projets qui ciblent une version finale de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f7f30-126">This ensures that you can use the latest features that are guaranteed to work with that preview in any environment without affecting your projects that target a released .NET Core version.</span></span>

## <a name="overriding-a-default"></a><span data-ttu-id="f7f30-127">Remplacement d’une valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="f7f30-127">Overriding a default</span></span>

<span data-ttu-id="f7f30-128">Si vous devez spécifier votre version C# explicitement, vous pouvez le faire de plusieurs façons :</span><span class="sxs-lookup"><span data-stu-id="f7f30-128">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="f7f30-129">Modifiez manuellement votre [fichier projet](#edit-the-project-file).</span><span class="sxs-lookup"><span data-stu-id="f7f30-129">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="f7f30-130">Définissez la version du langage [pour plusieurs projets d’un sous-répertoire](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="f7f30-130">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="f7f30-131">Configurez l’[option de compilateur `-langversion`](#set-the-langversion-compiler-option).</span><span class="sxs-lookup"><span data-stu-id="f7f30-131">Configure the [`-langversion` compiler option](#set-the-langversion-compiler-option).</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="f7f30-132">Modifier le fichier projet</span><span class="sxs-lookup"><span data-stu-id="f7f30-132">Edit the project file</span></span>

<span data-ttu-id="f7f30-133">Vous pouvez définir la version du langage dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="f7f30-133">You can set the language version in your project file.</span></span> <span data-ttu-id="f7f30-134">Par exemple, si vous souhaitez accéder explicitement aux fonctionnalités en préversion, vous pouvez ajouter un élément comme suit :</span><span class="sxs-lookup"><span data-stu-id="f7f30-134">For example, if you explicitly wanted access to preview features, you could do add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="f7f30-135">La valeur `preview` utilise la dernière préversion disponible du langage C# que prend en charge votre compilateur.</span><span class="sxs-lookup"><span data-stu-id="f7f30-135">The value `preview` uses the latest available preview C# language that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="f7f30-136">Configurer plusieurs projets</span><span class="sxs-lookup"><span data-stu-id="f7f30-136">Configure multiple projects</span></span>

<span data-ttu-id="f7f30-137">Vous pouvez créer un fichier **Directory.Build.props** contenant l’élément `<LangVersion>` pour configurer plusieurs répertoires.</span><span class="sxs-lookup"><span data-stu-id="f7f30-137">You can create a **Directory.Build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="f7f30-138">En règle générale, vous faites cela dans votre répertoire de solution.</span><span class="sxs-lookup"><span data-stu-id="f7f30-138">You typically do that in your solution directory.</span></span> <span data-ttu-id="f7f30-139">Ajoutez le code suivant à un fichier **Directory.build.props** dans votre répertoire de solution :</span><span class="sxs-lookup"><span data-stu-id="f7f30-139">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="f7f30-140">Maintenant, les builds de chaque sous-répertoire du répertoire contenant ce fichier vont utiliser la préversion de C#.</span><span class="sxs-lookup"><span data-stu-id="f7f30-140">Now, builds in every subdirectory of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="f7f30-141">Pour plus d’informations, consultez l’article sur [Personnaliser votre build](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="f7f30-141">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="f7f30-142">Informations de référence sur la version du langage C#</span><span class="sxs-lookup"><span data-stu-id="f7f30-142">C# language version reference</span></span>

<span data-ttu-id="f7f30-143">Le tableau suivant montre toutes les versions actuelles du langage C#.</span><span class="sxs-lookup"><span data-stu-id="f7f30-143">The following table shows all current C# language versions.</span></span> <span data-ttu-id="f7f30-144">Votre compilateur peut ne pas nécessairement comprendre chaque valeur si celle-ci est plus ancienne.</span><span class="sxs-lookup"><span data-stu-id="f7f30-144">Your compiler may not necessarily understand every value if it is older.</span></span> <span data-ttu-id="f7f30-145">Si vous installez .NET Core 3.0, vous avez accès à toutes les versions listées.</span><span class="sxs-lookup"><span data-stu-id="f7f30-145">If you install .NET Core 3.0, then you will have access to everything listed.</span></span>

|<span data-ttu-id="f7f30-146">Value</span><span class="sxs-lookup"><span data-stu-id="f7f30-146">Value</span></span>|<span data-ttu-id="f7f30-147">Signification</span><span class="sxs-lookup"><span data-stu-id="f7f30-147">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="f7f30-148">preview</span><span class="sxs-lookup"><span data-stu-id="f7f30-148">preview</span></span>|<span data-ttu-id="f7f30-149">Le compilateur accepte toute la syntaxe de langage valide de la dernière préversion.</span><span class="sxs-lookup"><span data-stu-id="f7f30-149">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="f7f30-150">latest</span><span class="sxs-lookup"><span data-stu-id="f7f30-150">latest</span></span>|<span data-ttu-id="f7f30-151">Le compilateur accepte la syntaxe de la dernière version publiée du compilateur (versions mineures incluses).</span><span class="sxs-lookup"><span data-stu-id="f7f30-151">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="f7f30-152">latestMajor</span><span class="sxs-lookup"><span data-stu-id="f7f30-152">latestMajor</span></span>|<span data-ttu-id="f7f30-153">Le compilateur accepte la syntaxe de la dernière version principale publiée du compilateur.</span><span class="sxs-lookup"><span data-stu-id="f7f30-153">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="f7f30-154">8.0</span><span class="sxs-lookup"><span data-stu-id="f7f30-154">8.0</span></span>|<span data-ttu-id="f7f30-155">Le compilateur accepte uniquement la syntaxe incluse dans C# 8.0 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="f7f30-155">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="f7f30-156">7.3</span><span class="sxs-lookup"><span data-stu-id="f7f30-156">7.3</span></span>|<span data-ttu-id="f7f30-157">Le compilateur accepte uniquement la syntaxe incluse dans C# 7.3 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="f7f30-157">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="f7f30-158">7.2</span><span class="sxs-lookup"><span data-stu-id="f7f30-158">7.2</span></span>|<span data-ttu-id="f7f30-159">Le compilateur accepte uniquement la syntaxe incluse dans C# 7.2 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="f7f30-159">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="f7f30-160">7.1</span><span class="sxs-lookup"><span data-stu-id="f7f30-160">7.1</span></span>|<span data-ttu-id="f7f30-161">Le compilateur accepte uniquement la syntaxe incluse dans C# 7.1 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="f7f30-161">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="f7f30-162">7</span><span class="sxs-lookup"><span data-stu-id="f7f30-162">7</span></span>|<span data-ttu-id="f7f30-163">Le compilateur accepte uniquement la syntaxe incluse dans C# 7.0 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="f7f30-163">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="f7f30-164">6</span><span class="sxs-lookup"><span data-stu-id="f7f30-164">6</span></span>|<span data-ttu-id="f7f30-165">Le compilateur accepte uniquement la syntaxe incluse dans C# 6.0 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="f7f30-165">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="f7f30-166">5</span><span class="sxs-lookup"><span data-stu-id="f7f30-166">5</span></span>|<span data-ttu-id="f7f30-167">Le compilateur accepte uniquement la syntaxe incluse dans C# 5.0 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="f7f30-167">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="f7f30-168">4</span><span class="sxs-lookup"><span data-stu-id="f7f30-168">4</span></span>|<span data-ttu-id="f7f30-169">Le compilateur accepte uniquement la syntaxe incluse dans C# 4.0 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="f7f30-169">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="f7f30-170">3</span><span class="sxs-lookup"><span data-stu-id="f7f30-170">3</span></span>|<span data-ttu-id="f7f30-171">Le compilateur accepte uniquement la syntaxe incluse dans C# 3.0 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="f7f30-171">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="f7f30-172">ISO-2</span><span class="sxs-lookup"><span data-stu-id="f7f30-172">ISO-2</span></span>|<span data-ttu-id="f7f30-173">Le compilateur accepte uniquement la syntaxe incluse dans ISO/IEC 23270:2006 C# (2.0)</span><span class="sxs-lookup"><span data-stu-id="f7f30-173">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="f7f30-174">ISO-1</span><span class="sxs-lookup"><span data-stu-id="f7f30-174">ISO-1</span></span>|<span data-ttu-id="f7f30-175">Le compilateur accepte uniquement la syntaxe incluse dans ISO/IEC 23270:2003 C# (1.0/1.2)</span><span class="sxs-lookup"><span data-stu-id="f7f30-175">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
