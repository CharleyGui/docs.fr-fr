---
title: Sélectionnez la version linguistique de Visual Basic
description: Configurer le compilateur pour effectuer une validation de syntaxe à l’aide d’une version de compilateur spécifique.
ms.date: 05/24/2018
ms.openlocfilehash: 4768d59a37d168b2883396f1dea4d0c1a0ff4ca7
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268265"
---
# <a name="select-the-visual-basic-language-version"></a><span data-ttu-id="99af5-103">Sélectionnez la version linguistique de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="99af5-103">Select the Visual Basic language version</span></span>

<span data-ttu-id="99af5-104">Le compilateur Visual Basic par défaut est la dernière version principale de la langue qui a été libérée.</span><span class="sxs-lookup"><span data-stu-id="99af5-104">The Visual Basic compiler defaults to the latest major version of the language that has been released.</span></span> <span data-ttu-id="99af5-105">Vous pouvez choisir de compiler n’importe quel projet à l’aide d’une nouvelle version intermédiaire du langage.</span><span class="sxs-lookup"><span data-stu-id="99af5-105">You may choose to compile any project using a new point release of the language.</span></span> <span data-ttu-id="99af5-106">En choisissant une version plus récente du langage, vous permettez à votre projet d’utiliser les dernières fonctionnalités de langage.</span><span class="sxs-lookup"><span data-stu-id="99af5-106">Choosing a newer version of the language enables your project to make use of the latest language features.</span></span> <span data-ttu-id="99af5-107">Dans d’autres scénarios, vous devrez peut-être vérifier qu’un projet est correctement compilé en cas d’utilisation d’une ancienne version de langage.</span><span class="sxs-lookup"><span data-stu-id="99af5-107">In other scenarios, you may need to validate that a project compiles cleanly when using an older version of the language.</span></span>

<span data-ttu-id="99af5-108">Cette fonctionnalité dissocie la décision d’installer de nouvelles versions du kit SDK et des outils dans votre environnement de développement de la décision d’incorporer de nouvelles fonctionnalités de langage dans un projet.</span><span class="sxs-lookup"><span data-stu-id="99af5-108">This capability decouples the decision to install new versions of the SDK and tools in your development environment from the decision to incorporate new language features in a project.</span></span> <span data-ttu-id="99af5-109">Vous pouvez installer la dernière version du SDK et des outils sur votre ordinateur de build.</span><span class="sxs-lookup"><span data-stu-id="99af5-109">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="99af5-110">Chaque projet peut être configuré pour utiliser une version spécifique du langage pour sa build.</span><span class="sxs-lookup"><span data-stu-id="99af5-110">Each project can be configured to use a specific version of the language for its build.</span></span>

<span data-ttu-id="99af5-111">Il existe trois façons de définir la version de langage :</span><span class="sxs-lookup"><span data-stu-id="99af5-111">There are three ways to set the language version:</span></span>

- <span data-ttu-id="99af5-112">Modifiez manuellement votre [ **.vbproj** fichier](#edit-the-vbproj-file)</span><span class="sxs-lookup"><span data-stu-id="99af5-112">Manually edit your [**.vbproj** file](#edit-the-vbproj-file)</span></span>
- <span data-ttu-id="99af5-113">Définissez la version de langage [pour plusieurs projets dans un sous-répertoire](#configure-multiple-projects)</span><span class="sxs-lookup"><span data-stu-id="99af5-113">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects)</span></span>
- <span data-ttu-id="99af5-114">Configurer le [ `-langversion` option du compilateur](#set-the-langversion-compiler-option)</span><span class="sxs-lookup"><span data-stu-id="99af5-114">Configure the [`-langversion` compiler option](#set-the-langversion-compiler-option)</span></span>

## <a name="edit-the-vbproj-file"></a><span data-ttu-id="99af5-115">Modifiez le fichier vbproj</span><span class="sxs-lookup"><span data-stu-id="99af5-115">Edit the vbproj file</span></span>

<span data-ttu-id="99af5-116">Vous pouvez définir la version de langage dans votre **.vbproj** fichier.</span><span class="sxs-lookup"><span data-stu-id="99af5-116">You can set the language version in your **.vbproj** file.</span></span> <span data-ttu-id="99af5-117">Ajoutez l’élément suivant :</span><span class="sxs-lookup"><span data-stu-id="99af5-117">Add the following element:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="99af5-118">La valeur `latest` utilise la dernière version mineure du langage Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="99af5-118">The value `latest` uses the latest minor version of the Visual Basic language.</span></span> <span data-ttu-id="99af5-119">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="99af5-119">Valid values are:</span></span>

|<span data-ttu-id="99af5-120">Value</span><span class="sxs-lookup"><span data-stu-id="99af5-120">Value</span></span>|<span data-ttu-id="99af5-121">Signification</span><span class="sxs-lookup"><span data-stu-id="99af5-121">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="99af5-122">default</span><span class="sxs-lookup"><span data-stu-id="99af5-122">default</span></span>|<span data-ttu-id="99af5-123">Le compilateur accepte toute la syntaxe de langage valide de la dernière version principale qu’il peut prendre en charge.</span><span class="sxs-lookup"><span data-stu-id="99af5-123">The compiler accepts all valid language syntax from the latest major version that it can support.</span></span>|
|<span data-ttu-id="99af5-124">9</span><span class="sxs-lookup"><span data-stu-id="99af5-124">9</span></span>|<span data-ttu-id="99af5-125">Le compilateur accepte uniquement la syntaxe qui est incluse dans Visual Basic 9.0 ou inférieure.</span><span class="sxs-lookup"><span data-stu-id="99af5-125">The compiler accepts only syntax that is included in Visual Basic 9.0 or lower.</span></span>|
|<span data-ttu-id="99af5-126">10</span><span class="sxs-lookup"><span data-stu-id="99af5-126">10</span></span>|<span data-ttu-id="99af5-127">Le compilateur accepte uniquement la syntaxe qui est incluse dans Visual Basic 10.0 ou inférieure.</span><span class="sxs-lookup"><span data-stu-id="99af5-127">The compiler accepts only syntax that is included in Visual Basic 10.0 or lower.</span></span>|
|<span data-ttu-id="99af5-128">11</span><span class="sxs-lookup"><span data-stu-id="99af5-128">11</span></span>|<span data-ttu-id="99af5-129">Le compilateur accepte uniquement la syntaxe qui est incluse dans Visual Basic 11.0 ou inférieure.</span><span class="sxs-lookup"><span data-stu-id="99af5-129">The compiler accepts only syntax that is included in Visual Basic 11.0 or lower.</span></span>|
|<span data-ttu-id="99af5-130">12</span><span class="sxs-lookup"><span data-stu-id="99af5-130">12</span></span>|<span data-ttu-id="99af5-131">Le compilateur accepte uniquement la syntaxe qui est incluse dans Visual Basic 12.0 ou inférieure.</span><span class="sxs-lookup"><span data-stu-id="99af5-131">The compiler accepts only syntax that is included in Visual Basic 12.0 or lower.</span></span>|
|<span data-ttu-id="99af5-132">14</span><span class="sxs-lookup"><span data-stu-id="99af5-132">14</span></span>|<span data-ttu-id="99af5-133">Le compilateur accepte uniquement la syntaxe qui est incluse dans Visual Basic 14.0 ou inférieure.</span><span class="sxs-lookup"><span data-stu-id="99af5-133">The compiler accepts only syntax that is included in Visual Basic 14.0 or lower.</span></span>|
|<span data-ttu-id="99af5-134">15</span><span class="sxs-lookup"><span data-stu-id="99af5-134">15</span></span>|<span data-ttu-id="99af5-135">Le compilateur accepte uniquement la syntaxe qui est incluse dans Visual Basic 15.0 ou inférieure.</span><span class="sxs-lookup"><span data-stu-id="99af5-135">The compiler accepts only syntax that is included in Visual Basic 15.0 or lower.</span></span>|
|<span data-ttu-id="99af5-136">15.3</span><span class="sxs-lookup"><span data-stu-id="99af5-136">15.3</span></span>|<span data-ttu-id="99af5-137">Le compilateur accepte uniquement la syntaxe qui est incluse dans Visual Basic 15.3 ou inférieure.</span><span class="sxs-lookup"><span data-stu-id="99af5-137">The compiler accepts only syntax that is included in Visual Basic 15.3 or lower.</span></span>|
|<span data-ttu-id="99af5-138">15.5</span><span class="sxs-lookup"><span data-stu-id="99af5-138">15.5</span></span>|<span data-ttu-id="99af5-139">Le compilateur accepte uniquement la syntaxe qui est incluse dans Visual Basic 15.5 ou inférieure.</span><span class="sxs-lookup"><span data-stu-id="99af5-139">The compiler accepts only syntax that is included in Visual Basic 15.5 or lower.</span></span>|
|<span data-ttu-id="99af5-140">15.8</span><span class="sxs-lookup"><span data-stu-id="99af5-140">15.8</span></span>|<span data-ttu-id="99af5-141">Le compilateur accepte uniquement la syntaxe qui est incluse dans Visual Basic 15.8 ou inférieure.</span><span class="sxs-lookup"><span data-stu-id="99af5-141">The compiler accepts only syntax that is included in Visual Basic 15.8 or lower.</span></span>|
|<span data-ttu-id="99af5-142">latest</span><span class="sxs-lookup"><span data-stu-id="99af5-142">latest</span></span>|<span data-ttu-id="99af5-143">Le compilateur accepte toute la syntaxe de langage valide qu’il peut prendre en charge.</span><span class="sxs-lookup"><span data-stu-id="99af5-143">The compiler accepts all valid language syntax that it can support.</span></span>|

<span data-ttu-id="99af5-144">Les chaînes spéciales `default` et `latest` définissent respectivement la dernière version majeure et la dernière version mineure du langage installées sur l’ordinateur de build.</span><span class="sxs-lookup"><span data-stu-id="99af5-144">The special strings `default` and `latest` resolve to the latest major and minor language versions installed on the build machine, respectively.</span></span>

## <a name="configure-multiple-projects"></a><span data-ttu-id="99af5-145">Configurer plusieurs projets</span><span class="sxs-lookup"><span data-stu-id="99af5-145">Configure multiple projects</span></span>

<span data-ttu-id="99af5-146">Vous pouvez créer un fichier **Directory.build.props** contenant l’élément `<LangVersion>` pour configurer plusieurs répertoires.</span><span class="sxs-lookup"><span data-stu-id="99af5-146">You can create a **Directory.build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="99af5-147">En règle générale, vous faites cela dans votre répertoire de solution.</span><span class="sxs-lookup"><span data-stu-id="99af5-147">You typically do that in your solution directory.</span></span> <span data-ttu-id="99af5-148">Ajoutez ce qui suit à un fichier **Directory.build.props** dans votre répertoire de solution :</span><span class="sxs-lookup"><span data-stu-id="99af5-148">Add the following to a **Directory.build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>15.5</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="99af5-149">Maintenant, builds dans chaque sous-répertoire du répertoire contenant ce fichier utilise la syntaxe de la version 15.5 Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="99af5-149">Now, builds in every subdirectory of the directory containing that file will use Visual Basic version 15.5 syntax.</span></span> <span data-ttu-id="99af5-150">Pour plus d’informations, consultez l’article sur [Personnaliser votre build](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="99af5-150">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="set-the-langversion-compiler-option"></a><span data-ttu-id="99af5-151">Définir l’option de compilateur langversion</span><span class="sxs-lookup"><span data-stu-id="99af5-151">Set the langversion compiler option</span></span>

<span data-ttu-id="99af5-152">Vous pouvez utiliser l’option de ligne de commande `-langversion`.</span><span class="sxs-lookup"><span data-stu-id="99af5-152">You can use the `-langversion` command-line option.</span></span> <span data-ttu-id="99af5-153">Pour plus d’informations, consultez l’article sur l’option de compilateur [-langversion](../reference/command-line-compiler/langversion.md).</span><span class="sxs-lookup"><span data-stu-id="99af5-153">For more information, see the article on the [-langversion](../reference/command-line-compiler/langversion.md) compiler option.</span></span> <span data-ttu-id="99af5-154">Vous pouvez voir une liste des valeurs valides en tapant `vbc -langversion:?` .</span><span class="sxs-lookup"><span data-stu-id="99af5-154">You can see a list of the valid values by typing  `vbc -langversion:?` .</span></span>
