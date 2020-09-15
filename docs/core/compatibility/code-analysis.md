---
title: Modifications importantes de l’analyse du code
description: Répertorie les modifications avec rupture dans les analyseurs de code source .NET.
ms.date: 09/02/2020
ms.openlocfilehash: 20badd69b316e1d87700b3c5061a71d648b71c64
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065154"
---
# <a name="code-analysis-breaking-changes"></a><span data-ttu-id="4ae2e-103">Modifications importantes de l’analyse du code</span><span class="sxs-lookup"><span data-stu-id="4ae2e-103">Code analysis breaking changes</span></span>

<span data-ttu-id="4ae2e-104">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="4ae2e-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="4ae2e-105">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="4ae2e-105">Breaking change</span></span> | <span data-ttu-id="4ae2e-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4ae2e-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="4ae2e-107">CA1416 : compatibilité de la plateforme</span><span class="sxs-lookup"><span data-stu-id="4ae2e-107">CA1416: Platform compatibility</span></span>](#ca1416-platform-compatibility) | <span data-ttu-id="4ae2e-108">5.0</span><span class="sxs-lookup"><span data-stu-id="4ae2e-108">5.0</span></span> |
| [<span data-ttu-id="4ae2e-109">Ca1417 : OutAttribute sur le paramètre de chaîne pour P/Invoke</span><span class="sxs-lookup"><span data-stu-id="4ae2e-109">CA1417: OutAttribute on string parameter for P/Invoke</span></span>](#ca1417-outattribute-on-string-parameter-for-pinvoke) | <span data-ttu-id="4ae2e-110">5.0</span><span class="sxs-lookup"><span data-stu-id="4ae2e-110">5.0</span></span> |
| [<span data-ttu-id="4ae2e-111">CA1831 : utiliser AsSpan à la place d’indexeurs basés sur une plage pour la chaîne</span><span class="sxs-lookup"><span data-stu-id="4ae2e-111">CA1831: Use AsSpan instead of Range-based indexers for string</span></span>](#ca1831-use-asspan-instead-of-range-based-indexers-for-string) | <span data-ttu-id="4ae2e-112">5.0</span><span class="sxs-lookup"><span data-stu-id="4ae2e-112">5.0</span></span> |
| [<span data-ttu-id="4ae2e-113">CA2013 : Ne pas utiliser ReferenceEquals avec des types valeur</span><span class="sxs-lookup"><span data-stu-id="4ae2e-113">CA2013: Do not use ReferenceEquals with value types</span></span>](#ca2013-do-not-use-referenceequals-with-value-types) | <span data-ttu-id="4ae2e-114">5.0</span><span class="sxs-lookup"><span data-stu-id="4ae2e-114">5.0</span></span> |
| [<span data-ttu-id="4ae2e-115">CA2014 : Ne pas utiliser stackalloc dans les boucles</span><span class="sxs-lookup"><span data-stu-id="4ae2e-115">CA2014: Do not use stackalloc in loops</span></span>](#ca2014-do-not-use-stackalloc-in-loops) | <span data-ttu-id="4ae2e-116">5.0</span><span class="sxs-lookup"><span data-stu-id="4ae2e-116">5.0</span></span> |
| [<span data-ttu-id="4ae2e-117">Ca2015 : ne définissez pas de finaliseur pour les types dérivés de MemoryManager\<T></span><span class="sxs-lookup"><span data-stu-id="4ae2e-117">CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | <span data-ttu-id="4ae2e-118">5.0</span><span class="sxs-lookup"><span data-stu-id="4ae2e-118">5.0</span></span> |
| [<span data-ttu-id="4ae2e-119">CA2247 : l’argument du constructeur TaskCompletionSource doit être une valeur TaskCreationOptions</span><span class="sxs-lookup"><span data-stu-id="4ae2e-119">CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | <span data-ttu-id="4ae2e-120">5.0</span><span class="sxs-lookup"><span data-stu-id="4ae2e-120">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="4ae2e-121">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="4ae2e-121">.NET 5.0</span></span>

[!INCLUDE [ca1416-platform-compatibility-analyzer](../../../includes/core-changes/codeanalysis/5.0/ca1416-platform-compatibility-analyzer.md)]

***

[!INCLUDE [outattributes-on-pinvoke-string-parameters](../../../includes/core-changes/codeanalysis/5.0/ca1417-outattributes-on-pinvoke-string-parameters.md)]

***

[!INCLUDE [range-based-indexer-on-string](../../../includes/core-changes/codeanalysis/5.0/ca1831-range-based-indexer-on-string.md)]

***

[!INCLUDE [referenceequals-on-value-types](../../../includes/core-changes/codeanalysis/5.0/ca2013-referenceequals-on-value-types.md)]

***

[!INCLUDE [stackalloc-in-loops](../../../includes/core-changes/codeanalysis/5.0/ca2014-stackalloc-in-loops.md)]

***

[!INCLUDE [finalizers-for-memorymanager-types](../../../includes/core-changes/codeanalysis/5.0/ca2015-finalizers-for-memorymanager-types.md)]

***

[!INCLUDE [ctor-arg-should-be-taskcreationoptions](../../../includes/core-changes/codeanalysis/5.0/ca2247-ctor-arg-should-be-taskcreationoptions.md)]

***
