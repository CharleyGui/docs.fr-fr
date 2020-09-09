---
title: Modifications importantes de l’analyse du code
description: Répertorie les modifications avec rupture dans les analyseurs de code source .NET.
ms.date: 09/02/2020
ms.openlocfilehash: f1e89c90e6d91b9b3555542a0c7adf2607a76a01
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598048"
---
# <a name="code-analysis-breaking-changes"></a><span data-ttu-id="c6ca7-103">Modifications importantes de l’analyse du code</span><span class="sxs-lookup"><span data-stu-id="c6ca7-103">Code analysis breaking changes</span></span>

<span data-ttu-id="c6ca7-104">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="c6ca7-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="c6ca7-105">Modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="c6ca7-105">Breaking change</span></span> | <span data-ttu-id="c6ca7-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c6ca7-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="c6ca7-107">Ca1417 : OutAttribute sur le paramètre de chaîne pour P/Invoke</span><span class="sxs-lookup"><span data-stu-id="c6ca7-107">CA1417: OutAttribute on string parameter for P/Invoke</span></span>](#ca1417-outattribute-on-string-parameter-for-pinvoke) | <span data-ttu-id="c6ca7-108">5.0</span><span class="sxs-lookup"><span data-stu-id="c6ca7-108">5.0</span></span> |
| [<span data-ttu-id="c6ca7-109">CA1831 : utiliser AsSpan à la place d’indexeurs basés sur une plage pour la chaîne</span><span class="sxs-lookup"><span data-stu-id="c6ca7-109">CA1831: Use AsSpan instead of Range-based indexers for string</span></span>](#ca1831-use-asspan-instead-of-range-based-indexers-for-string) | <span data-ttu-id="c6ca7-110">5.0</span><span class="sxs-lookup"><span data-stu-id="c6ca7-110">5.0</span></span> |
| [<span data-ttu-id="c6ca7-111">CA2013 : Ne pas utiliser ReferenceEquals avec des types valeur</span><span class="sxs-lookup"><span data-stu-id="c6ca7-111">CA2013: Do not use ReferenceEquals with value types</span></span>](#ca2013-do-not-use-referenceequals-with-value-types) | <span data-ttu-id="c6ca7-112">5.0</span><span class="sxs-lookup"><span data-stu-id="c6ca7-112">5.0</span></span> |
| [<span data-ttu-id="c6ca7-113">CA2014 : Ne pas utiliser stackalloc dans les boucles</span><span class="sxs-lookup"><span data-stu-id="c6ca7-113">CA2014: Do not use stackalloc in loops</span></span>](#ca2014-do-not-use-stackalloc-in-loops) | <span data-ttu-id="c6ca7-114">5.0</span><span class="sxs-lookup"><span data-stu-id="c6ca7-114">5.0</span></span> |
| [<span data-ttu-id="c6ca7-115">Ca2015 : ne définissez pas de finaliseur pour les types dérivés de MemoryManager\<T></span><span class="sxs-lookup"><span data-stu-id="c6ca7-115">CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | <span data-ttu-id="c6ca7-116">5.0</span><span class="sxs-lookup"><span data-stu-id="c6ca7-116">5.0</span></span> |
| [<span data-ttu-id="c6ca7-117">CA2247 : l’argument du constructeur TaskCompletionSource doit être une valeur TaskCreationOptions</span><span class="sxs-lookup"><span data-stu-id="c6ca7-117">CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | <span data-ttu-id="c6ca7-118">5.0</span><span class="sxs-lookup"><span data-stu-id="c6ca7-118">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="c6ca7-119">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="c6ca7-119">.NET 5.0</span></span>

[!INCLUDE [outattributes-on-pinvoke-string-parameters](../../../includes/core-changes/codeanalysis/5.0/outattributes-on-pinvoke-string-parameters.md)]

***

[!INCLUDE [range-based-indexer-on-string](../../../includes/core-changes/codeanalysis/5.0/range-based-indexer-on-string.md)]

***

[!INCLUDE [referenceequals-on-value-types](../../../includes/core-changes/codeanalysis/5.0/referenceequals-on-value-types.md)]

***

[!INCLUDE [stackalloc-in-loops](../../../includes/core-changes/codeanalysis/5.0/stackalloc-in-loops.md)]

***

[!INCLUDE [finalizers-for-memorymanager-types](../../../includes/core-changes/codeanalysis/5.0/finalizers-for-memorymanager-types.md)]

***

[!INCLUDE [ctor-arg-should-be-taskcreationoptions](../../../includes/core-changes/codeanalysis/5.0/ctor-arg-should-be-taskcreationoptions.md)]

***
