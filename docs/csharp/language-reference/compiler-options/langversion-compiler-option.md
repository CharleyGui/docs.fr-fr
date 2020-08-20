---
title: -langversion (Options du compilateur C#)
ms.date: 05/20/2020
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.custom: updateeachrelease
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: fd05802008a20267fea54f14bae4c8deb0e21c65
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656205"
---
# <a name="-langversion-c-compiler-options"></a><span data-ttu-id="bb446-102">-langversion (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="bb446-102">-langversion (C# Compiler Options)</span></span>

<span data-ttu-id="bb446-103">Force le compilateur à accepter uniquement la syntaxe incluse dans la spécification choisie du langage C#.</span><span class="sxs-lookup"><span data-stu-id="bb446-103">Causes the compiler to accept only syntax that is included in the chosen C# language specification.</span></span>

## <a name="syntax"></a><span data-ttu-id="bb446-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb446-104">Syntax</span></span>

```console
-langversion:option
```

## <a name="arguments"></a><span data-ttu-id="bb446-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="bb446-105">Arguments</span></span>

`option`

<span data-ttu-id="bb446-106">Les valeurs suivantes sont valides :</span><span class="sxs-lookup"><span data-stu-id="bb446-106">The following values are valid:</span></span>

[!INCLUDE [lang-versions-table](../includes/langversion-table.md)]

<span data-ttu-id="bb446-107">La version du langage par défaut dépend du framework cible de votre application et de la version installée du kit SDK ou de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bb446-107">The default language version depends on the target framework for your application and the version of the SDK or Visual Studio installed.</span></span> <span data-ttu-id="bb446-108">Ces règles sont définies dans l’article [configuration de la version linguistique](../configure-language-version.md#defaults) .</span><span class="sxs-lookup"><span data-stu-id="bb446-108">Those rules are defined in the [configuring the language version](../configure-language-version.md#defaults) article.</span></span>

## <a name="remarks"></a><span data-ttu-id="bb446-109">Notes</span><span class="sxs-lookup"><span data-stu-id="bb446-109">Remarks</span></span>

<span data-ttu-id="bb446-110">Les métadonnées référencées par votre application C# ne sont pas visées par l’option de compilateur **-langversion**.</span><span class="sxs-lookup"><span data-stu-id="bb446-110">Metadata referenced by your C# application is not subject to **-langversion** compiler option.</span></span>

<span data-ttu-id="bb446-111">Sachant que chaque version du compilateur C# contient des extensions de la spécification du langage, **-langversion** ne vous offre pas les fonctionnalités équivalentes d’une version antérieure du compilateur.</span><span class="sxs-lookup"><span data-stu-id="bb446-111">Because each version of the C# compiler contains extensions to the language specification, **-langversion** does not give you the equivalent functionality of an earlier version of the compiler.</span></span>

<span data-ttu-id="bb446-112">De plus, alors que les mises à jour de la version de C# coïncident généralement avec les versions principales du .NET Framework, la nouvelle syntaxe et les nouvelles fonctionnalités ne sont pas nécessairement liées à cette version spécifique du framework.</span><span class="sxs-lookup"><span data-stu-id="bb446-112">Additionally, while C# version updates generally coincide with major .NET Framework releases, the new syntax and features are not necessarily tied to that specific framework version.</span></span> <span data-ttu-id="bb446-113">Alors que les nouvelles fonctionnalités nécessitent une nouvelle mise à jour du compilateur, publiée en même temps que la révision de C#, chaque fonctionnalité spécifique a ses propres exigences minimales relatives à l’API .NET ou au Common Language Runtime pour pouvoir s’exécuter sur des frameworks de bas niveau en incluant des packages NuGet ou d’autres bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="bb446-113">While the new features definitely require a new compiler update that is also released alongside the C# revision, each specific feature has its own minimum .NET API or common language runtime requirements that may allow it to run on downlevel frameworks by including NuGet packages or other libraries.</span></span>

<span data-ttu-id="bb446-114">Quel que soit le paramètre **-langversion** utilisé, utilisez la version actuelle du Common Language Runtime pour créer votre fichier. exe ou. dll.</span><span class="sxs-lookup"><span data-stu-id="bb446-114">Regardless of which **-langversion** setting you use, use the current version of the common language runtime to create your .exe or .dll.</span></span> <span data-ttu-id="bb446-115">Les assemblys friend et [-moduleassemblyname (option du compilateur C#)](./moduleassemblyname-compiler-option.md), qui fonctionnent sous **-langversion : ISO-1**, sont une exception.</span><span class="sxs-lookup"><span data-stu-id="bb446-115">One exception is friend assemblies and [-moduleassemblyname (C# Compiler Option)](./moduleassemblyname-compiler-option.md), which work under **-langversion:ISO-1**.</span></span>

<span data-ttu-id="bb446-116">Pour d’autres façons de spécifier la version du langage C#, consultez l’article [Sélectionner la version du langage c#](../configure-language-version.md) .</span><span class="sxs-lookup"><span data-stu-id="bb446-116">For other ways to specify the C# language version, see the [Select the C# language version](../configure-language-version.md) article.</span></span>

<span data-ttu-id="bb446-117">Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="bb446-117">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bb446-118">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="bb446-118">C# language specification</span></span>

| <span data-ttu-id="bb446-119">Version</span><span class="sxs-lookup"><span data-stu-id="bb446-119">Version</span></span>          | <span data-ttu-id="bb446-120">Lien</span><span class="sxs-lookup"><span data-stu-id="bb446-120">Link</span></span>                       | <span data-ttu-id="bb446-121">Description</span><span class="sxs-lookup"><span data-stu-id="bb446-121">Description</span></span>                                                             |
|------------------|----------------------------|-------------------------------------------------------------------------|
| <span data-ttu-id="bb446-122">C# 7.0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="bb446-122">C# 7.0 and later</span></span> |                            | <span data-ttu-id="bb446-123">Actuellement non disponible</span><span class="sxs-lookup"><span data-stu-id="bb446-123">Not currently available</span></span>                                                 |
| <span data-ttu-id="bb446-124">C# 6.0</span><span class="sxs-lookup"><span data-stu-id="bb446-124">C# 6.0</span></span>           | <span data-ttu-id="bb446-125">[Lien][csharp-6]</span><span class="sxs-lookup"><span data-stu-id="bb446-125">[Link][csharp-6]</span></span>           | <span data-ttu-id="bb446-126">Spécification du langage C# version 6 - Ébauche non officielle : .NET Foundation</span><span class="sxs-lookup"><span data-stu-id="bb446-126">C# Language Specification Version 6 - Unofficial Draft: .NET Foundation</span></span> |
| <span data-ttu-id="bb446-127">C# 5.0</span><span class="sxs-lookup"><span data-stu-id="bb446-127">C# 5.0</span></span>           | <span data-ttu-id="bb446-128">[Télécharger le PDF][csharp-5]</span><span class="sxs-lookup"><span data-stu-id="bb446-128">[Download PDF][csharp-5]</span></span>   | <span data-ttu-id="bb446-129">Norme ECMA-334 5e édition</span><span class="sxs-lookup"><span data-stu-id="bb446-129">Standard ECMA-334 5th Edition</span></span>                                           |
| <span data-ttu-id="bb446-130">C# 3.0</span><span class="sxs-lookup"><span data-stu-id="bb446-130">C# 3.0</span></span>           | <span data-ttu-id="bb446-131">[Télécharger DOC][csharp-3]</span><span class="sxs-lookup"><span data-stu-id="bb446-131">[Download DOC][csharp-3]</span></span>   | <span data-ttu-id="bb446-132">Spécification du langage C# version 3.0 : Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="bb446-132">C# Language Specification Version 3.0: Microsoft Corporation</span></span>            |
| <span data-ttu-id="bb446-133">C# 2.0</span><span class="sxs-lookup"><span data-stu-id="bb446-133">C# 2.0</span></span>           | <span data-ttu-id="bb446-134">[Télécharger le PDF][csharp-2]</span><span class="sxs-lookup"><span data-stu-id="bb446-134">[Download PDF][csharp-2]</span></span>   | <span data-ttu-id="bb446-135">Norme ECMA-334 4e édition</span><span class="sxs-lookup"><span data-stu-id="bb446-135">Standard ECMA-334 4th Edition</span></span>                                           |
| <span data-ttu-id="bb446-136">C# 1.2</span><span class="sxs-lookup"><span data-stu-id="bb446-136">C# 1.2</span></span>           | <span data-ttu-id="bb446-137">[Télécharger DOC][csharp-1.2]</span><span class="sxs-lookup"><span data-stu-id="bb446-137">[Download DOC][csharp-1.2]</span></span> | <span data-ttu-id="bb446-138">Spécification du langage C# version 1.2 : Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="bb446-138">C# Language Specification Version 1.2: Microsoft Corporation</span></span>            |
| <span data-ttu-id="bb446-139">C# 1.0</span><span class="sxs-lookup"><span data-stu-id="bb446-139">C# 1.0</span></span>           | <span data-ttu-id="bb446-140">[Télécharger DOC][csharp-1]</span><span class="sxs-lookup"><span data-stu-id="bb446-140">[Download DOC][csharp-1]</span></span>   | <span data-ttu-id="bb446-141">Spécification du langage C# version 1.0 : Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="bb446-141">C# Language Specification Version 1.0: Microsoft Corporation</span></span>            |

[csharp-6]: /dotnet/csharp/language-reference/language-specification/introduction
[csharp-5]: https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf
[csharp-3]: https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc
[csharp-2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf
[csharp-1.2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf
[csharp-1]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a><span data-ttu-id="bb446-142">Version minimale du kit de développement logiciel nécessaire pour prendre en charge toutes les fonctionnalités de langage</span><span class="sxs-lookup"><span data-stu-id="bb446-142">Minimum SDK version needed to support all language features</span></span>

<span data-ttu-id="bb446-143">Le tableau suivant répertorie les versions minimales du kit de développement logiciel (SDK) avec le compilateur C# qui prend en charge la version de langue correspondante :</span><span class="sxs-lookup"><span data-stu-id="bb446-143">The following table lists the minimum versions of the SDK with the C# compiler that supports the corresponding language version:</span></span>

| <span data-ttu-id="bb446-144">Version C#</span><span class="sxs-lookup"><span data-stu-id="bb446-144">C# version</span></span> | <span data-ttu-id="bb446-145">Version minimale du kit de développement logiciel</span><span class="sxs-lookup"><span data-stu-id="bb446-145">Minimum SDK version</span></span>                                                                  |
|------------|--------------------------------------------------------------------------------------|
| <span data-ttu-id="bb446-146">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="bb446-146">C# 8.0</span></span>     | <span data-ttu-id="bb446-147">Microsoft Visual Studio/Build Tools 2019, version 16,3 ou .NET Core 3,0 SDK</span><span class="sxs-lookup"><span data-stu-id="bb446-147">Microsoft Visual Studio/Build Tools 2019, version 16.3, or .NET Core 3.0 SDK</span></span>         |
| <span data-ttu-id="bb446-148">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="bb446-148">C# 7.3</span></span>     | <span data-ttu-id="bb446-149">Microsoft Visual Studio/Build Tools 2017, version 15.7</span><span class="sxs-lookup"><span data-stu-id="bb446-149">Microsoft Visual Studio/Build Tools 2017, version 15.7</span></span>                               |
| <span data-ttu-id="bb446-150">C# 7.2</span><span class="sxs-lookup"><span data-stu-id="bb446-150">C# 7.2</span></span>     | <span data-ttu-id="bb446-151">Microsoft Visual Studio/Build Tools 2017, version 15.5</span><span class="sxs-lookup"><span data-stu-id="bb446-151">Microsoft Visual Studio/Build Tools 2017, version 15.5</span></span>                               |
| <span data-ttu-id="bb446-152">C# 7.1</span><span class="sxs-lookup"><span data-stu-id="bb446-152">C# 7.1</span></span>     | <span data-ttu-id="bb446-153">Microsoft Visual Studio/Build Tools 2017, version 15.3</span><span class="sxs-lookup"><span data-stu-id="bb446-153">Microsoft Visual Studio/Build Tools 2017, version 15.3</span></span>                               |
| <span data-ttu-id="bb446-154">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="bb446-154">C# 7.0</span></span>     | <span data-ttu-id="bb446-155">Microsoft Visual Studio/Build Tools 2017</span><span class="sxs-lookup"><span data-stu-id="bb446-155">Microsoft Visual Studio/Build Tools 2017</span></span>                                             |
| <span data-ttu-id="bb446-156">C# 6</span><span class="sxs-lookup"><span data-stu-id="bb446-156">C# 6</span></span>       | <span data-ttu-id="bb446-157">Microsoft Visual Studio/Build Tools 2015</span><span class="sxs-lookup"><span data-stu-id="bb446-157">Microsoft Visual Studio/Build Tools 2015</span></span>                                             |
| <span data-ttu-id="bb446-158">C# 5</span><span class="sxs-lookup"><span data-stu-id="bb446-158">C# 5</span></span>       | <span data-ttu-id="bb446-159">Microsoft Visual Studio/Build Tools 2012 ou compilateur .NET Framework 4.5 groupé</span><span class="sxs-lookup"><span data-stu-id="bb446-159">Microsoft Visual Studio/Build Tools 2012 or bundled .NET Framework 4.5 compiler</span></span>      |
| <span data-ttu-id="bb446-160">C# 4</span><span class="sxs-lookup"><span data-stu-id="bb446-160">C# 4</span></span>       | <span data-ttu-id="bb446-161">Microsoft Visual Studio/Build Tools 2010 ou compilateur .NET Framework 4.0 groupé</span><span class="sxs-lookup"><span data-stu-id="bb446-161">Microsoft Visual Studio/Build Tools 2010 or bundled .NET Framework 4.0 compiler</span></span>      |
| <span data-ttu-id="bb446-162">C# 3</span><span class="sxs-lookup"><span data-stu-id="bb446-162">C# 3</span></span>       | <span data-ttu-id="bb446-163">Microsoft Visual Studio/Build Tools 2008 ou compilateur .NET Framework 3.5 groupé</span><span class="sxs-lookup"><span data-stu-id="bb446-163">Microsoft Visual Studio/Build Tools 2008 or bundled .NET Framework 3.5 compiler</span></span>      |
| <span data-ttu-id="bb446-164">C# 2</span><span class="sxs-lookup"><span data-stu-id="bb446-164">C# 2</span></span>       | <span data-ttu-id="bb446-165">Microsoft Visual Studio/Build Tools 2005 ou compilateur .NET Framework 2.0 groupé</span><span class="sxs-lookup"><span data-stu-id="bb446-165">Microsoft Visual Studio/Build Tools 2005 or bundled .NET Framework 2.0 compiler</span></span>      |
| <span data-ttu-id="bb446-166">C# 1.0/1.2</span><span class="sxs-lookup"><span data-stu-id="bb446-166">C# 1.0/1.2</span></span> | <span data-ttu-id="bb446-167">Microsoft Visual Studio/Build Tools .NET 2002 ou regroupé .NET Framework 1,0 du compilateur</span><span class="sxs-lookup"><span data-stu-id="bb446-167">Microsoft Visual Studio/Build Tools .NET 2002 or bundled .NET Framework 1.0 compiler</span></span> |

## <a name="see-also"></a><span data-ttu-id="bb446-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb446-168">See also</span></span>

- [<span data-ttu-id="bb446-169">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="bb446-169">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="bb446-170">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="bb446-170">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
