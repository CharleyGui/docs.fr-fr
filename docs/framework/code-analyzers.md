---
title: Analyseurs de code pour .NET Framework
titleSuffix: ''
description: Découvrez comment utiliser les analyseurs dans le package des analyseurs de .NET Framework pour rechercher et résoudre les problèmes dans votre code.
author: billwagner
ms.author: wiwagn
ms.date: 10/23/2020
ms.openlocfilehash: 69dfbc9f9645c7f602ffbce46308b241c119fd96
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687903"
---
# <a name="code-analysis"></a><span data-ttu-id="e260a-103">Analyse du code</span><span class="sxs-lookup"><span data-stu-id="e260a-103">Code analysis</span></span>

<span data-ttu-id="e260a-104">Vous pouvez utiliser des analyseurs de code pour rechercher des problèmes potentiels dans votre code d’application .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e260a-104">You can use code analyzers to find potential issues in your .NET Framework application code.</span></span> <span data-ttu-id="e260a-105">Les analyseurs détectent les problèmes potentiels et suggèrent des correctifs pour eux.</span><span class="sxs-lookup"><span data-stu-id="e260a-105">The analyzers find potential issues and suggest fixes for them.</span></span>

<span data-ttu-id="e260a-106">Les analyseurs de code basés sur Roslyn s’exécutent de manière interactive dans Visual Studio lorsque vous écrivez votre code ou dans le cadre d’une build d’intégration continue.</span><span class="sxs-lookup"><span data-stu-id="e260a-106">Roslyn-based code analyzers run interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="e260a-107">Vous devez ajouter les analyseurs à votre projet le plus tôt possible dans le cycle de développement.</span><span class="sxs-lookup"><span data-stu-id="e260a-107">You should add the analyzers to your project as early as possible in the development cycle.</span></span> <span data-ttu-id="e260a-108">Plus tôt vous trouvez les problèmes potentiels dans votre code, plus ils sont faciles à corriger.</span><span class="sxs-lookup"><span data-stu-id="e260a-108">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="e260a-109">Les analyseurs signalent les problèmes dans le code existant et avertissent les nouveaux problèmes au fur et à mesure que vous continuez le développement.</span><span class="sxs-lookup"><span data-stu-id="e260a-109">The analyzers flag issues in existing code and warn about new issues as you continue development.</span></span>

## <a name="install-and-configure-analyzers"></a><span data-ttu-id="e260a-110">Installer et configurer des analyseurs</span><span class="sxs-lookup"><span data-stu-id="e260a-110">Install and configure analyzers</span></span>

<span data-ttu-id="e260a-111">L’Analyseur .NET Framework est livré dans le package NuGet [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/).</span><span class="sxs-lookup"><span data-stu-id="e260a-111">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="e260a-112">Ce package fournit des analyseurs spécifiques aux API .NET Framework, qui incluent des analyseurs de sécurité.</span><span class="sxs-lookup"><span data-stu-id="e260a-112">This package provides analyzers that are specific to .NET Framework APIs, which includes security analyzers.</span></span> <span data-ttu-id="e260a-113">Le package est inclus dans le [package Microsoft. CodeAnalysis. FxCopAnalyzers.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)par conséquent, si vous installez ce package, il n’est pas nécessaire d’installer les analyseurs de .NET Framework séparément.</span><span class="sxs-lookup"><span data-stu-id="e260a-113">The package is included with the [Microsoft.CodeAnalysis.FxCopAnalyzers package](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), so if you install that package, there's no need to install the .NET Framework analyzers separately.</span></span>

<span data-ttu-id="e260a-114">Installez le package NuGet sur chaque projet où vous souhaitez que les analyseurs s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="e260a-114">Install the NuGet package on every project where you want the analyzers to run.</span></span> <span data-ttu-id="e260a-115">Il suffit qu’un seul développeur les ajoute au projet.</span><span class="sxs-lookup"><span data-stu-id="e260a-115">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="e260a-116">Le package de l’analyseur est une dépendance de projet et il s’exécute sur la machine de chaque développeur une fois qu’il dispose de la solution mise à jour.</span><span class="sxs-lookup"><span data-stu-id="e260a-116">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="e260a-117">Pour installer le package, cliquez avec le bouton droit sur le projet, puis sélectionnez « gérer les dépendances ».</span><span class="sxs-lookup"><span data-stu-id="e260a-117">To install the package, right-click on the project, and select "Manage Dependencies".</span></span> <span data-ttu-id="e260a-118">Dans l’Explorateur NuGet, recherchez « Microsoft. NETFramework. Analyzers ».</span><span class="sxs-lookup"><span data-stu-id="e260a-118">From the NuGet explorer, search for "Microsoft.NetFramework.Analyzers".</span></span> <span data-ttu-id="e260a-119">Installez la dernière version stable dans tous les projets de votre solution.</span><span class="sxs-lookup"><span data-stu-id="e260a-119">Install the latest stable version in all projects in your solution.</span></span>

## <a name="use-the-analyzers"></a><span data-ttu-id="e260a-120">Utiliser les analyseurs</span><span class="sxs-lookup"><span data-stu-id="e260a-120">Use the analyzers</span></span>

<span data-ttu-id="e260a-121">Une fois le package NuGet installé, générez votre solution.</span><span class="sxs-lookup"><span data-stu-id="e260a-121">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="e260a-122">L’analyseur signale les éventuels problèmes qu’il trouve dans votre code base.</span><span class="sxs-lookup"><span data-stu-id="e260a-122">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="e260a-123">Les problèmes sont signalés sous forme d’avertissements dans la fenêtre Liste d’erreurs de Visual Studio, comme le montre l’image suivante :</span><span class="sxs-lookup"><span data-stu-id="e260a-123">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![Problèmes signalés par les analyseurs de .NET Framework.](./media/framework-analyzers-2.png)

<span data-ttu-id="e260a-125">Au fil de l’écriture du code, vous voyez des marques ondulées sous les problèmes potentiels de votre code.</span><span class="sxs-lookup"><span data-stu-id="e260a-125">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="e260a-126">Pointez sur un problème pour obtenir plus d’informations et consulter des suggestions pour tout correctif possible, comme illustré dans l’image suivante :</span><span class="sxs-lookup"><span data-stu-id="e260a-126">Hover over any issue to get more information and see suggestions for any possible fix, as shown in the following image:</span></span>

![Rapport interactif des problèmes détectés par les analyseurs de code.](./media/framework-analyzers-1.png)

<span data-ttu-id="e260a-128">Pour plus d’informations, consultez [analyse du code dans Visual Studio](/visualstudio/code-quality/roslyn-analyzers-overview).</span><span class="sxs-lookup"><span data-stu-id="e260a-128">For more information, see [Code analysis in Visual Studio](/visualstudio/code-quality/roslyn-analyzers-overview).</span></span>

## <a name="types-of-rules"></a><span data-ttu-id="e260a-129">Types de règles</span><span class="sxs-lookup"><span data-stu-id="e260a-129">Types of rules</span></span>

<span data-ttu-id="e260a-130">Les analyseurs examinent le code dans votre solution et les avertissements de surface avec un `CA` préfixe.</span><span class="sxs-lookup"><span data-stu-id="e260a-130">The analyzers examine the code in your solution and surface warnings with a `CA` prefix.</span></span> <span data-ttu-id="e260a-131">Pour obtenir la liste de tous les avertissements possibles, consultez [règles de qualité du code](../fundamentals/code-analysis/quality-rules/index.md).</span><span class="sxs-lookup"><span data-stu-id="e260a-131">For a list of all possible warnings, see [Code quality rules](../fundamentals/code-analysis/quality-rules/index.md).</span></span> <span data-ttu-id="e260a-132">Seuls certains de ces avertissements s’appliquent à .NET Framework API, notamment :</span><span class="sxs-lookup"><span data-stu-id="e260a-132">Only some of these warnings apply to .NET Framework APIS, including:</span></span>

- [<span data-ttu-id="e260a-133">CA1058 : Les types ne doivent pas étendre certains types de base</span><span class="sxs-lookup"><span data-stu-id="e260a-133">CA1058: Types should not extend certain base types</span></span>](../fundamentals/code-analysis/quality-rules/ca1058.md)

- [<span data-ttu-id="e260a-134">CA2153 : Ne pas intercepter des exceptions d’état endommagé</span><span class="sxs-lookup"><span data-stu-id="e260a-134">CA2153: Do not catch corrupted state exceptions</span></span>](../fundamentals/code-analysis/quality-rules/ca2153.md)

- [<span data-ttu-id="e260a-135">CA2229 : Implémentez des constructeurs de sérialisation</span><span class="sxs-lookup"><span data-stu-id="e260a-135">CA2229: Implement serialization constructors</span></span>](../fundamentals/code-analysis/quality-rules/ca2229.md)

- [<span data-ttu-id="e260a-136">CA2235 : Marquez tous les champs non sérialisés</span><span class="sxs-lookup"><span data-stu-id="e260a-136">CA2235: Mark all non-serializable fields</span></span>](../fundamentals/code-analysis/quality-rules/ca2235.md)

- [<span data-ttu-id="e260a-137">CA2237 : Marquez les types ISerializable comme étant sérialisables</span><span class="sxs-lookup"><span data-stu-id="e260a-137">CA2237: Mark ISerializable types with serializable</span></span>](../fundamentals/code-analysis/quality-rules/ca2237.md)

- [<span data-ttu-id="e260a-138">CA3075 : Traitement du DTD non sécurisé dans XML</span><span class="sxs-lookup"><span data-stu-id="e260a-138">CA3075: Insecure DTD processing in XML</span></span>](../fundamentals/code-analysis/quality-rules/ca3075.md)

- [<span data-ttu-id="e260a-139">CA5350 : n’utilisez pas d’algorithmes de chiffrement faibles</span><span class="sxs-lookup"><span data-stu-id="e260a-139">CA5350: Do not use weak cryptographic algorithms</span></span>](../fundamentals/code-analysis/quality-rules/ca5350.md)

- [<span data-ttu-id="e260a-140">CA5351 n’utilisez pas d’algorithmes de chiffrement rompus</span><span class="sxs-lookup"><span data-stu-id="e260a-140">CA5351 Do not use broken cryptographic algorithms</span></span>](../fundamentals/code-analysis/quality-rules/ca5351.md)

## <a name="see-also"></a><span data-ttu-id="e260a-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e260a-141">See also</span></span>

- [<span data-ttu-id="e260a-142">Analyse du code dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e260a-142">Code analysis in Visual Studio</span></span>](/visualstudio/code-quality/roslyn-analyzers-overview)
- [<span data-ttu-id="e260a-143">Analyse du code dans le kit de développement logiciel (SDK) .NET</span><span class="sxs-lookup"><span data-stu-id="e260a-143">Code analysis in the .NET SDK</span></span>](../fundamentals/code-analysis/overview.md)
