---
title: Types de collections pris en charge dans System.Text.Json
description: Découvrez les types de collections pris en charge pour la sérialisation par les API dans l' System.Text.Json espace de noms.
ms.date: 01/06/2021
no-loc:
- System.Text.Json
ms.topic: reference
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 48033689e844dd29c999395255b5a1565fa2996e
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970992"
---
# <a name="supported-collection-types-in-no-locsystemtextjson"></a><span data-ttu-id="f674f-103">Types de collections pris en charge dans System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="f674f-103">Supported collection types in System.Text.Json</span></span>

<span data-ttu-id="f674f-104">Cet article donne une vue d’ensemble des regroupements pris en charge pour la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="f674f-104">This article gives an overview of which collections are supported for serialization and deserialization.</span></span> <span data-ttu-id="f674f-105"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> prend en charge un type de collection pour la sérialisation s’il :</span><span class="sxs-lookup"><span data-stu-id="f674f-105"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> supports a collection type for serialization if it:</span></span>

* <span data-ttu-id="f674f-106">Dérive de <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="f674f-106">Derives from <xref:System.Collections.IEnumerable>.</span></span>
* <span data-ttu-id="f674f-107">Contient des éléments qui sont sérialisables.</span><span class="sxs-lookup"><span data-stu-id="f674f-107">Contains elements that are serializable.</span></span>

<span data-ttu-id="f674f-108">Le sérialiseur appelle la <xref:System.Collections.IEnumerable.GetEnumerator> méthode et écrit les éléments.</span><span class="sxs-lookup"><span data-stu-id="f674f-108">The serializer calls the <xref:System.Collections.IEnumerable.GetEnumerator> method, and writes the elements.</span></span>

<span data-ttu-id="f674f-109">La désérialisation est plus compliquée et n’est pas prise en charge pour certains types de collections.</span><span class="sxs-lookup"><span data-stu-id="f674f-109">Deserialization is more complicated and is not supported for some collection types.</span></span>

<span data-ttu-id="f674f-110">Les sections suivantes sont organisées par espace de noms et indiquent les types pris en charge pour la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="f674f-110">The following sections are organized by namespace and show which types are supported for serialization and deserialization.</span></span>

## <a name="systemcollections-namespace"></a><span data-ttu-id="f674f-111">Espace de noms System.Collections</span><span class="sxs-lookup"><span data-stu-id="f674f-111">System.Collections namespace</span></span>

| <span data-ttu-id="f674f-112">Type</span><span class="sxs-lookup"><span data-stu-id="f674f-112">Type</span></span>                                      | <span data-ttu-id="f674f-113">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-113">Serialization</span></span> | <span data-ttu-id="f674f-114">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-114">Deserialization</span></span> |
|-------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ArrayList>       | <span data-ttu-id="f674f-115">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-115">✔️</span></span>           | <span data-ttu-id="f674f-116">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-116">✔️</span></span>              |
| <xref:System.Collections.BitArray>        | <span data-ttu-id="f674f-117">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-117">✔️</span></span>           | ❌              |
| <xref:System.Collections.DictionaryEntry> | <span data-ttu-id="f674f-118">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-118">✔️</span></span>           | <span data-ttu-id="f674f-119">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-119">✔️</span></span>              |
| <xref:System.Collections.Hashtable>       | <span data-ttu-id="f674f-120">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-120">✔️</span></span>           | <span data-ttu-id="f674f-121">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-121">✔️</span></span>              |
| <xref:System.Collections.Queue>           | <span data-ttu-id="f674f-122">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-122">✔️</span></span>           | <span data-ttu-id="f674f-123">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-123">✔️</span></span>              |
| <xref:System.Collections.SortedList>      | <span data-ttu-id="f674f-124">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-124">✔️</span></span>           | <span data-ttu-id="f674f-125">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-125">✔️</span></span>              |
| <xref:System.Collections.Stack>           | <span data-ttu-id="f674f-126">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-126">✔️</span></span>           | <span data-ttu-id="f674f-127">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-127">✔️</span></span>              |
| <xref:System.Collections.ICollection>     | <span data-ttu-id="f674f-128">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-128">✔️</span></span>           | <span data-ttu-id="f674f-129">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-129">✔️</span></span>              |
| <xref:System.Collections.IDictionary>     | <span data-ttu-id="f674f-130">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-130">✔️</span></span>           | <span data-ttu-id="f674f-131">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-131">✔️</span></span>              |
| <xref:System.Collections.IEnumerable>     | <span data-ttu-id="f674f-132">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-132">✔️</span></span>           | <span data-ttu-id="f674f-133">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-133">✔️</span></span>              |
| <xref:System.Collections.IList>           | <span data-ttu-id="f674f-134">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-134">✔️</span></span>           | <span data-ttu-id="f674f-135">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-135">✔️</span></span>              |

## <a name="systemcollectionsgeneric-namespace"></a><span data-ttu-id="f674f-136">Espace de noms System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="f674f-136">System.Collections.Generic namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="f674f-137">Type</span><span class="sxs-lookup"><span data-stu-id="f674f-137">Type</span></span>                                                      | <span data-ttu-id="f674f-138">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-138">Serialization</span></span> | <span data-ttu-id="f674f-139">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-139">Deserialization</span></span> |
|-----------------------------------------------------------|---------------|-----------------|
| <span data-ttu-id="f674f-140"><xref:System.Collections.Generic.Dictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="f674f-140"><xref:System.Collections.Generic.Dictionary%602> \*</span></span>       | <span data-ttu-id="f674f-141">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-141">✔️</span></span>           | <span data-ttu-id="f674f-142">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-142">✔️</span></span>              |
| <xref:System.Collections.Generic.HashSet%601>             | <span data-ttu-id="f674f-143">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-143">✔️</span></span>           | <span data-ttu-id="f674f-144">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-144">✔️</span></span>              |
| <xref:System.Collections.Generic.KeyValuePair%602>        | <span data-ttu-id="f674f-145">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-145">✔️</span></span>           | <span data-ttu-id="f674f-146">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-146">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedList%601>          | <span data-ttu-id="f674f-147">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-147">✔️</span></span>           | <span data-ttu-id="f674f-148">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-148">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedListNode%601>      | <span data-ttu-id="f674f-149">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-149">✔️</span></span>           | ❌              |
| <xref:System.Collections.Generic.List%601>                | <span data-ttu-id="f674f-150">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-150">✔️</span></span>           | <span data-ttu-id="f674f-151">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-151">✔️</span></span>              |
| <xref:System.Collections.Generic.Queue%601>               | <span data-ttu-id="f674f-152">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-152">✔️</span></span>           | <span data-ttu-id="f674f-153">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-153">✔️</span></span>              |
| <span data-ttu-id="f674f-154"><xref:System.Collections.Generic.SortedDictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="f674f-154"><xref:System.Collections.Generic.SortedDictionary%602> \*</span></span> | <span data-ttu-id="f674f-155">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-155">✔️</span></span>           | <span data-ttu-id="f674f-156">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-156">✔️</span></span>              |
| <span data-ttu-id="f674f-157"><xref:System.Collections.Generic.SortedList%602> \*</span><span class="sxs-lookup"><span data-stu-id="f674f-157"><xref:System.Collections.Generic.SortedList%602> \*</span></span>       | <span data-ttu-id="f674f-158">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-158">✔️</span></span>           | <span data-ttu-id="f674f-159">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-159">✔️</span></span>              |
| <xref:System.Collections.Generic.SortedSet%601>           | <span data-ttu-id="f674f-160">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-160">✔️</span></span>           | <span data-ttu-id="f674f-161">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-161">✔️</span></span>              |
| <xref:System.Collections.Generic.Stack%601>               | <span data-ttu-id="f674f-162">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-162">✔️</span></span>           | <span data-ttu-id="f674f-163">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-163">✔️</span></span>              |
| <xref:System.Collections.Generic.IAsyncEnumerable%601>    | ❌           | ❌              |
| <xref:System.Collections.Generic.ICollection%601>         | <span data-ttu-id="f674f-164">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-164">✔️</span></span>           | <span data-ttu-id="f674f-165">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-165">✔️</span></span>              |
| <span data-ttu-id="f674f-166"><xref:System.Collections.Generic.IDictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="f674f-166"><xref:System.Collections.Generic.IDictionary%602> \*</span></span>      | <span data-ttu-id="f674f-167">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-167">✔️</span></span>           | <span data-ttu-id="f674f-168">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-168">✔️</span></span>              |
| <xref:System.Collections.Generic.IEnumerable%601>         | <span data-ttu-id="f674f-169">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-169">✔️</span></span>           | <span data-ttu-id="f674f-170">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-170">✔️</span></span>              |
| <xref:System.Collections.Generic.IList%601>               | <span data-ttu-id="f674f-171">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-171">✔️</span></span>           | <span data-ttu-id="f674f-172">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-172">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyCollection%601> | <span data-ttu-id="f674f-173">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-173">✔️</span></span>           | <span data-ttu-id="f674f-174">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-174">✔️</span></span>              |
| <span data-ttu-id="f674f-175"><xref:System.Collections.Generic.IReadOnlyDictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="f674f-175"><xref:System.Collections.Generic.IReadOnlyDictionary%602> \*</span></span> | <span data-ttu-id="f674f-176">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-176">✔️</span></span>        | <span data-ttu-id="f674f-177">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-177">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyList%601>       | <span data-ttu-id="f674f-178">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-178">✔️</span></span>           | <span data-ttu-id="f674f-179">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-179">✔️</span></span>              |
| <xref:System.Collections.Generic.ISet%601>                | <span data-ttu-id="f674f-180">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-180">✔️</span></span>           | <span data-ttu-id="f674f-181">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-181">✔️</span></span>              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="f674f-182">Type</span><span class="sxs-lookup"><span data-stu-id="f674f-182">Type</span></span>                                                                                            | <span data-ttu-id="f674f-183">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-183">Serialization</span></span> | <span data-ttu-id="f674f-184">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-184">Deserialization</span></span> |
|-------------------------------------------------------------------------------------------------|---------------|-----------------|
| <span data-ttu-id="f674f-185">[Dictionnaire \<string, TValue> ](xref:System.Collections.Generic.Dictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="f674f-185">[Dictionary\<string, TValue>](xref:System.Collections.Generic.Dictionary%602) \*</span></span>                | <span data-ttu-id="f674f-186">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-186">✔️</span></span>           | <span data-ttu-id="f674f-187">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-187">✔️</span></span>              |
| <xref:System.Collections.Generic.HashSet%601>                                                   | <span data-ttu-id="f674f-188">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-188">✔️</span></span>           | <span data-ttu-id="f674f-189">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-189">✔️</span></span>              |
| <xref:System.Collections.Generic.KeyValuePair%602>                                              | <span data-ttu-id="f674f-190">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-190">✔️</span></span>           | <span data-ttu-id="f674f-191">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-191">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedList%601>                                                | <span data-ttu-id="f674f-192">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-192">✔️</span></span>           | <span data-ttu-id="f674f-193">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-193">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedListNode%601>                                            | <span data-ttu-id="f674f-194">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-194">✔️</span></span>           | ❌              |
| <xref:System.Collections.Generic.List%601>                                                      | <span data-ttu-id="f674f-195">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-195">✔️</span></span>           | <span data-ttu-id="f674f-196">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-196">✔️</span></span>              |
| <xref:System.Collections.Generic.Queue%601>                                                     | <span data-ttu-id="f674f-197">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-197">✔️</span></span>           | <span data-ttu-id="f674f-198">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-198">✔️</span></span>              |
| <span data-ttu-id="f674f-199">[SortedDictionary \<string, TValue> ](xref:System.Collections.Generic.SortedDictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="f674f-199">[SortedDictionary\<string, TValue>](xref:System.Collections.Generic.SortedDictionary%602) \*</span></span>    | <span data-ttu-id="f674f-200">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-200">✔️</span></span>           | <span data-ttu-id="f674f-201">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-201">✔️</span></span>              |
| <span data-ttu-id="f674f-202">[SortedList \<string, TValue> ](xref:System.Collections.Generic.SortedList%602)\*</span><span class="sxs-lookup"><span data-stu-id="f674f-202">[SortedList\<string, TValue>](xref:System.Collections.Generic.SortedList%602) \*</span></span>                | <span data-ttu-id="f674f-203">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-203">✔️</span></span>           | <span data-ttu-id="f674f-204">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-204">✔️</span></span>              |
| <xref:System.Collections.Generic.SortedSet%601>                                                 | <span data-ttu-id="f674f-205">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-205">✔️</span></span>           | <span data-ttu-id="f674f-206">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-206">✔️</span></span>              |
| <xref:System.Collections.Generic.Stack%601>                                                     | <span data-ttu-id="f674f-207">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-207">✔️</span></span>           | <span data-ttu-id="f674f-208">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-208">✔️</span></span>              |
| <xref:System.Collections.Generic.IAsyncEnumerable%601>                                          | ❌           | ❌              |
| <xref:System.Collections.Generic.ICollection%601>                                               | <span data-ttu-id="f674f-209">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-209">✔️</span></span>           | <span data-ttu-id="f674f-210">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-210">✔️</span></span>              |
| <span data-ttu-id="f674f-211">[IDictionary\<string, TValue> ](xref:System.Collections.Generic.IDictionary%602) \*</span><span class="sxs-lookup"><span data-stu-id="f674f-211">[IDictionary\<string, TValue>](xref:System.Collections.Generic.IDictionary%602) \*</span></span>              | <span data-ttu-id="f674f-212">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-212">✔️</span></span>           | <span data-ttu-id="f674f-213">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-213">✔️</span></span>              |
| <xref:System.Collections.Generic.IEnumerable%601>                                               | <span data-ttu-id="f674f-214">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-214">✔️</span></span>           | <span data-ttu-id="f674f-215">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-215">✔️</span></span>              |
| <xref:System.Collections.Generic.IList%601>                                                     | <span data-ttu-id="f674f-216">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-216">✔️</span></span>           | <span data-ttu-id="f674f-217">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-217">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyCollection%601>                                       | <span data-ttu-id="f674f-218">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-218">✔️</span></span>           | <span data-ttu-id="f674f-219">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-219">✔️</span></span>              |
| <span data-ttu-id="f674f-220">[IReadOnlyDictionary \<string, TValue> ](xref:System.Collections.Generic.IReadOnlyDictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="f674f-220">[IReadOnlyDictionary\<string, TValue>](xref:System.Collections.Generic.IReadOnlyDictionary%602) \*</span></span> | <span data-ttu-id="f674f-221">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-221">✔️</span></span>        | <span data-ttu-id="f674f-222">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-222">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyList%601>                                             | <span data-ttu-id="f674f-223">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-223">✔️</span></span>           | <span data-ttu-id="f674f-224">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-224">✔️</span></span>              |
| <xref:System.Collections.Generic.ISet%601>                                                      | <span data-ttu-id="f674f-225">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-225">✔️</span></span>           | <span data-ttu-id="f674f-226">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-226">✔️</span></span>              |

::: zone-end

<span data-ttu-id="f674f-227">\* Consultez [types de clés pris en charge](#supported-key-types).</span><span class="sxs-lookup"><span data-stu-id="f674f-227">\* See [Supported key types](#supported-key-types).</span></span>

## <a name="systemcollectionsimmutable-namespace"></a><span data-ttu-id="f674f-228">Espace de noms System. Collections. immuable</span><span class="sxs-lookup"><span data-stu-id="f674f-228">System.Collections.Immutable namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="f674f-229">Type</span><span class="sxs-lookup"><span data-stu-id="f674f-229">Type</span></span>                                                              | <span data-ttu-id="f674f-230">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-230">Serialization</span></span> | <span data-ttu-id="f674f-231">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-231">Deserialization</span></span> |
|-------------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Immutable.ImmutableArray%601>            | <span data-ttu-id="f674f-232">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-232">✔️</span></span>           | <span data-ttu-id="f674f-233">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-233">✔️</span></span>              |
| <span data-ttu-id="f674f-234"><xref:System.Collections.Immutable.ImmutableDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="f674f-234"><xref:System.Collections.Immutable.ImmutableDictionary%602> \*\*</span></span>  | <span data-ttu-id="f674f-235">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-235">✔️</span></span>           | <span data-ttu-id="f674f-236">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-236">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableHashSet%601>          | <span data-ttu-id="f674f-237">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-237">✔️</span></span>           | <span data-ttu-id="f674f-238">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-238">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>            | <span data-ttu-id="f674f-239">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-239">✔️</span></span>           | <span data-ttu-id="f674f-240">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-240">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableQueue%601>            | <span data-ttu-id="f674f-241">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-241">✔️</span></span>           | <span data-ttu-id="f674f-242">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-242">✔️</span></span>              |
| <span data-ttu-id="f674f-243"><xref:System.Collections.Immutable.ImmutableSortedDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="f674f-243"><xref:System.Collections.Immutable.ImmutableSortedDictionary%602> \*\*</span></span> | <span data-ttu-id="f674f-244">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-244">✔️</span></span>      | <span data-ttu-id="f674f-245">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-245">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableSortedSet%601>        | <span data-ttu-id="f674f-246">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-246">✔️</span></span>           | <span data-ttu-id="f674f-247">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-247">✔️</span></span>              |
| <span data-ttu-id="f674f-248"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="f674f-248"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span></span>         | <span data-ttu-id="f674f-249">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-249">✔️</span></span>           | <span data-ttu-id="f674f-250">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-250">✔️</span></span>              |
| <span data-ttu-id="f674f-251"><xref:System.Collections.Immutable.IImmutableDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="f674f-251"><xref:System.Collections.Immutable.IImmutableDictionary%602> \*\*</span></span> | <span data-ttu-id="f674f-252">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-252">✔️</span></span>           | <span data-ttu-id="f674f-253">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-253">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>            | <span data-ttu-id="f674f-254">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-254">✔️</span></span>           | <span data-ttu-id="f674f-255">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-255">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableQueue%601>           | <span data-ttu-id="f674f-256">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-256">✔️</span></span>           | <span data-ttu-id="f674f-257">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-257">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableSet%601>             | <span data-ttu-id="f674f-258">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-258">✔️</span></span>           | <span data-ttu-id="f674f-259">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-259">✔️</span></span>              |
| <span data-ttu-id="f674f-260"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="f674f-260"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span></span>        | <span data-ttu-id="f674f-261">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-261">✔️</span></span>           | <span data-ttu-id="f674f-262">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-262">✔️</span></span>              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="f674f-263">Type</span><span class="sxs-lookup"><span data-stu-id="f674f-263">Type</span></span>                                                                                                          | <span data-ttu-id="f674f-264">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-264">Serialization</span></span> | <span data-ttu-id="f674f-265">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-265">Deserialization</span></span> |
|---------------------------------------------------------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Immutable.ImmutableArray%601>                                                        | <span data-ttu-id="f674f-266">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-266">✔️</span></span>           | <span data-ttu-id="f674f-267">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-267">✔️</span></span>              |
| <span data-ttu-id="f674f-268">[ImmutableDictionary \<string, TValue> ](xref:System.Collections.Immutable.ImmutableDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="f674f-268">[ImmutableDictionary\<string, TValue>](xref:System.Collections.Immutable.ImmutableDictionary%602) \*\*</span></span>        | <span data-ttu-id="f674f-269">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-269">✔️</span></span>           | <span data-ttu-id="f674f-270">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-270">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableHashSet%601>                                                      | <span data-ttu-id="f674f-271">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-271">✔️</span></span>           | <span data-ttu-id="f674f-272">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-272">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>                                                        | <span data-ttu-id="f674f-273">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-273">✔️</span></span>           | <span data-ttu-id="f674f-274">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-274">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableQueue%601>                                                        | <span data-ttu-id="f674f-275">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-275">✔️</span></span>           | <span data-ttu-id="f674f-276">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-276">✔️</span></span>              |
| <span data-ttu-id="f674f-277">[ImmutableSortedDictionary \<string, TValue> ](xref:System.Collections.Immutable.ImmutableSortedDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="f674f-277">[ImmutableSortedDictionary\<string, TValue>](xref:System.Collections.Immutable.ImmutableSortedDictionary%602) \*\*</span></span>| <span data-ttu-id="f674f-278">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-278">✔️</span></span>       | <span data-ttu-id="f674f-279">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-279">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableSortedSet%601>                                                    | <span data-ttu-id="f674f-280">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-280">✔️</span></span>           | <span data-ttu-id="f674f-281">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-281">✔️</span></span>              |
| <span data-ttu-id="f674f-282"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="f674f-282"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span></span>                                                     | <span data-ttu-id="f674f-283">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-283">✔️</span></span>           | <span data-ttu-id="f674f-284">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-284">✔️</span></span>              |
| <span data-ttu-id="f674f-285">[IImmutableDictionary \<string, TValue> ](xref:System.Collections.Immutable.IImmutableDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="f674f-285">[IImmutableDictionary\<string, TValue>](xref:System.Collections.Immutable.IImmutableDictionary%602) \*\*</span></span>      | <span data-ttu-id="f674f-286">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-286">✔️</span></span>           | <span data-ttu-id="f674f-287">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-287">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>                                                        | <span data-ttu-id="f674f-288">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-288">✔️</span></span>           | <span data-ttu-id="f674f-289">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-289">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableQueue%601>                                                       | <span data-ttu-id="f674f-290">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-290">✔️</span></span>           | <span data-ttu-id="f674f-291">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-291">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableSet%601>                                                         | <span data-ttu-id="f674f-292">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-292">✔️</span></span>           | <span data-ttu-id="f674f-293">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-293">✔️</span></span>              |
| <span data-ttu-id="f674f-294"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="f674f-294"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span></span>                                                    | <span data-ttu-id="f674f-295">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-295">✔️</span></span>           | <span data-ttu-id="f674f-296">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-296">✔️</span></span>              |

::: zone-end

<span data-ttu-id="f674f-297">\*Consultez [prendre en charge l’aller \<T> -retour pour la pile](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="f674f-297">\* See [Support round trip for Stack\<T>](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span></span>

<span data-ttu-id="f674f-298">\*\* Consultez [types de clés pris en charge](#supported-key-types).</span><span class="sxs-lookup"><span data-stu-id="f674f-298">\*\* See [Supported key types](#supported-key-types).</span></span>

## <a name="systemcollectionsspecialized-namespace"></a><span data-ttu-id="f674f-299">Espace de noms System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="f674f-299">System.Collections.Specialized namespace</span></span>

| <span data-ttu-id="f674f-300">Type</span><span class="sxs-lookup"><span data-stu-id="f674f-300">Type</span></span>                                                      | <span data-ttu-id="f674f-301">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-301">Serialization</span></span> | <span data-ttu-id="f674f-302">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-302">Deserialization</span></span> |
|-----------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Specialized.BitVector32>         | <span data-ttu-id="f674f-303">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-303">✔️</span></span>           | ❌\*            |
| <xref:System.Collections.Specialized.HybridDictionary>    | <span data-ttu-id="f674f-304">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-304">✔️</span></span>           | <span data-ttu-id="f674f-305">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-305">✔️</span></span>              |
| <xref:System.Collections.Specialized.IOrderedDictionary>  | <span data-ttu-id="f674f-306">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-306">✔️</span></span>           | ❌              |
| <xref:System.Collections.Specialized.ListDictionary>      | <span data-ttu-id="f674f-307">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-307">✔️</span></span>           | <span data-ttu-id="f674f-308">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-308">✔️</span></span>              |
| <xref:System.Collections.Specialized.StringCollection>    | <span data-ttu-id="f674f-309">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-309">✔️</span></span>           | ❌              |
| <xref:System.Collections.Specialized.StringDictionary>    | <span data-ttu-id="f674f-310">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-310">✔️</span></span>           | ❌              |
| <xref:System.Collections.Specialized.NameValueCollection> | <span data-ttu-id="f674f-311">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-311">✔️</span></span>           | ❌              |

<span data-ttu-id="f674f-312">\* Lorsque <xref:System.Collections.Specialized.BitVector32> est désérialisé, la <xref:System.Collections.Specialized.BitVector32.Data> propriété est ignorée, car elle n’a pas d’accesseur Set public.</span><span class="sxs-lookup"><span data-stu-id="f674f-312">\* When <xref:System.Collections.Specialized.BitVector32> is deserialized, the <xref:System.Collections.Specialized.BitVector32.Data> property is skipped because it doesn't have a public setter.</span></span> <span data-ttu-id="f674f-313">Aucune exception n’est générée.</span><span class="sxs-lookup"><span data-stu-id="f674f-313">No exception is thrown.</span></span>

## <a name="systemcollectionsconcurrent-namespace"></a><span data-ttu-id="f674f-314">Espace de noms System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="f674f-314">System.Collections.Concurrent namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="f674f-315">Type</span><span class="sxs-lookup"><span data-stu-id="f674f-315">Type</span></span>                                                          | <span data-ttu-id="f674f-316">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-316">Serialization</span></span> | <span data-ttu-id="f674f-317">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-317">Deserialization</span></span> |
|---------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Concurrent.BlockingCollection%601>   | <span data-ttu-id="f674f-318">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-318">✔️</span></span>           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentBag%601>        | <span data-ttu-id="f674f-319">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-319">✔️</span></span>           | ❌              |
| <span data-ttu-id="f674f-320"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="f674f-320"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> \*\*</span></span> | <span data-ttu-id="f674f-321">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-321">✔️</span></span>      | <span data-ttu-id="f674f-322">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-322">✔️</span></span>              |
| <xref:System.Collections.Concurrent.ConcurrentQueue%601>      | <span data-ttu-id="f674f-323">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-323">✔️</span></span>           | <span data-ttu-id="f674f-324">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-324">✔️</span></span>              |
| <span data-ttu-id="f674f-325"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="f674f-325"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span>   | <span data-ttu-id="f674f-326">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-326">✔️</span></span>           | <span data-ttu-id="f674f-327">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-327">✔️</span></span>              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="f674f-328">Type</span><span class="sxs-lookup"><span data-stu-id="f674f-328">Type</span></span>                                                        | <span data-ttu-id="f674f-329">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-329">Serialization</span></span> | <span data-ttu-id="f674f-330">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-330">Deserialization</span></span> |
|-------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Concurrent.BlockingCollection%601> | <span data-ttu-id="f674f-331">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-331">✔️</span></span>           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentBag%601>      | <span data-ttu-id="f674f-332">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-332">✔️</span></span>           | ❌              |
| <span data-ttu-id="f674f-333">[ConcurrentDictionary \<string, TValue> ](xref:System.Collections.Concurrent.ConcurrentDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="f674f-333">[ConcurrentDictionary\<string, TValue>](xref:System.Collections.Concurrent.ConcurrentDictionary%602) \*\*</span></span> |<span data-ttu-id="f674f-334">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-334">✔️</span></span>|<span data-ttu-id="f674f-335">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-335">✔️</span></span>|
| <xref:System.Collections.Concurrent.ConcurrentQueue%601>    | <span data-ttu-id="f674f-336">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-336">✔️</span></span>           | <span data-ttu-id="f674f-337">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-337">✔️</span></span>              |
| <span data-ttu-id="f674f-338"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="f674f-338"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span> | <span data-ttu-id="f674f-339">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-339">✔️</span></span>           | <span data-ttu-id="f674f-340">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-340">✔️</span></span>              |

::: zone-end

<span data-ttu-id="f674f-341">\*Consultez [prendre en charge l’aller \<T> -retour pour la pile](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="f674f-341">\* See [Support round trip for Stack\<T>](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span></span>

<span data-ttu-id="f674f-342">\*\* Consultez [types de clés pris en charge](#supported-key-types).</span><span class="sxs-lookup"><span data-stu-id="f674f-342">\*\* See [Supported key types](#supported-key-types).</span></span>

## <a name="systemcollectionsobjectmodel-namespace"></a><span data-ttu-id="f674f-343">Espace de noms System.Collections.ObjectModel</span><span class="sxs-lookup"><span data-stu-id="f674f-343">System.Collections.ObjectModel namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="f674f-344">Type</span><span class="sxs-lookup"><span data-stu-id="f674f-344">Type</span></span>                                                           | <span data-ttu-id="f674f-345">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-345">Serialization</span></span> | <span data-ttu-id="f674f-346">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-346">Deserialization</span></span> |
|----------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ObjectModel.Collection%601>           | <span data-ttu-id="f674f-347">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-347">✔️</span></span>            | <span data-ttu-id="f674f-348">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-348">✔️</span></span>             |
| <span data-ttu-id="f674f-349">[KeyedCollection \<string, TValue> ](xref:System.Collections.ObjectModel.KeyedCollection%602)\*</span><span class="sxs-lookup"><span data-stu-id="f674f-349">[KeyedCollection\<string, TValue>](xref:System.Collections.ObjectModel.KeyedCollection%602) \*</span></span> |<span data-ttu-id="f674f-350">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-350">✔️</span></span>|❌|
| <xref:System.Collections.ObjectModel.ObservableCollection%601> | <span data-ttu-id="f674f-351">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-351">✔️</span></span>            | <span data-ttu-id="f674f-352">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-352">✔️</span></span>             |
| <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>   | <span data-ttu-id="f674f-353">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-353">✔️</span></span>            | ❌             |
| <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602>   | <span data-ttu-id="f674f-354">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-354">✔️</span></span>            | ❌             |
| <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601> | <span data-ttu-id="f674f-355">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-355">✔️</span></span>    | ❌             |

<span data-ttu-id="f674f-356">\* Les non- `string` clés ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="f674f-356">\* Non-`string` keys are not supported.</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="f674f-357">Type</span><span class="sxs-lookup"><span data-stu-id="f674f-357">Type</span></span>                                                           | <span data-ttu-id="f674f-358">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-358">Serialization</span></span> | <span data-ttu-id="f674f-359">Désérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-359">Deserialization</span></span> |
|----------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ObjectModel.Collection%601>           | <span data-ttu-id="f674f-360">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-360">✔️</span></span>            | <span data-ttu-id="f674f-361">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-361">✔️</span></span>             |
| <span data-ttu-id="f674f-362">[KeyedCollection \<string, TValue> ](xref:System.Collections.ObjectModel.KeyedCollection%602)\*</span><span class="sxs-lookup"><span data-stu-id="f674f-362">[KeyedCollection\<string, TValue>](xref:System.Collections.ObjectModel.KeyedCollection%602) \*</span></span> |<span data-ttu-id="f674f-363">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-363">✔️</span></span>|❌|
| <xref:System.Collections.ObjectModel.ObservableCollection%601> | <span data-ttu-id="f674f-364">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-364">✔️</span></span>            | <span data-ttu-id="f674f-365">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-365">✔️</span></span>             |
| <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>   | <span data-ttu-id="f674f-366">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-366">✔️</span></span>            | ❌             |
| <span data-ttu-id="f674f-367">[Objet ReadOnlyDictionary \<string, TValue> ](xref:System.Collections.ObjectModel.ReadOnlyDictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="f674f-367">[ReadOnlyDictionary\<string, TValue>](xref:System.Collections.ObjectModel.ReadOnlyDictionary%602) \*</span></span> |<span data-ttu-id="f674f-368">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-368">✔️</span></span>|❌|
| <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601>| <span data-ttu-id="f674f-369">✔️</span><span class="sxs-lookup"><span data-stu-id="f674f-369">✔️</span></span>     | ❌             |

<span data-ttu-id="f674f-370">\* Consultez [types de clés pris en charge](#supported-key-types).</span><span class="sxs-lookup"><span data-stu-id="f674f-370">\* See [Supported key types](#supported-key-types).</span></span>

::: zone-end

## <a name="custom-collections"></a><span data-ttu-id="f674f-371">Regroupements personnalisés</span><span class="sxs-lookup"><span data-stu-id="f674f-371">Custom collections</span></span>

<span data-ttu-id="f674f-372">Tout type de collection qui n’est pas dans l’un des espaces de noms précédents est considéré comme une collection personnalisée.</span><span class="sxs-lookup"><span data-stu-id="f674f-372">Any collection type that isn't in one of the preceding namespaces is considered a custom collection.</span></span> <span data-ttu-id="f674f-373">Ces types incluent des types définis par l’utilisateur et des types définis par ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f674f-373">Such types include user-defined types and types defined by ASP.NET Core.</span></span> <span data-ttu-id="f674f-374">Par exemple, <xref:Microsoft.Extensions.Primitives?displayProperty=fullName> se trouve dans ce groupe.</span><span class="sxs-lookup"><span data-stu-id="f674f-374">For example, <xref:Microsoft.Extensions.Primitives?displayProperty=fullName> is in this group.</span></span>

<span data-ttu-id="f674f-375">Toutes les collections personnalisées (tout ce qui dérive de `IEnumerable` ) sont prises en charge pour la sérialisation, à condition que leurs types d’éléments soient pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f674f-375">All custom collections (everything that derives from `IEnumerable`) are supported for serialization, as long as their element types are supported.</span></span>

### <a name="custom-collections-with-deserialization-support"></a><span data-ttu-id="f674f-376">Collections personnalisées avec prise en charge de la désérialisation</span><span class="sxs-lookup"><span data-stu-id="f674f-376">Custom collections with deserialization support</span></span>

<span data-ttu-id="f674f-377">Une collection personnalisée est prise en charge pour la désérialisation si :</span><span class="sxs-lookup"><span data-stu-id="f674f-377">A custom collection is supported for deserialization if it:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="f674f-378">N’est pas une interface ni abstraite.</span><span class="sxs-lookup"><span data-stu-id="f674f-378">Isn't an interface or abstract.</span></span>
* <span data-ttu-id="f674f-379">A un constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="f674f-379">Has a parameterless constructor.</span></span>
* <span data-ttu-id="f674f-380">Contient les types d’éléments pris en charge par <xref:System.Text.Json.JsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="f674f-380">Contains element types that are supported by <xref:System.Text.Json.JsonSerializer>.</span></span>
* <span data-ttu-id="f674f-381">Implémente ou hérite d’une ou plusieurs des interfaces ou classes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f674f-381">Implements or inherits one or more of the following interfaces or classes:</span></span>
  * <xref:System.Collections.Concurrent.ConcurrentQueue%601>
  * <span data-ttu-id="f674f-382"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="f674f-382"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span>
  * <xref:System.Collections.Generic.ICollection%601>
  * <xref:System.Collections.IDictionary>
  * <span data-ttu-id="f674f-383"><xref:System.Collections.Generic.IDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="f674f-383"><xref:System.Collections.Generic.IDictionary%602> \*\*</span></span>
  * <xref:System.Collections.IList>
  * <xref:System.Collections.Generic.IList%601>
  * <xref:System.Collections.Queue>
  * <xref:System.Collections.Generic.Queue%601>
  * <span data-ttu-id="f674f-384"><xref:System.Collections.Stack> \*</span><span class="sxs-lookup"><span data-stu-id="f674f-384"><xref:System.Collections.Stack> \*</span></span>
  * <span data-ttu-id="f674f-385"><xref:System.Collections.Generic.Stack%601> \*</span><span class="sxs-lookup"><span data-stu-id="f674f-385"><xref:System.Collections.Generic.Stack%601> \*</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="f674f-386">N’est pas une interface ni abstraite.</span><span class="sxs-lookup"><span data-stu-id="f674f-386">Isn't an interface or abstract.</span></span>
* <span data-ttu-id="f674f-387">A un constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="f674f-387">Has a parameterless constructor.</span></span>
* <span data-ttu-id="f674f-388">Contient les types d’éléments pris en charge par <xref:System.Text.Json.JsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="f674f-388">Contains element types that are supported by <xref:System.Text.Json.JsonSerializer>.</span></span>
* <span data-ttu-id="f674f-389">Implémente ou hérite d’une ou plusieurs des interfaces ou classes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f674f-389">Implements or inherits one or more of the following interfaces or classes:</span></span>
  * <xref:System.Collections.Concurrent.ConcurrentQueue%601>
  * <span data-ttu-id="f674f-390"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="f674f-390"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span>
  * <xref:System.Collections.Generic.ICollection%601>
  * <xref:System.Collections.IDictionary>
  * <span data-ttu-id="f674f-391">[IDictionary\<string, TValue>](xref:System.Collections.Generic.IDictionary%602) \* \*</span><span class="sxs-lookup"><span data-stu-id="f674f-391">[IDictionary\<string, TValue>](xref:System.Collections.Generic.IDictionary%602) \*\*</span></span>
  * <xref:System.Collections.IList>
  * <xref:System.Collections.Generic.IList%601>
  * <xref:System.Collections.Queue>
  * <xref:System.Collections.Generic.Queue%601>
  * <span data-ttu-id="f674f-392"><xref:System.Collections.Stack> \*</span><span class="sxs-lookup"><span data-stu-id="f674f-392"><xref:System.Collections.Stack> \*</span></span>
  * <span data-ttu-id="f674f-393"><xref:System.Collections.Generic.Stack%601> \*</span><span class="sxs-lookup"><span data-stu-id="f674f-393"><xref:System.Collections.Generic.Stack%601> \*</span></span>

::: zone-end

  <span data-ttu-id="f674f-394">\*Consultez [prendre en charge l’aller \<T> -retour pour la pile](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="f674f-394">\* See [Support round trip for Stack\<T>](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span></span>

  <span data-ttu-id="f674f-395">\*\* Consultez [types de clés pris en charge](#supported-key-types).</span><span class="sxs-lookup"><span data-stu-id="f674f-395">\*\* See [Supported key types](#supported-key-types).</span></span>

### <a name="custom-collections-with-known-issues"></a><span data-ttu-id="f674f-396">Regroupements personnalisés avec problèmes connus</span><span class="sxs-lookup"><span data-stu-id="f674f-396">Custom collections with known issues</span></span>

<span data-ttu-id="f674f-397">Il existe des problèmes connus avec les regroupements personnalisés suivants :</span><span class="sxs-lookup"><span data-stu-id="f674f-397">There are known issues with the following custom collections:</span></span>

- <span data-ttu-id="f674f-398"><xref:System.Dynamic.ExpandoObject>: Consultez [dotnet/Runtime # 29690](https://github.com/dotnet/runtime/issues/29690).</span><span class="sxs-lookup"><span data-stu-id="f674f-398"><xref:System.Dynamic.ExpandoObject>: See [dotnet/runtime#29690](https://github.com/dotnet/runtime/issues/29690).</span></span>
- <span data-ttu-id="f674f-399"><xref:System.Dynamic.DynamicObject>: Consultez [dotnet/Runtime # 1808](https://github.com/dotnet/runtime/issues/1808).</span><span class="sxs-lookup"><span data-stu-id="f674f-399"><xref:System.Dynamic.DynamicObject>: See [dotnet/runtime#1808](https://github.com/dotnet/runtime/issues/1808).</span></span>
- <span data-ttu-id="f674f-400"><xref:System.Data.DataTable>: Consultez [dotnet/docs # 21366](https://github.com/dotnet/docs/issues/21366).</span><span class="sxs-lookup"><span data-stu-id="f674f-400"><xref:System.Data.DataTable>: See [dotnet/docs#21366](https://github.com/dotnet/docs/issues/21366).</span></span>
- <span data-ttu-id="f674f-401"><xref:Microsoft.AspNetCore.Http.FormFile?displayProperty=fullName>: Consultez [dotnet/Runtime # 1559](https://github.com/dotnet/runtime/issues/1559).</span><span class="sxs-lookup"><span data-stu-id="f674f-401"><xref:Microsoft.AspNetCore.Http.FormFile?displayProperty=fullName>: See [dotnet/runtime#1559](https://github.com/dotnet/runtime/issues/1559).</span></span>
- <span data-ttu-id="f674f-402"><xref:Microsoft.AspNetCore.Http.IFormCollection?displayProperty=fullName>: Consultez [dotnet/Runtime # 1559](https://github.com/dotnet/runtime/issues/1559).</span><span class="sxs-lookup"><span data-stu-id="f674f-402"><xref:Microsoft.AspNetCore.Http.IFormCollection?displayProperty=fullName>: See [dotnet/runtime#1559](https://github.com/dotnet/runtime/issues/1559).</span></span>

<span data-ttu-id="f674f-403">Pour plus d’informations sur les problèmes connus, consultez la rubrique [problèmes ouverts dans System.Text.Json ](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json).</span><span class="sxs-lookup"><span data-stu-id="f674f-403">For more information about known issues, see the [open issues in System.Text.Json](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json).</span></span>

## <a name="supported-key-types"></a><span data-ttu-id="f674f-404">Types de clé pris en charge</span><span class="sxs-lookup"><span data-stu-id="f674f-404">Supported key types</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="f674f-405">Les types pris en charge pour les clés `Dictionary` et `SortedList` sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="f674f-405">Supported types for the keys of `Dictionary` and `SortedList` types include the following:</span></span>

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
* <span data-ttu-id="f674f-406">`Object` (Uniquement lors de la sérialisation et si le type de Runtime est l’un des types pris en charge dans cette liste.)</span><span class="sxs-lookup"><span data-stu-id="f674f-406">`Object` (Only on serialization and if the runtime type is one of the supported types in this list.)</span></span>
* `SByte`
* `Single`
* `String`
* `UInt16`
* `UInt32`
* `UInt64`

::: zone-end

::: zone pivot="dotnet-core-3-1"

<span data-ttu-id="f674f-407">\*\* Les non- `string` clés pour les `Dictionary` types et ne `SortedList` sont pas prises en charge dans .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="f674f-407">\*\* Non-`string` keys for `Dictionary` and `SortedList` types are not supported in .NET Core 3.1.</span></span>

::: zone-end

## <a name="see-also"></a><span data-ttu-id="f674f-408">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f674f-408">See also</span></span>

* [<span data-ttu-id="f674f-409">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="f674f-409">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="f674f-410">Instancier des instances JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="f674f-410">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="f674f-411">Activer la correspondance non sensible à la casse</span><span class="sxs-lookup"><span data-stu-id="f674f-411">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="f674f-412">Personnaliser les noms et valeurs de propriété</span><span class="sxs-lookup"><span data-stu-id="f674f-412">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="f674f-413">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="f674f-413">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="f674f-414">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="f674f-414">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="f674f-415">Gérer le JSON de dépassement</span><span class="sxs-lookup"><span data-stu-id="f674f-415">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="f674f-416">Préserver les références</span><span class="sxs-lookup"><span data-stu-id="f674f-416">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="f674f-417">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="f674f-417">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="f674f-418">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="f674f-418">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="f674f-419">Migrer de Newtonsoft.Jsvers System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="f674f-419">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="f674f-420">Personnaliser l’encodage de caractères</span><span class="sxs-lookup"><span data-stu-id="f674f-420">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="f674f-421">Écrire des sérialiseurs et des désérialiseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="f674f-421">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="f674f-422">Écrire des convertisseurs personnalisés pour la sérialisation JSON</span><span class="sxs-lookup"><span data-stu-id="f674f-422">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="f674f-423">Prise en charge DateTime et DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="f674f-423">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="f674f-424">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="f674f-424">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="f674f-425">[System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="f674f-425">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
