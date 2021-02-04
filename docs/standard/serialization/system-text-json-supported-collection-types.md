---
title: Types de collections pris en charge dans System.Text.Json
description: Découvrez les types de collections pris en charge pour la sérialisation par les API dans l' System.Text.Json espace de noms.
ms.date: 02/01/2021
no-loc:
- System.Text.Json
ms.topic: reference
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 5a5016c70e86124510a4778aafb9fb14b1890add
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99547653"
---
# <a name="supported-collection-types-in-systemtextjson"></a><span data-ttu-id="04982-103">Types de collections pris en charge dans System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="04982-103">Supported collection types in System.Text.Json</span></span>

<span data-ttu-id="04982-104">Cet article donne une vue d’ensemble des regroupements pris en charge pour la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="04982-104">This article gives an overview of which collections are supported for serialization and deserialization.</span></span> <span data-ttu-id="04982-105"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> prend en charge un type de collection pour la sérialisation s’il :</span><span class="sxs-lookup"><span data-stu-id="04982-105"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> supports a collection type for serialization if it:</span></span>

* <span data-ttu-id="04982-106">Dérive de <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="04982-106">Derives from <xref:System.Collections.IEnumerable>.</span></span>
* <span data-ttu-id="04982-107">Contient des éléments qui sont sérialisables.</span><span class="sxs-lookup"><span data-stu-id="04982-107">Contains elements that are serializable.</span></span>

<span data-ttu-id="04982-108">Le sérialiseur appelle la <xref:System.Collections.IEnumerable.GetEnumerator> méthode et écrit les éléments.</span><span class="sxs-lookup"><span data-stu-id="04982-108">The serializer calls the <xref:System.Collections.IEnumerable.GetEnumerator> method, and writes the elements.</span></span>

<span data-ttu-id="04982-109">La désérialisation est plus compliquée et n’est pas prise en charge pour certains types de collections.</span><span class="sxs-lookup"><span data-stu-id="04982-109">Deserialization is more complicated and is not supported for some collection types.</span></span>

<span data-ttu-id="04982-110">Les sections suivantes sont organisées par espace de noms et indiquent les types pris en charge pour la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="04982-110">The following sections are organized by namespace and show which types are supported for serialization and deserialization.</span></span>

## <a name="systemarray-namespace"></a><span data-ttu-id="04982-111">Espace de noms System. Array</span><span class="sxs-lookup"><span data-stu-id="04982-111">System.Array namespace</span></span>

| <span data-ttu-id="04982-112">Type</span><span class="sxs-lookup"><span data-stu-id="04982-112">Type</span></span>                                                                                            | <span data-ttu-id="04982-113">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-113">Serialization</span></span> | <span data-ttu-id="04982-114">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-114">Deserialization</span></span> |
|-------------------------------------------------------------------------------------------------|---------------|-----------------|
| [<span data-ttu-id="04982-115">Tableaux unidimensionnels</span><span class="sxs-lookup"><span data-stu-id="04982-115">Single-dimensional arrays</span></span>](../../csharp/programming-guide/arrays/single-dimensional-arrays.md) | <span data-ttu-id="04982-116">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-116">✔️</span></span>           | <span data-ttu-id="04982-117">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-117">✔️</span></span>              |
| [<span data-ttu-id="04982-118">Tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="04982-118">Multi-dimensional arrays</span></span>](../../csharp/programming-guide/arrays/multidimensional-arrays.md)    | ❌           | ❌              |
| [<span data-ttu-id="04982-119">Tableaux en escalier</span><span class="sxs-lookup"><span data-stu-id="04982-119">Jagged arrays</span></span>](../../csharp/programming-guide/arrays/jagged-arrays.md)                         | <span data-ttu-id="04982-120">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-120">✔️</span></span>           | <span data-ttu-id="04982-121">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-121">✔️</span></span>              |

## <a name="systemcollections-namespace"></a><span data-ttu-id="04982-122">Espace de noms System.Collections</span><span class="sxs-lookup"><span data-stu-id="04982-122">System.Collections namespace</span></span>

| <span data-ttu-id="04982-123">Type</span><span class="sxs-lookup"><span data-stu-id="04982-123">Type</span></span>                                      | <span data-ttu-id="04982-124">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-124">Serialization</span></span> | <span data-ttu-id="04982-125">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-125">Deserialization</span></span> |
|-------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ArrayList>       | <span data-ttu-id="04982-126">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-126">✔️</span></span>           | <span data-ttu-id="04982-127">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-127">✔️</span></span>              |
| <xref:System.Collections.BitArray>        | <span data-ttu-id="04982-128">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-128">✔️</span></span>           | ❌              |
| <xref:System.Collections.DictionaryEntry> | <span data-ttu-id="04982-129">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-129">✔️</span></span>           | <span data-ttu-id="04982-130">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-130">✔️</span></span>              |
| <xref:System.Collections.Hashtable>       | <span data-ttu-id="04982-131">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-131">✔️</span></span>           | <span data-ttu-id="04982-132">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-132">✔️</span></span>              |
| <xref:System.Collections.Queue>           | <span data-ttu-id="04982-133">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-133">✔️</span></span>           | <span data-ttu-id="04982-134">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-134">✔️</span></span>              |
| <xref:System.Collections.SortedList>      | <span data-ttu-id="04982-135">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-135">✔️</span></span>           | <span data-ttu-id="04982-136">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-136">✔️</span></span>              |
| <xref:System.Collections.Stack>           | <span data-ttu-id="04982-137">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-137">✔️</span></span>           | <span data-ttu-id="04982-138">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-138">✔️</span></span>              |
| <xref:System.Collections.ICollection>     | <span data-ttu-id="04982-139">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-139">✔️</span></span>           | <span data-ttu-id="04982-140">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-140">✔️</span></span>              |
| <xref:System.Collections.IDictionary>     | <span data-ttu-id="04982-141">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-141">✔️</span></span>           | <span data-ttu-id="04982-142">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-142">✔️</span></span>              |
| <xref:System.Collections.IEnumerable>     | <span data-ttu-id="04982-143">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-143">✔️</span></span>           | <span data-ttu-id="04982-144">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-144">✔️</span></span>              |
| <xref:System.Collections.IList>           | <span data-ttu-id="04982-145">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-145">✔️</span></span>           | <span data-ttu-id="04982-146">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-146">✔️</span></span>              |

## <a name="systemcollectionsgeneric-namespace"></a><span data-ttu-id="04982-147">Espace de noms System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="04982-147">System.Collections.Generic namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="04982-148">Type</span><span class="sxs-lookup"><span data-stu-id="04982-148">Type</span></span>                                                      | <span data-ttu-id="04982-149">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-149">Serialization</span></span> | <span data-ttu-id="04982-150">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-150">Deserialization</span></span> |
|-----------------------------------------------------------|---------------|-----------------|
| <span data-ttu-id="04982-151"><xref:System.Collections.Generic.Dictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="04982-151"><xref:System.Collections.Generic.Dictionary%602> \*</span></span>       | <span data-ttu-id="04982-152">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-152">✔️</span></span>           | <span data-ttu-id="04982-153">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-153">✔️</span></span>              |
| <xref:System.Collections.Generic.HashSet%601>             | <span data-ttu-id="04982-154">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-154">✔️</span></span>           | <span data-ttu-id="04982-155">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-155">✔️</span></span>              |
| <xref:System.Collections.Generic.KeyValuePair%602>        | <span data-ttu-id="04982-156">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-156">✔️</span></span>           | <span data-ttu-id="04982-157">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-157">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedList%601>          | <span data-ttu-id="04982-158">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-158">✔️</span></span>           | <span data-ttu-id="04982-159">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-159">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedListNode%601>      | <span data-ttu-id="04982-160">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-160">✔️</span></span>           | ❌              |
| <xref:System.Collections.Generic.List%601>                | <span data-ttu-id="04982-161">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-161">✔️</span></span>           | <span data-ttu-id="04982-162">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-162">✔️</span></span>              |
| <xref:System.Collections.Generic.Queue%601>               | <span data-ttu-id="04982-163">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-163">✔️</span></span>           | <span data-ttu-id="04982-164">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-164">✔️</span></span>              |
| <span data-ttu-id="04982-165"><xref:System.Collections.Generic.SortedDictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="04982-165"><xref:System.Collections.Generic.SortedDictionary%602> \*</span></span> | <span data-ttu-id="04982-166">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-166">✔️</span></span>           | <span data-ttu-id="04982-167">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-167">✔️</span></span>              |
| <span data-ttu-id="04982-168"><xref:System.Collections.Generic.SortedList%602> \*</span><span class="sxs-lookup"><span data-stu-id="04982-168"><xref:System.Collections.Generic.SortedList%602> \*</span></span>       | <span data-ttu-id="04982-169">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-169">✔️</span></span>           | <span data-ttu-id="04982-170">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-170">✔️</span></span>              |
| <xref:System.Collections.Generic.SortedSet%601>           | <span data-ttu-id="04982-171">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-171">✔️</span></span>           | <span data-ttu-id="04982-172">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-172">✔️</span></span>              |
| <xref:System.Collections.Generic.Stack%601>               | <span data-ttu-id="04982-173">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-173">✔️</span></span>           | <span data-ttu-id="04982-174">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-174">✔️</span></span>              |
| <xref:System.Collections.Generic.IAsyncEnumerable%601>    | ❌           | ❌              |
| <xref:System.Collections.Generic.ICollection%601>         | <span data-ttu-id="04982-175">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-175">✔️</span></span>           | <span data-ttu-id="04982-176">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-176">✔️</span></span>              |
| <span data-ttu-id="04982-177"><xref:System.Collections.Generic.IDictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="04982-177"><xref:System.Collections.Generic.IDictionary%602> \*</span></span>      | <span data-ttu-id="04982-178">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-178">✔️</span></span>           | <span data-ttu-id="04982-179">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-179">✔️</span></span>              |
| <xref:System.Collections.Generic.IEnumerable%601>         | <span data-ttu-id="04982-180">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-180">✔️</span></span>           | <span data-ttu-id="04982-181">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-181">✔️</span></span>              |
| <xref:System.Collections.Generic.IList%601>               | <span data-ttu-id="04982-182">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-182">✔️</span></span>           | <span data-ttu-id="04982-183">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-183">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyCollection%601> | <span data-ttu-id="04982-184">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-184">✔️</span></span>           | <span data-ttu-id="04982-185">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-185">✔️</span></span>              |
| <span data-ttu-id="04982-186"><xref:System.Collections.Generic.IReadOnlyDictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="04982-186"><xref:System.Collections.Generic.IReadOnlyDictionary%602> \*</span></span> | <span data-ttu-id="04982-187">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-187">✔️</span></span>        | <span data-ttu-id="04982-188">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-188">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyList%601>       | <span data-ttu-id="04982-189">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-189">✔️</span></span>           | <span data-ttu-id="04982-190">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-190">✔️</span></span>              |
| <xref:System.Collections.Generic.ISet%601>                | <span data-ttu-id="04982-191">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-191">✔️</span></span>           | <span data-ttu-id="04982-192">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-192">✔️</span></span>              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="04982-193">Type</span><span class="sxs-lookup"><span data-stu-id="04982-193">Type</span></span>                                                                                            | <span data-ttu-id="04982-194">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-194">Serialization</span></span> | <span data-ttu-id="04982-195">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-195">Deserialization</span></span> |
|-------------------------------------------------------------------------------------------------|---------------|-----------------|
| <span data-ttu-id="04982-196">[Dictionnaire \<string, TValue> ](xref:System.Collections.Generic.Dictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="04982-196">[Dictionary\<string, TValue>](xref:System.Collections.Generic.Dictionary%602) \*</span></span>                | <span data-ttu-id="04982-197">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-197">✔️</span></span>           | <span data-ttu-id="04982-198">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-198">✔️</span></span>              |
| <xref:System.Collections.Generic.HashSet%601>                                                   | <span data-ttu-id="04982-199">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-199">✔️</span></span>           | <span data-ttu-id="04982-200">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-200">✔️</span></span>              |
| <xref:System.Collections.Generic.KeyValuePair%602>                                              | <span data-ttu-id="04982-201">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-201">✔️</span></span>           | <span data-ttu-id="04982-202">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-202">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedList%601>                                                | <span data-ttu-id="04982-203">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-203">✔️</span></span>           | <span data-ttu-id="04982-204">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-204">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedListNode%601>                                            | <span data-ttu-id="04982-205">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-205">✔️</span></span>           | ❌              |
| <xref:System.Collections.Generic.List%601>                                                      | <span data-ttu-id="04982-206">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-206">✔️</span></span>           | <span data-ttu-id="04982-207">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-207">✔️</span></span>              |
| <xref:System.Collections.Generic.Queue%601>                                                     | <span data-ttu-id="04982-208">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-208">✔️</span></span>           | <span data-ttu-id="04982-209">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-209">✔️</span></span>              |
| <span data-ttu-id="04982-210">[SortedDictionary \<string, TValue> ](xref:System.Collections.Generic.SortedDictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="04982-210">[SortedDictionary\<string, TValue>](xref:System.Collections.Generic.SortedDictionary%602) \*</span></span>    | <span data-ttu-id="04982-211">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-211">✔️</span></span>           | <span data-ttu-id="04982-212">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-212">✔️</span></span>              |
| <span data-ttu-id="04982-213">[SortedList \<string, TValue> ](xref:System.Collections.Generic.SortedList%602)\*</span><span class="sxs-lookup"><span data-stu-id="04982-213">[SortedList\<string, TValue>](xref:System.Collections.Generic.SortedList%602) \*</span></span>                | <span data-ttu-id="04982-214">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-214">✔️</span></span>           | <span data-ttu-id="04982-215">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-215">✔️</span></span>              |
| <xref:System.Collections.Generic.SortedSet%601>                                                 | <span data-ttu-id="04982-216">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-216">✔️</span></span>           | <span data-ttu-id="04982-217">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-217">✔️</span></span>              |
| <xref:System.Collections.Generic.Stack%601>                                                     | <span data-ttu-id="04982-218">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-218">✔️</span></span>           | <span data-ttu-id="04982-219">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-219">✔️</span></span>              |
| <xref:System.Collections.Generic.IAsyncEnumerable%601>                                          | ❌           | ❌              |
| <xref:System.Collections.Generic.ICollection%601>                                               | <span data-ttu-id="04982-220">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-220">✔️</span></span>           | <span data-ttu-id="04982-221">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-221">✔️</span></span>              |
| <span data-ttu-id="04982-222">[IDictionary\<string, TValue> ](xref:System.Collections.Generic.IDictionary%602) \*</span><span class="sxs-lookup"><span data-stu-id="04982-222">[IDictionary\<string, TValue>](xref:System.Collections.Generic.IDictionary%602) \*</span></span>              | <span data-ttu-id="04982-223">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-223">✔️</span></span>           | <span data-ttu-id="04982-224">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-224">✔️</span></span>              |
| <xref:System.Collections.Generic.IEnumerable%601>                                               | <span data-ttu-id="04982-225">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-225">✔️</span></span>           | <span data-ttu-id="04982-226">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-226">✔️</span></span>              |
| <xref:System.Collections.Generic.IList%601>                                                     | <span data-ttu-id="04982-227">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-227">✔️</span></span>           | <span data-ttu-id="04982-228">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-228">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyCollection%601>                                       | <span data-ttu-id="04982-229">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-229">✔️</span></span>           | <span data-ttu-id="04982-230">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-230">✔️</span></span>              |
| <span data-ttu-id="04982-231">[IReadOnlyDictionary \<string, TValue> ](xref:System.Collections.Generic.IReadOnlyDictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="04982-231">[IReadOnlyDictionary\<string, TValue>](xref:System.Collections.Generic.IReadOnlyDictionary%602) \*</span></span> | <span data-ttu-id="04982-232">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-232">✔️</span></span>        | <span data-ttu-id="04982-233">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-233">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyList%601>                                             | <span data-ttu-id="04982-234">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-234">✔️</span></span>           | <span data-ttu-id="04982-235">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-235">✔️</span></span>              |
| <xref:System.Collections.Generic.ISet%601>                                                      | <span data-ttu-id="04982-236">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-236">✔️</span></span>           | <span data-ttu-id="04982-237">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-237">✔️</span></span>              |

::: zone-end

<span data-ttu-id="04982-238">\* Consultez [types de clés pris en charge](#supported-key-types).</span><span class="sxs-lookup"><span data-stu-id="04982-238">\* See [Supported key types](#supported-key-types).</span></span>

## <a name="systemcollectionsimmutable-namespace"></a><span data-ttu-id="04982-239">Espace de noms System. Collections. immuable</span><span class="sxs-lookup"><span data-stu-id="04982-239">System.Collections.Immutable namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="04982-240">Type</span><span class="sxs-lookup"><span data-stu-id="04982-240">Type</span></span>                                                              | <span data-ttu-id="04982-241">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-241">Serialization</span></span> | <span data-ttu-id="04982-242">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-242">Deserialization</span></span> |
|-------------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Immutable.ImmutableArray%601>            | <span data-ttu-id="04982-243">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-243">✔️</span></span>           | <span data-ttu-id="04982-244">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-244">✔️</span></span>              |
| <span data-ttu-id="04982-245"><xref:System.Collections.Immutable.ImmutableDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="04982-245"><xref:System.Collections.Immutable.ImmutableDictionary%602> \*\*</span></span>  | <span data-ttu-id="04982-246">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-246">✔️</span></span>           | <span data-ttu-id="04982-247">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-247">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableHashSet%601>          | <span data-ttu-id="04982-248">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-248">✔️</span></span>           | <span data-ttu-id="04982-249">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-249">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>            | <span data-ttu-id="04982-250">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-250">✔️</span></span>           | <span data-ttu-id="04982-251">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-251">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableQueue%601>            | <span data-ttu-id="04982-252">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-252">✔️</span></span>           | <span data-ttu-id="04982-253">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-253">✔️</span></span>              |
| <span data-ttu-id="04982-254"><xref:System.Collections.Immutable.ImmutableSortedDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="04982-254"><xref:System.Collections.Immutable.ImmutableSortedDictionary%602> \*\*</span></span> | <span data-ttu-id="04982-255">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-255">✔️</span></span>      | <span data-ttu-id="04982-256">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-256">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableSortedSet%601>        | <span data-ttu-id="04982-257">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-257">✔️</span></span>           | <span data-ttu-id="04982-258">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-258">✔️</span></span>              |
| <span data-ttu-id="04982-259"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="04982-259"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span></span>         | <span data-ttu-id="04982-260">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-260">✔️</span></span>           | <span data-ttu-id="04982-261">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-261">✔️</span></span>              |
| <span data-ttu-id="04982-262"><xref:System.Collections.Immutable.IImmutableDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="04982-262"><xref:System.Collections.Immutable.IImmutableDictionary%602> \*\*</span></span> | <span data-ttu-id="04982-263">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-263">✔️</span></span>           | <span data-ttu-id="04982-264">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-264">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>            | <span data-ttu-id="04982-265">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-265">✔️</span></span>           | <span data-ttu-id="04982-266">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-266">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableQueue%601>           | <span data-ttu-id="04982-267">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-267">✔️</span></span>           | <span data-ttu-id="04982-268">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-268">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableSet%601>             | <span data-ttu-id="04982-269">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-269">✔️</span></span>           | <span data-ttu-id="04982-270">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-270">✔️</span></span>              |
| <span data-ttu-id="04982-271"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="04982-271"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span></span>        | <span data-ttu-id="04982-272">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-272">✔️</span></span>           | <span data-ttu-id="04982-273">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-273">✔️</span></span>              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="04982-274">Type</span><span class="sxs-lookup"><span data-stu-id="04982-274">Type</span></span>                                                                                                          | <span data-ttu-id="04982-275">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-275">Serialization</span></span> | <span data-ttu-id="04982-276">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-276">Deserialization</span></span> |
|---------------------------------------------------------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Immutable.ImmutableArray%601>                                                        | <span data-ttu-id="04982-277">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-277">✔️</span></span>           | <span data-ttu-id="04982-278">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-278">✔️</span></span>              |
| <span data-ttu-id="04982-279">[ImmutableDictionary \<string, TValue> ](xref:System.Collections.Immutable.ImmutableDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="04982-279">[ImmutableDictionary\<string, TValue>](xref:System.Collections.Immutable.ImmutableDictionary%602) \*\*</span></span>        | <span data-ttu-id="04982-280">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-280">✔️</span></span>           | <span data-ttu-id="04982-281">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-281">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableHashSet%601>                                                      | <span data-ttu-id="04982-282">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-282">✔️</span></span>           | <span data-ttu-id="04982-283">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-283">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>                                                        | <span data-ttu-id="04982-284">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-284">✔️</span></span>           | <span data-ttu-id="04982-285">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-285">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableQueue%601>                                                        | <span data-ttu-id="04982-286">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-286">✔️</span></span>           | <span data-ttu-id="04982-287">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-287">✔️</span></span>              |
| <span data-ttu-id="04982-288">[ImmutableSortedDictionary \<string, TValue> ](xref:System.Collections.Immutable.ImmutableSortedDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="04982-288">[ImmutableSortedDictionary\<string, TValue>](xref:System.Collections.Immutable.ImmutableSortedDictionary%602) \*\*</span></span>| <span data-ttu-id="04982-289">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-289">✔️</span></span>       | <span data-ttu-id="04982-290">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-290">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableSortedSet%601>                                                    | <span data-ttu-id="04982-291">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-291">✔️</span></span>           | <span data-ttu-id="04982-292">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-292">✔️</span></span>              |
| <span data-ttu-id="04982-293"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="04982-293"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span></span>                                                     | <span data-ttu-id="04982-294">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-294">✔️</span></span>           | <span data-ttu-id="04982-295">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-295">✔️</span></span>              |
| <span data-ttu-id="04982-296">[IImmutableDictionary \<string, TValue> ](xref:System.Collections.Immutable.IImmutableDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="04982-296">[IImmutableDictionary\<string, TValue>](xref:System.Collections.Immutable.IImmutableDictionary%602) \*\*</span></span>      | <span data-ttu-id="04982-297">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-297">✔️</span></span>           | <span data-ttu-id="04982-298">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-298">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>                                                        | <span data-ttu-id="04982-299">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-299">✔️</span></span>           | <span data-ttu-id="04982-300">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-300">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableQueue%601>                                                       | <span data-ttu-id="04982-301">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-301">✔️</span></span>           | <span data-ttu-id="04982-302">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-302">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableSet%601>                                                         | <span data-ttu-id="04982-303">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-303">✔️</span></span>           | <span data-ttu-id="04982-304">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-304">✔️</span></span>              |
| <span data-ttu-id="04982-305"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="04982-305"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span></span>                                                    | <span data-ttu-id="04982-306">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-306">✔️</span></span>           | <span data-ttu-id="04982-307">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-307">✔️</span></span>              |

::: zone-end

<span data-ttu-id="04982-308">\*Consultez [prendre en charge l’aller \<T> -retour pour la pile](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="04982-308">\* See [Support round trip for Stack\<T>](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span></span>

<span data-ttu-id="04982-309">\*\* Consultez [types de clés pris en charge](#supported-key-types).</span><span class="sxs-lookup"><span data-stu-id="04982-309">\*\* See [Supported key types](#supported-key-types).</span></span>

## <a name="systemcollectionsspecialized-namespace"></a><span data-ttu-id="04982-310">Espace de noms System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="04982-310">System.Collections.Specialized namespace</span></span>

| <span data-ttu-id="04982-311">Type</span><span class="sxs-lookup"><span data-stu-id="04982-311">Type</span></span>                                                      | <span data-ttu-id="04982-312">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-312">Serialization</span></span> | <span data-ttu-id="04982-313">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-313">Deserialization</span></span> |
|-----------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Specialized.BitVector32>         | <span data-ttu-id="04982-314">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-314">✔️</span></span>           | ❌\*            |
| <xref:System.Collections.Specialized.HybridDictionary>    | <span data-ttu-id="04982-315">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-315">✔️</span></span>           | <span data-ttu-id="04982-316">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-316">✔️</span></span>              |
| <xref:System.Collections.Specialized.IOrderedDictionary>  | <span data-ttu-id="04982-317">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-317">✔️</span></span>           | ❌              |
| <xref:System.Collections.Specialized.ListDictionary>      | <span data-ttu-id="04982-318">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-318">✔️</span></span>           | <span data-ttu-id="04982-319">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-319">✔️</span></span>              |
| <xref:System.Collections.Specialized.StringCollection>    | <span data-ttu-id="04982-320">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-320">✔️</span></span>           | ❌              |
| <xref:System.Collections.Specialized.StringDictionary>    | <span data-ttu-id="04982-321">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-321">✔️</span></span>           | ❌              |
| <xref:System.Collections.Specialized.NameValueCollection> | <span data-ttu-id="04982-322">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-322">✔️</span></span>           | ❌              |

<span data-ttu-id="04982-323">\* Lorsque <xref:System.Collections.Specialized.BitVector32> est désérialisé, la <xref:System.Collections.Specialized.BitVector32.Data> propriété est ignorée, car elle n’a pas d’accesseur Set public.</span><span class="sxs-lookup"><span data-stu-id="04982-323">\* When <xref:System.Collections.Specialized.BitVector32> is deserialized, the <xref:System.Collections.Specialized.BitVector32.Data> property is skipped because it doesn't have a public setter.</span></span> <span data-ttu-id="04982-324">Aucune exception n’est générée.</span><span class="sxs-lookup"><span data-stu-id="04982-324">No exception is thrown.</span></span>

## <a name="systemcollectionsconcurrent-namespace"></a><span data-ttu-id="04982-325">Espace de noms System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="04982-325">System.Collections.Concurrent namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="04982-326">Type</span><span class="sxs-lookup"><span data-stu-id="04982-326">Type</span></span>                                                          | <span data-ttu-id="04982-327">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-327">Serialization</span></span> | <span data-ttu-id="04982-328">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-328">Deserialization</span></span> |
|---------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Concurrent.BlockingCollection%601>   | <span data-ttu-id="04982-329">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-329">✔️</span></span>           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentBag%601>        | <span data-ttu-id="04982-330">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-330">✔️</span></span>           | ❌              |
| <span data-ttu-id="04982-331"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="04982-331"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> \*\*</span></span> | <span data-ttu-id="04982-332">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-332">✔️</span></span>      | <span data-ttu-id="04982-333">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-333">✔️</span></span>              |
| <xref:System.Collections.Concurrent.ConcurrentQueue%601>      | <span data-ttu-id="04982-334">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-334">✔️</span></span>           | <span data-ttu-id="04982-335">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-335">✔️</span></span>              |
| <span data-ttu-id="04982-336"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="04982-336"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span>   | <span data-ttu-id="04982-337">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-337">✔️</span></span>           | <span data-ttu-id="04982-338">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-338">✔️</span></span>              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="04982-339">Type</span><span class="sxs-lookup"><span data-stu-id="04982-339">Type</span></span>                                                        | <span data-ttu-id="04982-340">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-340">Serialization</span></span> | <span data-ttu-id="04982-341">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-341">Deserialization</span></span> |
|-------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Concurrent.BlockingCollection%601> | <span data-ttu-id="04982-342">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-342">✔️</span></span>           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentBag%601>      | <span data-ttu-id="04982-343">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-343">✔️</span></span>           | ❌              |
| <span data-ttu-id="04982-344">[ConcurrentDictionary \<string, TValue> ](xref:System.Collections.Concurrent.ConcurrentDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="04982-344">[ConcurrentDictionary\<string, TValue>](xref:System.Collections.Concurrent.ConcurrentDictionary%602) \*\*</span></span> |<span data-ttu-id="04982-345">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-345">✔️</span></span>|<span data-ttu-id="04982-346">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-346">✔️</span></span>|
| <xref:System.Collections.Concurrent.ConcurrentQueue%601>    | <span data-ttu-id="04982-347">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-347">✔️</span></span>           | <span data-ttu-id="04982-348">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-348">✔️</span></span>              |
| <span data-ttu-id="04982-349"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="04982-349"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span> | <span data-ttu-id="04982-350">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-350">✔️</span></span>           | <span data-ttu-id="04982-351">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-351">✔️</span></span>              |

::: zone-end

<span data-ttu-id="04982-352">\*Consultez [prendre en charge l’aller \<T> -retour pour la pile](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="04982-352">\* See [Support round trip for Stack\<T>](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span></span>

<span data-ttu-id="04982-353">\*\* Consultez [types de clés pris en charge](#supported-key-types).</span><span class="sxs-lookup"><span data-stu-id="04982-353">\*\* See [Supported key types](#supported-key-types).</span></span>

## <a name="systemcollectionsobjectmodel-namespace"></a><span data-ttu-id="04982-354">Espace de noms System.Collections.ObjectModel</span><span class="sxs-lookup"><span data-stu-id="04982-354">System.Collections.ObjectModel namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="04982-355">Type</span><span class="sxs-lookup"><span data-stu-id="04982-355">Type</span></span>                                                           | <span data-ttu-id="04982-356">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-356">Serialization</span></span> | <span data-ttu-id="04982-357">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-357">Deserialization</span></span> |
|----------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ObjectModel.Collection%601>           | <span data-ttu-id="04982-358">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-358">✔️</span></span>            | <span data-ttu-id="04982-359">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-359">✔️</span></span>             |
| <span data-ttu-id="04982-360">[KeyedCollection \<string, TValue> ](xref:System.Collections.ObjectModel.KeyedCollection%602)\*</span><span class="sxs-lookup"><span data-stu-id="04982-360">[KeyedCollection\<string, TValue>](xref:System.Collections.ObjectModel.KeyedCollection%602) \*</span></span> |<span data-ttu-id="04982-361">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-361">✔️</span></span>|❌|
| <xref:System.Collections.ObjectModel.ObservableCollection%601> | <span data-ttu-id="04982-362">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-362">✔️</span></span>            | <span data-ttu-id="04982-363">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-363">✔️</span></span>             |
| <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>   | <span data-ttu-id="04982-364">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-364">✔️</span></span>            | ❌             |
| <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602>   | <span data-ttu-id="04982-365">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-365">✔️</span></span>            | ❌             |
| <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601> | <span data-ttu-id="04982-366">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-366">✔️</span></span>    | ❌             |

<span data-ttu-id="04982-367">\* Les non- `string` clés ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="04982-367">\* Non-`string` keys are not supported.</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="04982-368">Type</span><span class="sxs-lookup"><span data-stu-id="04982-368">Type</span></span>                                                           | <span data-ttu-id="04982-369">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-369">Serialization</span></span> | <span data-ttu-id="04982-370">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-370">Deserialization</span></span> |
|----------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ObjectModel.Collection%601>           | <span data-ttu-id="04982-371">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-371">✔️</span></span>            | <span data-ttu-id="04982-372">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-372">✔️</span></span>             |
| <span data-ttu-id="04982-373">[KeyedCollection \<string, TValue> ](xref:System.Collections.ObjectModel.KeyedCollection%602)\*</span><span class="sxs-lookup"><span data-stu-id="04982-373">[KeyedCollection\<string, TValue>](xref:System.Collections.ObjectModel.KeyedCollection%602) \*</span></span> |<span data-ttu-id="04982-374">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-374">✔️</span></span>|❌|
| <xref:System.Collections.ObjectModel.ObservableCollection%601> | <span data-ttu-id="04982-375">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-375">✔️</span></span>            | <span data-ttu-id="04982-376">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-376">✔️</span></span>             |
| <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>   | <span data-ttu-id="04982-377">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-377">✔️</span></span>            | ❌             |
| <span data-ttu-id="04982-378">[Objet ReadOnlyDictionary \<string, TValue> ](xref:System.Collections.ObjectModel.ReadOnlyDictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="04982-378">[ReadOnlyDictionary\<string, TValue>](xref:System.Collections.ObjectModel.ReadOnlyDictionary%602) \*</span></span> |<span data-ttu-id="04982-379">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-379">✔️</span></span>|❌|
| <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601>| <span data-ttu-id="04982-380">✔️</span><span class="sxs-lookup"><span data-stu-id="04982-380">✔️</span></span>     | ❌             |

<span data-ttu-id="04982-381">\* Consultez [types de clés pris en charge](#supported-key-types).</span><span class="sxs-lookup"><span data-stu-id="04982-381">\* See [Supported key types](#supported-key-types).</span></span>

::: zone-end

## <a name="custom-collections"></a><span data-ttu-id="04982-382">Regroupements personnalisés</span><span class="sxs-lookup"><span data-stu-id="04982-382">Custom collections</span></span>

<span data-ttu-id="04982-383">Tout type de collection qui n’est pas dans l’un des espaces de noms précédents est considéré comme une collection personnalisée.</span><span class="sxs-lookup"><span data-stu-id="04982-383">Any collection type that isn't in one of the preceding namespaces is considered a custom collection.</span></span> <span data-ttu-id="04982-384">Ces types incluent des types définis par l’utilisateur et des types définis par ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="04982-384">Such types include user-defined types and types defined by ASP.NET Core.</span></span> <span data-ttu-id="04982-385">Par exemple, <xref:Microsoft.Extensions.Primitives?displayProperty=fullName> se trouve dans ce groupe.</span><span class="sxs-lookup"><span data-stu-id="04982-385">For example, <xref:Microsoft.Extensions.Primitives?displayProperty=fullName> is in this group.</span></span>

<span data-ttu-id="04982-386">Toutes les collections personnalisées (tout ce qui dérive de `IEnumerable` ) sont prises en charge pour la sérialisation, à condition que leurs types d’éléments soient pris en charge.</span><span class="sxs-lookup"><span data-stu-id="04982-386">All custom collections (everything that derives from `IEnumerable`) are supported for serialization, as long as their element types are supported.</span></span>

### <a name="custom-collections-with-deserialization-support"></a><span data-ttu-id="04982-387">Collections personnalisées avec prise en charge de la désérialisation</span><span class="sxs-lookup"><span data-stu-id="04982-387">Custom collections with deserialization support</span></span>

<span data-ttu-id="04982-388">Une collection personnalisée est prise en charge pour la désérialisation si :</span><span class="sxs-lookup"><span data-stu-id="04982-388">A custom collection is supported for deserialization if it:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="04982-389">N’est pas une interface ni abstraite.</span><span class="sxs-lookup"><span data-stu-id="04982-389">Isn't an interface or abstract.</span></span>
* <span data-ttu-id="04982-390">A un constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="04982-390">Has a parameterless constructor.</span></span>
* <span data-ttu-id="04982-391">Contient les types d’éléments pris en charge par <xref:System.Text.Json.JsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="04982-391">Contains element types that are supported by <xref:System.Text.Json.JsonSerializer>.</span></span>
* <span data-ttu-id="04982-392">Implémente ou hérite d’une ou plusieurs des interfaces ou classes suivantes :</span><span class="sxs-lookup"><span data-stu-id="04982-392">Implements or inherits one or more of the following interfaces or classes:</span></span>
  * <xref:System.Collections.Concurrent.ConcurrentQueue%601>
  * <span data-ttu-id="04982-393"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="04982-393"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span>
  * <xref:System.Collections.Generic.ICollection%601>
  * <xref:System.Collections.IDictionary>
  * <span data-ttu-id="04982-394"><xref:System.Collections.Generic.IDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="04982-394"><xref:System.Collections.Generic.IDictionary%602> \*\*</span></span>
  * <xref:System.Collections.IList>
  * <xref:System.Collections.Generic.IList%601>
  * <xref:System.Collections.Queue>
  * <xref:System.Collections.Generic.Queue%601>
  * <span data-ttu-id="04982-395"><xref:System.Collections.Stack> \*</span><span class="sxs-lookup"><span data-stu-id="04982-395"><xref:System.Collections.Stack> \*</span></span>
  * <span data-ttu-id="04982-396"><xref:System.Collections.Generic.Stack%601> \*</span><span class="sxs-lookup"><span data-stu-id="04982-396"><xref:System.Collections.Generic.Stack%601> \*</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="04982-397">N’est pas une interface ni abstraite.</span><span class="sxs-lookup"><span data-stu-id="04982-397">Isn't an interface or abstract.</span></span>
* <span data-ttu-id="04982-398">A un constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="04982-398">Has a parameterless constructor.</span></span>
* <span data-ttu-id="04982-399">Contient les types d’éléments pris en charge par <xref:System.Text.Json.JsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="04982-399">Contains element types that are supported by <xref:System.Text.Json.JsonSerializer>.</span></span>
* <span data-ttu-id="04982-400">Implémente ou hérite d’une ou plusieurs des interfaces ou classes suivantes :</span><span class="sxs-lookup"><span data-stu-id="04982-400">Implements or inherits one or more of the following interfaces or classes:</span></span>
  * <xref:System.Collections.Concurrent.ConcurrentQueue%601>
  * <span data-ttu-id="04982-401"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="04982-401"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span>
  * <xref:System.Collections.Generic.ICollection%601>
  * <xref:System.Collections.IDictionary>
  * <span data-ttu-id="04982-402">[IDictionary\<string, TValue>](xref:System.Collections.Generic.IDictionary%602) \* \*</span><span class="sxs-lookup"><span data-stu-id="04982-402">[IDictionary\<string, TValue>](xref:System.Collections.Generic.IDictionary%602) \*\*</span></span>
  * <xref:System.Collections.IList>
  * <xref:System.Collections.Generic.IList%601>
  * <xref:System.Collections.Queue>
  * <xref:System.Collections.Generic.Queue%601>
  * <span data-ttu-id="04982-403"><xref:System.Collections.Stack> \*</span><span class="sxs-lookup"><span data-stu-id="04982-403"><xref:System.Collections.Stack> \*</span></span>
  * <span data-ttu-id="04982-404"><xref:System.Collections.Generic.Stack%601> \*</span><span class="sxs-lookup"><span data-stu-id="04982-404"><xref:System.Collections.Generic.Stack%601> \*</span></span>

::: zone-end

  <span data-ttu-id="04982-405">\*Consultez [prendre en charge l’aller \<T> -retour pour la pile](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="04982-405">\* See [Support round trip for Stack\<T>](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span></span>

  <span data-ttu-id="04982-406">\*\* Consultez [types de clés pris en charge](#supported-key-types).</span><span class="sxs-lookup"><span data-stu-id="04982-406">\*\* See [Supported key types](#supported-key-types).</span></span>

### <a name="custom-collections-with-known-issues"></a><span data-ttu-id="04982-407">Regroupements personnalisés avec problèmes connus</span><span class="sxs-lookup"><span data-stu-id="04982-407">Custom collections with known issues</span></span>

<span data-ttu-id="04982-408">Il existe des problèmes connus avec les regroupements personnalisés suivants :</span><span class="sxs-lookup"><span data-stu-id="04982-408">There are known issues with the following custom collections:</span></span>

- <span data-ttu-id="04982-409"><xref:System.Dynamic.ExpandoObject>: Consultez [dotnet/Runtime # 29690](https://github.com/dotnet/runtime/issues/29690).</span><span class="sxs-lookup"><span data-stu-id="04982-409"><xref:System.Dynamic.ExpandoObject>: See [dotnet/runtime#29690](https://github.com/dotnet/runtime/issues/29690).</span></span>
- <span data-ttu-id="04982-410"><xref:System.Dynamic.DynamicObject>: Consultez [dotnet/Runtime # 1808](https://github.com/dotnet/runtime/issues/1808).</span><span class="sxs-lookup"><span data-stu-id="04982-410"><xref:System.Dynamic.DynamicObject>: See [dotnet/runtime#1808](https://github.com/dotnet/runtime/issues/1808).</span></span>
- <span data-ttu-id="04982-411"><xref:System.Data.DataTable>: Consultez [dotnet/docs # 21366](https://github.com/dotnet/docs/issues/21366).</span><span class="sxs-lookup"><span data-stu-id="04982-411"><xref:System.Data.DataTable>: See [dotnet/docs#21366](https://github.com/dotnet/docs/issues/21366).</span></span>
- <span data-ttu-id="04982-412"><xref:Microsoft.AspNetCore.Http.FormFile?displayProperty=fullName>: Consultez [dotnet/Runtime # 1559](https://github.com/dotnet/runtime/issues/1559).</span><span class="sxs-lookup"><span data-stu-id="04982-412"><xref:Microsoft.AspNetCore.Http.FormFile?displayProperty=fullName>: See [dotnet/runtime#1559](https://github.com/dotnet/runtime/issues/1559).</span></span>
- <span data-ttu-id="04982-413"><xref:Microsoft.AspNetCore.Http.IFormCollection?displayProperty=fullName>: Consultez [dotnet/Runtime # 1559](https://github.com/dotnet/runtime/issues/1559).</span><span class="sxs-lookup"><span data-stu-id="04982-413"><xref:Microsoft.AspNetCore.Http.IFormCollection?displayProperty=fullName>: See [dotnet/runtime#1559](https://github.com/dotnet/runtime/issues/1559).</span></span>

<span data-ttu-id="04982-414">Pour plus d’informations sur les problèmes connus, consultez la rubrique [problèmes ouverts dans System.Text.Json ](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json).</span><span class="sxs-lookup"><span data-stu-id="04982-414">For more information about known issues, see the [open issues in System.Text.Json](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json).</span></span>

## <a name="supported-key-types"></a><span data-ttu-id="04982-415">Types de clé pris en charge</span><span class="sxs-lookup"><span data-stu-id="04982-415">Supported key types</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="04982-416">Les types pris en charge pour les clés `Dictionary` et `SortedList` sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="04982-416">Supported types for the keys of `Dictionary` and `SortedList` types include the following:</span></span>

* `Boolean`
* `Byte`
* `DateTime`
* `DateTimeOffset`
* `Decimal`
* `Double`
* `Enum`
* `Guid`
* `Int16`
* `Int32`
* `Int64`
* <span data-ttu-id="04982-417">`Object` (Uniquement lors de la sérialisation et si le type de Runtime est l’un des types pris en charge dans cette liste.)</span><span class="sxs-lookup"><span data-stu-id="04982-417">`Object` (Only on serialization and if the runtime type is one of the supported types in this list.)</span></span>
* `SByte`
* `Single`
* `String`
* `UInt16`
* `UInt32`
* `UInt64`

::: zone-end

::: zone pivot="dotnet-core-3-1"

<span data-ttu-id="04982-418">\*\* Les non- `string` clés pour les `Dictionary` types et ne `SortedList` sont pas prises en charge dans .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="04982-418">\*\* Non-`string` keys for `Dictionary` and `SortedList` types are not supported in .NET Core 3.1.</span></span>

::: zone-end

## <a name="see-also"></a><span data-ttu-id="04982-419">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04982-419">See also</span></span>

* [<span data-ttu-id="04982-420">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="04982-420">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="04982-421">Instancier des instances JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="04982-421">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="04982-422">Activer la correspondance non sensible à la casse</span><span class="sxs-lookup"><span data-stu-id="04982-422">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="04982-423">Personnaliser les noms et valeurs de propriété</span><span class="sxs-lookup"><span data-stu-id="04982-423">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="04982-424">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="04982-424">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="04982-425">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="04982-425">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="04982-426">Gérer le JSON de dépassement</span><span class="sxs-lookup"><span data-stu-id="04982-426">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="04982-427">Préserver les références</span><span class="sxs-lookup"><span data-stu-id="04982-427">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="04982-428">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="04982-428">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="04982-429">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="04982-429">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="04982-430">Migrer de Newtonsoft.Jsvers System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="04982-430">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="04982-431">Personnaliser l’encodage de caractères</span><span class="sxs-lookup"><span data-stu-id="04982-431">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="04982-432">Écrire des sérialiseurs et des désérialiseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="04982-432">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="04982-433">Écrire des convertisseurs personnalisés pour la sérialisation JSON</span><span class="sxs-lookup"><span data-stu-id="04982-433">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="04982-434">Prise en charge DateTime et DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="04982-434">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="04982-435">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="04982-435">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="04982-436">[System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="04982-436">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
