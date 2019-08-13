---
title: Gestion des versions du langage C# - Guide C#
description: Découvrez comment la version du langage C# est déterminée en fonction de votre projet, et les différentes valeurs que vous pouvez y ajuster manuellement.
ms.date: 07/10/2019
ms.openlocfilehash: 744cec0aac21f743648cccbdc93cf2977c32d644
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796533"
---
# <a name="c-language-versioning"></a><span data-ttu-id="5d677-103">Gestion des versions du langage C#</span><span class="sxs-lookup"><span data-stu-id="5d677-103">C# language versioning</span></span>

<span data-ttu-id="5d677-104">Le compilateur C# détermine une version du langage par défaut en fonction du ou des versions cibles de .NET Framework du projet concerné.</span><span class="sxs-lookup"><span data-stu-id="5d677-104">The C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="5d677-105">La raison est que le langage C# peut avoir des fonctionnalités qui reposent sur des types ou des composants d’exécution qui ne sont pas disponibles dans chaque implémentation .NET.</span><span class="sxs-lookup"><span data-stu-id="5d677-105">This is because the C# language may have features that rely on types or runtime components that are not available in every .NET implementation.</span></span> <span data-ttu-id="5d677-106">Cela garantit aussi que quelle que soit la cible sur laquelle votre projet est créé, vous obtenez la version de langage compatible la plus récente par défaut.</span><span class="sxs-lookup"><span data-stu-id="5d677-106">This also ensures that for whatever target your project is built against, you get the highest compatible language version by default.</span></span>

## <a name="defaults"></a><span data-ttu-id="5d677-107">Valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="5d677-107">Defaults</span></span>

<span data-ttu-id="5d677-108">Le compilateur détermine une valeur par défaut en fonction de ces règles :</span><span class="sxs-lookup"><span data-stu-id="5d677-108">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="5d677-109">Version cible de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5d677-109">Target framework</span></span>|<span data-ttu-id="5d677-110">version</span><span class="sxs-lookup"><span data-stu-id="5d677-110">version</span></span>|<span data-ttu-id="5d677-111">Version du langage C# par défaut</span><span class="sxs-lookup"><span data-stu-id="5d677-111">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="5d677-112">.NET Core</span><span class="sxs-lookup"><span data-stu-id="5d677-112">.NET Core</span></span>|<span data-ttu-id="5d677-113">3.x</span><span class="sxs-lookup"><span data-stu-id="5d677-113">3.x</span></span>|<span data-ttu-id="5d677-114">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="5d677-114">C# 8.0</span></span>|
|<span data-ttu-id="5d677-115">.NET Core</span><span class="sxs-lookup"><span data-stu-id="5d677-115">.NET Core</span></span>|<span data-ttu-id="5d677-116">2.x</span><span class="sxs-lookup"><span data-stu-id="5d677-116">2.x</span></span>|<span data-ttu-id="5d677-117">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="5d677-117">C# 7.3</span></span>|
|<span data-ttu-id="5d677-118">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="5d677-118">.NET Standard</span></span>|<span data-ttu-id="5d677-119">all</span><span class="sxs-lookup"><span data-stu-id="5d677-119">all</span></span>|<span data-ttu-id="5d677-120">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="5d677-120">C# 7.3</span></span>|
|<span data-ttu-id="5d677-121">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="5d677-121">.NET Framework</span></span>|<span data-ttu-id="5d677-122">all</span><span class="sxs-lookup"><span data-stu-id="5d677-122">all</span></span>|<span data-ttu-id="5d677-123">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="5d677-123">C# 7.3</span></span>|

## <a name="default-for-previews"></a><span data-ttu-id="5d677-124">Valeur par défaut pour les préversions</span><span class="sxs-lookup"><span data-stu-id="5d677-124">Default for previews</span></span>

<span data-ttu-id="5d677-125">Lorsqu’il s’agit d’une préversion cible pour laquelle il existe une préversion du langage correspondante, c’est cette dernière qui est utilisée.</span><span class="sxs-lookup"><span data-stu-id="5d677-125">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="5d677-126">Vous avez ainsi l’assurance de pouvoir utiliser les fonctionnalités les plus récentes dont le fonctionnement est garanti avec cette préversion dans n’importe quel environnement sans affecter vos projets qui ciblent une version finale de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5d677-126">This ensures that you can use the latest features that are guaranteed to work with that preview in any environment without affecting your projects that target a released .NET Core version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="5d677-127">Remplacer les valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="5d677-127">Override a default</span></span>

<span data-ttu-id="5d677-128">Si vous devez spécifier votre version C# explicitement, vous pouvez le faire de plusieurs façons :</span><span class="sxs-lookup"><span data-stu-id="5d677-128">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="5d677-129">Modifiez manuellement votre [fichier projet](#edit-the-project-file).</span><span class="sxs-lookup"><span data-stu-id="5d677-129">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="5d677-130">Définissez la version du langage [pour plusieurs projets d’un sous-répertoire](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="5d677-130">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="5d677-131">Configurez l’option de compilateur [`-langversion` ](compiler-options/langversion-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="5d677-131">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md)</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="5d677-132">Modifier le fichier projet</span><span class="sxs-lookup"><span data-stu-id="5d677-132">Edit the project file</span></span>

<span data-ttu-id="5d677-133">Vous pouvez définir la version du langage dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="5d677-133">You can set the language version in your project file.</span></span> <span data-ttu-id="5d677-134">Par exemple, si vous souhaitez accéder explicitement aux fonctionnalités d’évaluation, ajoutez un élément comme suit :</span><span class="sxs-lookup"><span data-stu-id="5d677-134">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="5d677-135">La valeur `preview` utilise la dernière préversion disponible du langage C# que prend en charge votre compilateur.</span><span class="sxs-lookup"><span data-stu-id="5d677-135">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="5d677-136">Configurer plusieurs projets</span><span class="sxs-lookup"><span data-stu-id="5d677-136">Configure multiple projects</span></span>

<span data-ttu-id="5d677-137">Vous pouvez créer un fichier **Directory.Build.props** contenant l’élément `<LangVersion>` pour configurer plusieurs répertoires.</span><span class="sxs-lookup"><span data-stu-id="5d677-137">You can create a **Directory.Build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="5d677-138">En règle générale, vous faites cela dans votre répertoire de solution.</span><span class="sxs-lookup"><span data-stu-id="5d677-138">You typically do that in your solution directory.</span></span> <span data-ttu-id="5d677-139">Ajoutez le code suivant à un fichier **Directory.build.props** dans votre répertoire de solution :</span><span class="sxs-lookup"><span data-stu-id="5d677-139">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="5d677-140">Maintenant, les builds de chaque sous-répertoire du répertoire contenant ce fichier vont utiliser la préversion de C#.</span><span class="sxs-lookup"><span data-stu-id="5d677-140">Now, builds in every subdirectory of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="5d677-141">Pour plus d’informations, consultez l’article sur [Personnaliser votre build](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="5d677-141">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="5d677-142">Informations de référence sur la version du langage C#</span><span class="sxs-lookup"><span data-stu-id="5d677-142">C# language version reference</span></span>

<span data-ttu-id="5d677-143">Le tableau suivant montre toutes les versions actuelles du langage C#.</span><span class="sxs-lookup"><span data-stu-id="5d677-143">The following table shows all current C# language versions.</span></span> <span data-ttu-id="5d677-144">Votre compilateur peut ne pas nécessairement comprendre chaque valeur si celle-ci est plus ancienne.</span><span class="sxs-lookup"><span data-stu-id="5d677-144">Your compiler may not necessarily understand every value if it is older.</span></span> <span data-ttu-id="5d677-145">Si vous installez .NET Core 3.0, vous avez accès à toutes les versions listées.</span><span class="sxs-lookup"><span data-stu-id="5d677-145">If you install .NET Core 3.0, then you will have access to everything listed.</span></span>

|<span data-ttu-id="5d677-146">Value</span><span class="sxs-lookup"><span data-stu-id="5d677-146">Value</span></span>|<span data-ttu-id="5d677-147">Signification</span><span class="sxs-lookup"><span data-stu-id="5d677-147">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="5d677-148">preview</span><span class="sxs-lookup"><span data-stu-id="5d677-148">preview</span></span>|<span data-ttu-id="5d677-149">Le compilateur accepte toute la syntaxe de langage valide de la dernière préversion.</span><span class="sxs-lookup"><span data-stu-id="5d677-149">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="5d677-150">latest</span><span class="sxs-lookup"><span data-stu-id="5d677-150">latest</span></span>|<span data-ttu-id="5d677-151">Le compilateur accepte la syntaxe de la dernière version publiée du compilateur (versions mineures incluses).</span><span class="sxs-lookup"><span data-stu-id="5d677-151">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="5d677-152">latestMajor</span><span class="sxs-lookup"><span data-stu-id="5d677-152">latestMajor</span></span>|<span data-ttu-id="5d677-153">Le compilateur accepte la syntaxe de la dernière version principale publiée du compilateur.</span><span class="sxs-lookup"><span data-stu-id="5d677-153">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="5d677-154">8.0</span><span class="sxs-lookup"><span data-stu-id="5d677-154">8.0</span></span>|<span data-ttu-id="5d677-155">Le compilateur accepte uniquement la syntaxe incluse dans C# 8.0 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="5d677-155">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="5d677-156">7.3</span><span class="sxs-lookup"><span data-stu-id="5d677-156">7.3</span></span>|<span data-ttu-id="5d677-157">Le compilateur accepte uniquement la syntaxe incluse dans C# 7.3 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="5d677-157">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="5d677-158">7.2</span><span class="sxs-lookup"><span data-stu-id="5d677-158">7.2</span></span>|<span data-ttu-id="5d677-159">Le compilateur accepte uniquement la syntaxe incluse dans C# 7.2 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="5d677-159">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="5d677-160">7.1</span><span class="sxs-lookup"><span data-stu-id="5d677-160">7.1</span></span>|<span data-ttu-id="5d677-161">Le compilateur accepte uniquement la syntaxe incluse dans C# 7.1 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="5d677-161">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="5d677-162">7</span><span class="sxs-lookup"><span data-stu-id="5d677-162">7</span></span>|<span data-ttu-id="5d677-163">Le compilateur accepte uniquement la syntaxe incluse dans C# 7.0 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="5d677-163">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="5d677-164">6</span><span class="sxs-lookup"><span data-stu-id="5d677-164">6</span></span>|<span data-ttu-id="5d677-165">Le compilateur accepte uniquement la syntaxe incluse dans C# 6.0 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="5d677-165">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="5d677-166">5</span><span class="sxs-lookup"><span data-stu-id="5d677-166">5</span></span>|<span data-ttu-id="5d677-167">Le compilateur accepte uniquement la syntaxe incluse dans C# 5.0 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="5d677-167">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="5d677-168">4</span><span class="sxs-lookup"><span data-stu-id="5d677-168">4</span></span>|<span data-ttu-id="5d677-169">Le compilateur accepte uniquement la syntaxe incluse dans C# 4.0 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="5d677-169">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="5d677-170">3</span><span class="sxs-lookup"><span data-stu-id="5d677-170">3</span></span>|<span data-ttu-id="5d677-171">Le compilateur accepte uniquement la syntaxe incluse dans C# 3.0 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="5d677-171">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="5d677-172">ISO-2</span><span class="sxs-lookup"><span data-stu-id="5d677-172">ISO-2</span></span>|<span data-ttu-id="5d677-173">Le compilateur accepte uniquement la syntaxe incluse dans ISO/IEC 23270:2006 C# (2.0)</span><span class="sxs-lookup"><span data-stu-id="5d677-173">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="5d677-174">ISO-1</span><span class="sxs-lookup"><span data-stu-id="5d677-174">ISO-1</span></span>|<span data-ttu-id="5d677-175">Le compilateur accepte uniquement la syntaxe incluse dans ISO/IEC 23270:2003 C# (1.0/1.2)</span><span class="sxs-lookup"><span data-stu-id="5d677-175">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
