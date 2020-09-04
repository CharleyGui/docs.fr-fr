---
ms.openlocfilehash: a51160a8ab5a4b437e51db31def577f8d8f50182
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465570"
---
### <a name="ca2014-do-not-use-stackalloc-in-loops"></a><span data-ttu-id="d2b17-101">CA2014 : Ne pas utiliser stackalloc dans les boucles</span><span class="sxs-lookup"><span data-stu-id="d2b17-101">CA2014: Do not use stackalloc in loops</span></span>

<span data-ttu-id="d2b17-102">La règle de l’analyseur de code .NET [ca2014](/visualstudio/code-quality/ca2014) est activée, par défaut, à partir de .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="d2b17-102">.NET code analyzer rule [CA2014](/visualstudio/code-quality/ca2014) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="d2b17-103">Il génère un avertissement de génération pour tout code C# dans lequel une expression [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) est utilisée à l’intérieur d’une boucle.</span><span class="sxs-lookup"><span data-stu-id="d2b17-103">It produces a build warning for any C# code where a [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) expression is used inside a loop.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d2b17-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="d2b17-104">Change description</span></span>

<span data-ttu-id="d2b17-105">À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../docs/fundamentals/productivity/code-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="d2b17-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="d2b17-106">Plusieurs de ces règles sont activées par défaut, y compris [ca2014](/visualstudio/code-quality/ca2014).</span><span class="sxs-lookup"><span data-stu-id="d2b17-106">Several of these rules are enabled, by default, including [CA2014](/visualstudio/code-quality/ca2014).</span></span> <span data-ttu-id="d2b17-107">Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.</span><span class="sxs-lookup"><span data-stu-id="d2b17-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="d2b17-108">La règle ca2014 recherche le code C# dans lequel une [expression stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) est utilisée à l’intérieur d’une boucle.</span><span class="sxs-lookup"><span data-stu-id="d2b17-108">Rule CA2014 looks for C# code where a [stackalloc expression](../../../../docs/csharp/language-reference/operators/stackalloc.md) is used inside a loop.</span></span> <span data-ttu-id="d2b17-109">[stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) alloue de la mémoire à partir du frame de pile actuel.</span><span class="sxs-lookup"><span data-stu-id="d2b17-109">[stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) allocates memory from the current stack frame.</span></span> <span data-ttu-id="d2b17-110">La mémoire n’est pas libérée tant que l’appel de la méthode en cours n’est pas retourné, ce qui peut entraîner un dépassement de capacité de la pile.</span><span class="sxs-lookup"><span data-stu-id="d2b17-110">The memory isn't released until the current method call returns, which can lead to stack overflows.</span></span> <span data-ttu-id="d2b17-111">Comme vous ne pouvez pas intercepter les exceptions de dépassement de capacité de la pile, l’application se termine en cas de dépassement de capacité de pile.</span><span class="sxs-lookup"><span data-stu-id="d2b17-111">Because you can't catch stack overflow exceptions, the app will terminate in case of stack overflow.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d2b17-112">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d2b17-112">Version introduced</span></span>

<span data-ttu-id="d2b17-113">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="d2b17-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d2b17-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d2b17-114">Recommended action</span></span>

- <span data-ttu-id="d2b17-115">Évitez d’utiliser [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) dans les boucles.</span><span class="sxs-lookup"><span data-stu-id="d2b17-115">Avoid using [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) inside loops.</span></span> <span data-ttu-id="d2b17-116">Allouez le bloc de mémoire en dehors de la boucle et réutilisez-le à l’intérieur de la boucle.</span><span class="sxs-lookup"><span data-stu-id="d2b17-116">Allocate the memory block outside the loop and reuse it inside the loop.</span></span> <span data-ttu-id="d2b17-117">Pour plus d’informations, consultez [ca2014](/visualstudio/code-quality/ca2014).</span><span class="sxs-lookup"><span data-stu-id="d2b17-117">For more information, see [CA2014](/visualstudio/code-quality/ca2014).</span></span>

- <span data-ttu-id="d2b17-118">Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="d2b17-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="d2b17-119">Pour plus d’informations, consultez [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="d2b17-119">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="d2b17-120">Category</span><span class="sxs-lookup"><span data-stu-id="d2b17-120">Category</span></span>

<span data-ttu-id="d2b17-121">Analyse du code</span><span class="sxs-lookup"><span data-stu-id="d2b17-121">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d2b17-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="d2b17-122">Affected APIs</span></span>

<span data-ttu-id="d2b17-123">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="d2b17-123">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
