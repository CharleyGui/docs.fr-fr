---
title: Modifications importantes de l’analyse du code
description: Répertorie les modifications avec rupture dans les analyseurs de code source .NET.
ms.date: 08/22/2020
ms.openlocfilehash: 8b2b50c5f03a3ca971aefd0f2cf53624dfa82274
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465569"
---
# <a name="code-analysis-breaking-changes"></a><span data-ttu-id="be669-103">Modifications importantes de l’analyse du code</span><span class="sxs-lookup"><span data-stu-id="be669-103">Code analysis breaking changes</span></span>

<span data-ttu-id="be669-104">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="be669-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="be669-105">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="be669-105">Breaking change</span></span> | <span data-ttu-id="be669-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="be669-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="be669-107">CA1831 : utiliser AsSpan ou AsMemory à la place de l’indexeur basé sur une plage</span><span class="sxs-lookup"><span data-stu-id="be669-107">CA1831: Use AsSpan or AsMemory instead of Range-based indexer</span></span>](#ca1831-use-asspan-or-asmemory-instead-of-range-based-indexer) | <span data-ttu-id="be669-108">5.0</span><span class="sxs-lookup"><span data-stu-id="be669-108">5.0</span></span> |
| [<span data-ttu-id="be669-109">CA2014 : Ne pas utiliser stackalloc dans les boucles</span><span class="sxs-lookup"><span data-stu-id="be669-109">CA2014: Do not use stackalloc in loops</span></span>](#ca2014-do-not-use-stackalloc-in-loops) | <span data-ttu-id="be669-110">5.0</span><span class="sxs-lookup"><span data-stu-id="be669-110">5.0</span></span> |
| [<span data-ttu-id="be669-111">Ca2015 : ne définissez pas de finaliseur pour les types dérivés de MemoryManager\<T></span><span class="sxs-lookup"><span data-stu-id="be669-111">CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | <span data-ttu-id="be669-112">5.0</span><span class="sxs-lookup"><span data-stu-id="be669-112">5.0</span></span> |
| [<span data-ttu-id="be669-113">CA2247 : l’argument du constructeur TaskCompletionSource doit être une valeur TaskCreationOptions</span><span class="sxs-lookup"><span data-stu-id="be669-113">CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | <span data-ttu-id="be669-114">5.0</span><span class="sxs-lookup"><span data-stu-id="be669-114">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="be669-115">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="be669-115">.NET 5.0</span></span>

[!INCLUDE [range-based-indexer-on-string](../../../includes/core-changes/codeanalysis/5.0/range-based-indexer-on-string.md)]

***

[!INCLUDE [stackalloc-in-loops](../../../includes/core-changes/codeanalysis/5.0/stackalloc-in-loops.md)]

***

[!INCLUDE [finalizers-for-memorymanager-types](../../../includes/core-changes/codeanalysis/5.0/finalizers-for-memorymanager-types.md)]

***

[!INCLUDE [ctor-arg-should-be-taskcreationoptions](../../../includes/core-changes/codeanalysis/5.0/ctor-arg-should-be-taskcreationoptions.md)]

***
