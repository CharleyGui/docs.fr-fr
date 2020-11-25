---
title: 'Modification avec rupture : ca2014 : ne pas utiliser stackalloc dans les boucles'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 provoquée par l’activation de la règle d’analyse du code ca2014.
ms.date: 09/03/2020
ms.openlocfilehash: 7ad6203c0edd930bbbe43cdb8df0413cba833d8e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760815"
---
# <a name="warning-ca2014-do-not-use-stackalloc-in-loops"></a><span data-ttu-id="5046f-103">AVERTISSEMENT ca2014 : ne pas utiliser stackalloc dans les boucles</span><span class="sxs-lookup"><span data-stu-id="5046f-103">Warning CA2014: Do not use stackalloc in loops</span></span>

<span data-ttu-id="5046f-104">La règle de l’analyseur de code .NET [ca2014](/visualstudio/code-quality/ca2014) est activée, par défaut, à partir de .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="5046f-104">.NET code analyzer rule [CA2014](/visualstudio/code-quality/ca2014) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="5046f-105">Il génère un avertissement de génération pour tout code C# dans lequel une expression [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) est utilisée à l’intérieur d’une boucle.</span><span class="sxs-lookup"><span data-stu-id="5046f-105">It produces a build warning for any C# code where a [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) expression is used inside a loop.</span></span>

## <a name="change-description"></a><span data-ttu-id="5046f-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="5046f-106">Change description</span></span>

<span data-ttu-id="5046f-107">À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../fundamentals/code-analysis/overview.md).</span><span class="sxs-lookup"><span data-stu-id="5046f-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="5046f-108">Plusieurs de ces règles sont activées par défaut, y compris [ca2014](/visualstudio/code-quality/ca2014).</span><span class="sxs-lookup"><span data-stu-id="5046f-108">Several of these rules are enabled, by default, including [CA2014](/visualstudio/code-quality/ca2014).</span></span> <span data-ttu-id="5046f-109">Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.</span><span class="sxs-lookup"><span data-stu-id="5046f-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="5046f-110">La règle ca2014 recherche le code C# dans lequel une [expression stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) est utilisée à l’intérieur d’une boucle.</span><span class="sxs-lookup"><span data-stu-id="5046f-110">Rule CA2014 looks for C# code where a [stackalloc expression](../../../../csharp/language-reference/operators/stackalloc.md) is used inside a loop.</span></span> <span data-ttu-id="5046f-111">[stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) alloue de la mémoire à partir du frame de pile actuel.</span><span class="sxs-lookup"><span data-stu-id="5046f-111">[stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) allocates memory from the current stack frame.</span></span> <span data-ttu-id="5046f-112">La mémoire n’est pas libérée tant que l’appel de la méthode en cours n’est pas retourné, ce qui peut entraîner un dépassement de capacité de la pile.</span><span class="sxs-lookup"><span data-stu-id="5046f-112">The memory isn't released until the current method call returns, which can lead to stack overflows.</span></span> <span data-ttu-id="5046f-113">Comme vous ne pouvez pas intercepter les exceptions de dépassement de capacité de la pile, l’application se termine en cas de dépassement de capacité de pile.</span><span class="sxs-lookup"><span data-stu-id="5046f-113">Because you can't catch stack overflow exceptions, the app will terminate in case of stack overflow.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="5046f-114">Version introduite</span><span class="sxs-lookup"><span data-stu-id="5046f-114">Version introduced</span></span>

<span data-ttu-id="5046f-115">5.0</span><span class="sxs-lookup"><span data-stu-id="5046f-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="5046f-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="5046f-116">Recommended action</span></span>

- <span data-ttu-id="5046f-117">Évitez d’utiliser [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) dans les boucles.</span><span class="sxs-lookup"><span data-stu-id="5046f-117">Avoid using [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) inside loops.</span></span> <span data-ttu-id="5046f-118">Allouez le bloc de mémoire en dehors de la boucle et réutilisez-le à l’intérieur de la boucle.</span><span class="sxs-lookup"><span data-stu-id="5046f-118">Allocate the memory block outside the loop and reuse it inside the loop.</span></span> <span data-ttu-id="5046f-119">Pour plus d’informations, consultez [ca2014](/visualstudio/code-quality/ca2014).</span><span class="sxs-lookup"><span data-stu-id="5046f-119">For more information, see [CA2014](/visualstudio/code-quality/ca2014).</span></span>

- <span data-ttu-id="5046f-120">Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="5046f-120">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="5046f-121">Pour plus d’informations, consultez [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="5046f-121">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="5046f-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="5046f-122">Affected APIs</span></span>

<span data-ttu-id="5046f-123">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="5046f-123">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
