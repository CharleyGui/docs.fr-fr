---
description: -langversion (Options du compilateur C#)
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
ms.openlocfilehash: b0e966bcc87303c0a7c2199fbfac743b22481424
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125473"
---
# <a name="-langversion-c-compiler-options"></a><span data-ttu-id="46c07-103">-langversion (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="46c07-103">-langversion (C# Compiler Options)</span></span>

<span data-ttu-id="46c07-104">Force le compilateur à accepter uniquement la syntaxe incluse dans la spécification choisie du langage C#.</span><span class="sxs-lookup"><span data-stu-id="46c07-104">Causes the compiler to accept only syntax that is included in the chosen C# language specification.</span></span>

## <a name="syntax"></a><span data-ttu-id="46c07-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46c07-105">Syntax</span></span>

```console
-langversion:option
```

## <a name="arguments"></a><span data-ttu-id="46c07-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="46c07-106">Arguments</span></span>

`option`

<span data-ttu-id="46c07-107">Les valeurs suivantes sont valides :</span><span class="sxs-lookup"><span data-stu-id="46c07-107">The following values are valid:</span></span>

[!INCLUDE [lang-versions-table](../includes/langversion-table.md)]

<span data-ttu-id="46c07-108">La version du langage par défaut dépend du framework cible de votre application et de la version installée du kit SDK ou de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="46c07-108">The default language version depends on the target framework for your application and the version of the SDK or Visual Studio installed.</span></span> <span data-ttu-id="46c07-109">Ces règles sont définies dans l’article [configuration de la version linguistique](../configure-language-version.md#defaults) .</span><span class="sxs-lookup"><span data-stu-id="46c07-109">Those rules are defined in the [configuring the language version](../configure-language-version.md#defaults) article.</span></span>

## <a name="remarks"></a><span data-ttu-id="46c07-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="46c07-110">Remarks</span></span>

<span data-ttu-id="46c07-111">Les métadonnées référencées par votre application C# ne sont pas visées par l’option de compilateur **-langversion**.</span><span class="sxs-lookup"><span data-stu-id="46c07-111">Metadata referenced by your C# application is not subject to **-langversion** compiler option.</span></span>

<span data-ttu-id="46c07-112">Sachant que chaque version du compilateur C# contient des extensions de la spécification du langage, **-langversion** ne vous offre pas les fonctionnalités équivalentes d’une version antérieure du compilateur.</span><span class="sxs-lookup"><span data-stu-id="46c07-112">Because each version of the C# compiler contains extensions to the language specification, **-langversion** does not give you the equivalent functionality of an earlier version of the compiler.</span></span>

<span data-ttu-id="46c07-113">De plus, alors que les mises à jour de la version de C# coïncident généralement avec les versions principales du .NET Framework, la nouvelle syntaxe et les nouvelles fonctionnalités ne sont pas nécessairement liées à cette version spécifique du framework.</span><span class="sxs-lookup"><span data-stu-id="46c07-113">Additionally, while C# version updates generally coincide with major .NET Framework releases, the new syntax and features are not necessarily tied to that specific framework version.</span></span> <span data-ttu-id="46c07-114">Alors que les nouvelles fonctionnalités nécessitent une nouvelle mise à jour du compilateur, publiée en même temps que la révision de C#, chaque fonctionnalité spécifique a ses propres exigences minimales relatives à l’API .NET ou au Common Language Runtime pour pouvoir s’exécuter sur des frameworks de bas niveau en incluant des packages NuGet ou d’autres bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="46c07-114">While the new features definitely require a new compiler update that is also released alongside the C# revision, each specific feature has its own minimum .NET API or common language runtime requirements that may allow it to run on downlevel frameworks by including NuGet packages or other libraries.</span></span>

<span data-ttu-id="46c07-115">Quel que soit le paramètre **-langversion** utilisé, utilisez la version actuelle du Common Language Runtime pour créer votre fichier. exe ou. dll.</span><span class="sxs-lookup"><span data-stu-id="46c07-115">Regardless of which **-langversion** setting you use, use the current version of the common language runtime to create your .exe or .dll.</span></span> <span data-ttu-id="46c07-116">Les assemblys friend et [-moduleassemblyname (option du compilateur C#)](./moduleassemblyname-compiler-option.md), qui fonctionnent sous **-langversion : ISO-1**, sont une exception.</span><span class="sxs-lookup"><span data-stu-id="46c07-116">One exception is friend assemblies and [-moduleassemblyname (C# Compiler Option)](./moduleassemblyname-compiler-option.md), which work under **-langversion:ISO-1**.</span></span>

<span data-ttu-id="46c07-117">Pour d’autres façons de spécifier la version du langage C#, consultez l’article [Sélectionner la version du langage c#](../configure-language-version.md) .</span><span class="sxs-lookup"><span data-stu-id="46c07-117">For other ways to specify the C# language version, see the [Select the C# language version](../configure-language-version.md) article.</span></span>

<span data-ttu-id="46c07-118">Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="46c07-118">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="46c07-119">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="46c07-119">C# language specification</span></span>

| <span data-ttu-id="46c07-120">Version</span><span class="sxs-lookup"><span data-stu-id="46c07-120">Version</span></span>          | <span data-ttu-id="46c07-121">Lien</span><span class="sxs-lookup"><span data-stu-id="46c07-121">Link</span></span>                       | <span data-ttu-id="46c07-122">Description</span><span class="sxs-lookup"><span data-stu-id="46c07-122">Description</span></span>                                                             |
|------------------|----------------------------|-------------------------------------------------------------------------|
| <span data-ttu-id="46c07-123">C# 7.0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="46c07-123">C# 7.0 and later</span></span> |                            | <span data-ttu-id="46c07-124">Actuellement non disponible</span><span class="sxs-lookup"><span data-stu-id="46c07-124">Not currently available</span></span>                                                 |
| <span data-ttu-id="46c07-125">C# 6.0</span><span class="sxs-lookup"><span data-stu-id="46c07-125">C# 6.0</span></span>           | <span data-ttu-id="46c07-126">[Lien][csharp-6]</span><span class="sxs-lookup"><span data-stu-id="46c07-126">[Link][csharp-6]</span></span>           | <span data-ttu-id="46c07-127">Spécification du langage C# version 6 - Ébauche non officielle : .NET Foundation</span><span class="sxs-lookup"><span data-stu-id="46c07-127">C# Language Specification Version 6 - Unofficial Draft: .NET Foundation</span></span> |
| <span data-ttu-id="46c07-128">C# 5.0</span><span class="sxs-lookup"><span data-stu-id="46c07-128">C# 5.0</span></span>           | <span data-ttu-id="46c07-129">[Télécharger le PDF][csharp-5]</span><span class="sxs-lookup"><span data-stu-id="46c07-129">[Download PDF][csharp-5]</span></span>   | <span data-ttu-id="46c07-130">Norme ECMA-334 5e édition</span><span class="sxs-lookup"><span data-stu-id="46c07-130">Standard ECMA-334 5th Edition</span></span>                                           |
| <span data-ttu-id="46c07-131">C# 3.0</span><span class="sxs-lookup"><span data-stu-id="46c07-131">C# 3.0</span></span>           | <span data-ttu-id="46c07-132">[Télécharger DOC][csharp-3]</span><span class="sxs-lookup"><span data-stu-id="46c07-132">[Download DOC][csharp-3]</span></span>   | <span data-ttu-id="46c07-133">Spécification du langage C# version 3.0 : Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="46c07-133">C# Language Specification Version 3.0: Microsoft Corporation</span></span>            |
| <span data-ttu-id="46c07-134">C# 2.0</span><span class="sxs-lookup"><span data-stu-id="46c07-134">C# 2.0</span></span>           | <span data-ttu-id="46c07-135">[Télécharger le PDF][csharp-2]</span><span class="sxs-lookup"><span data-stu-id="46c07-135">[Download PDF][csharp-2]</span></span>   | <span data-ttu-id="46c07-136">Norme ECMA-334 4e édition</span><span class="sxs-lookup"><span data-stu-id="46c07-136">Standard ECMA-334 4th Edition</span></span>                                           |
| <span data-ttu-id="46c07-137">C# 1.2</span><span class="sxs-lookup"><span data-stu-id="46c07-137">C# 1.2</span></span>           | <span data-ttu-id="46c07-138">[Télécharger DOC][csharp-1.2]</span><span class="sxs-lookup"><span data-stu-id="46c07-138">[Download DOC][csharp-1.2]</span></span> | <span data-ttu-id="46c07-139">Spécification du langage C# version 1.2 : Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="46c07-139">C# Language Specification Version 1.2: Microsoft Corporation</span></span>            |
| <span data-ttu-id="46c07-140">C# 1.0</span><span class="sxs-lookup"><span data-stu-id="46c07-140">C# 1.0</span></span>           | <span data-ttu-id="46c07-141">[Télécharger DOC][csharp-1]</span><span class="sxs-lookup"><span data-stu-id="46c07-141">[Download DOC][csharp-1]</span></span>   | <span data-ttu-id="46c07-142">Spécification du langage C# version 1.0 : Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="46c07-142">C# Language Specification Version 1.0: Microsoft Corporation</span></span>            |

[csharp-6]: /dotnet/csharp/language-reference/language-specification/introduction
[csharp-5]: https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf
[csharp-3]: https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc
[csharp-2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf
[csharp-1.2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf
[csharp-1]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a><span data-ttu-id="46c07-143">Version minimale du kit de développement logiciel nécessaire pour prendre en charge toutes les fonctionnalités de langage</span><span class="sxs-lookup"><span data-stu-id="46c07-143">Minimum SDK version needed to support all language features</span></span>

<span data-ttu-id="46c07-144">Le tableau suivant répertorie les versions minimales du kit de développement logiciel (SDK) avec le compilateur C# qui prend en charge la version de langue correspondante :</span><span class="sxs-lookup"><span data-stu-id="46c07-144">The following table lists the minimum versions of the SDK with the C# compiler that supports the corresponding language version:</span></span>

| <span data-ttu-id="46c07-145">Version C#</span><span class="sxs-lookup"><span data-stu-id="46c07-145">C# version</span></span> | <span data-ttu-id="46c07-146">Version minimale du kit de développement logiciel</span><span class="sxs-lookup"><span data-stu-id="46c07-146">Minimum SDK version</span></span>                                                                  |
|------------|--------------------------------------------------------------------------------------|
| <span data-ttu-id="46c07-147">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="46c07-147">C# 8.0</span></span>     | <span data-ttu-id="46c07-148">Microsoft Visual Studio/Build Tools 2019, version 16,3 ou .NET Core 3,0 SDK</span><span class="sxs-lookup"><span data-stu-id="46c07-148">Microsoft Visual Studio/Build Tools 2019, version 16.3, or .NET Core 3.0 SDK</span></span>         |
| <span data-ttu-id="46c07-149">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="46c07-149">C# 7.3</span></span>     | <span data-ttu-id="46c07-150">Microsoft Visual Studio/Build Tools 2017, version 15.7</span><span class="sxs-lookup"><span data-stu-id="46c07-150">Microsoft Visual Studio/Build Tools 2017, version 15.7</span></span>                               |
| <span data-ttu-id="46c07-151">C# 7.2</span><span class="sxs-lookup"><span data-stu-id="46c07-151">C# 7.2</span></span>     | <span data-ttu-id="46c07-152">Microsoft Visual Studio/Build Tools 2017, version 15.5</span><span class="sxs-lookup"><span data-stu-id="46c07-152">Microsoft Visual Studio/Build Tools 2017, version 15.5</span></span>                               |
| <span data-ttu-id="46c07-153">C# 7.1</span><span class="sxs-lookup"><span data-stu-id="46c07-153">C# 7.1</span></span>     | <span data-ttu-id="46c07-154">Microsoft Visual Studio/Build Tools 2017, version 15.3</span><span class="sxs-lookup"><span data-stu-id="46c07-154">Microsoft Visual Studio/Build Tools 2017, version 15.3</span></span>                               |
| <span data-ttu-id="46c07-155">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="46c07-155">C# 7.0</span></span>     | <span data-ttu-id="46c07-156">Microsoft Visual Studio/Build Tools 2017</span><span class="sxs-lookup"><span data-stu-id="46c07-156">Microsoft Visual Studio/Build Tools 2017</span></span>                                             |
| <span data-ttu-id="46c07-157">C# 6</span><span class="sxs-lookup"><span data-stu-id="46c07-157">C# 6</span></span>       | <span data-ttu-id="46c07-158">Microsoft Visual Studio/Build Tools 2015</span><span class="sxs-lookup"><span data-stu-id="46c07-158">Microsoft Visual Studio/Build Tools 2015</span></span>                                             |
| <span data-ttu-id="46c07-159">C# 5</span><span class="sxs-lookup"><span data-stu-id="46c07-159">C# 5</span></span>       | <span data-ttu-id="46c07-160">Microsoft Visual Studio/Build Tools 2012 ou compilateur .NET Framework 4.5 groupé</span><span class="sxs-lookup"><span data-stu-id="46c07-160">Microsoft Visual Studio/Build Tools 2012 or bundled .NET Framework 4.5 compiler</span></span>      |
| <span data-ttu-id="46c07-161">C# 4</span><span class="sxs-lookup"><span data-stu-id="46c07-161">C# 4</span></span>       | <span data-ttu-id="46c07-162">Microsoft Visual Studio/Build Tools 2010 ou compilateur .NET Framework 4.0 groupé</span><span class="sxs-lookup"><span data-stu-id="46c07-162">Microsoft Visual Studio/Build Tools 2010 or bundled .NET Framework 4.0 compiler</span></span>      |
| <span data-ttu-id="46c07-163">C# 3</span><span class="sxs-lookup"><span data-stu-id="46c07-163">C# 3</span></span>       | <span data-ttu-id="46c07-164">Microsoft Visual Studio/Build Tools 2008 ou compilateur .NET Framework 3.5 groupé</span><span class="sxs-lookup"><span data-stu-id="46c07-164">Microsoft Visual Studio/Build Tools 2008 or bundled .NET Framework 3.5 compiler</span></span>      |
| <span data-ttu-id="46c07-165">C# 2</span><span class="sxs-lookup"><span data-stu-id="46c07-165">C# 2</span></span>       | <span data-ttu-id="46c07-166">Microsoft Visual Studio/Build Tools 2005 ou compilateur .NET Framework 2.0 groupé</span><span class="sxs-lookup"><span data-stu-id="46c07-166">Microsoft Visual Studio/Build Tools 2005 or bundled .NET Framework 2.0 compiler</span></span>      |
| <span data-ttu-id="46c07-167">C# 1.0/1.2</span><span class="sxs-lookup"><span data-stu-id="46c07-167">C# 1.0/1.2</span></span> | <span data-ttu-id="46c07-168">Microsoft Visual Studio/Build Tools .NET 2002 ou regroupé .NET Framework 1,0 du compilateur</span><span class="sxs-lookup"><span data-stu-id="46c07-168">Microsoft Visual Studio/Build Tools .NET 2002 or bundled .NET Framework 1.0 compiler</span></span> |

## <a name="see-also"></a><span data-ttu-id="46c07-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46c07-169">See also</span></span>

- [<span data-ttu-id="46c07-170">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="46c07-170">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="46c07-171">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="46c07-171">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
