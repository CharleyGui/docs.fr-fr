---
title: Exécution d'opérations de chaînes indépendantes de la culture
ms.date: 08/22/2018
helpviewer_keywords:
- case mappings
- custom case mappings
- culture, custom sorting rules
- custom sorting rules
- culture-insensitive string operations, options for performing
- culture, custom case mappings
- culture-insensitive string operations, method overloads
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
ms.openlocfilehash: 868f36a1025f0b121a8765edf50bb42679736240
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829763"
---
# <a name="performing-culture-insensitive-string-operations"></a><span data-ttu-id="1b367-102">Exécution d’opérations de chaînes indépendantes de la culture</span><span class="sxs-lookup"><span data-stu-id="1b367-102">Performing culture-insensitive string operations</span></span>

<span data-ttu-id="1b367-103">La plupart des méthodes .NET qui effectuent des opérations de chaînes dépendantes de la culture fournissent par défaut des surcharges de méthode qui vous permettent de spécifier explicitement la culture à utiliser en passant un <xref:System.Globalization.CultureInfo> paramètre.</span><span class="sxs-lookup"><span data-stu-id="1b367-103">Most .NET methods that perform culture-sensitive string operations by default provide method overloads that allow you to explicitly specify the culture to use by passing a <xref:System.Globalization.CultureInfo> parameter.</span></span> <span data-ttu-id="1b367-104">Ces surcharges vous permettent d’éliminer les différences culturelles dans les règles de mappages et de tri de casse et de garantir des résultats indépendants de la culture.</span><span class="sxs-lookup"><span data-stu-id="1b367-104">These overloads allow you to eliminate cultural variations in case mappings and sorting rules and guarantee culture-insensitive results.</span></span>  
  
 <span data-ttu-id="1b367-105">Cette section fournit les articles suivants pour illustrer comment effectuer des opérations de chaînes indépendantes de la culture à l’aide de méthodes .NET qui sont dépendantes de la culture par défaut.</span><span class="sxs-lookup"><span data-stu-id="1b367-105">This section provides the following articles to demonstrate how to perform culture-insensitive string operations using .NET methods that are culture-sensitive by default.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1b367-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1b367-106">In this section</span></span>  
 [<span data-ttu-id="1b367-107">Exécution de comparaisons de chaînes indépendantes de la culture</span><span class="sxs-lookup"><span data-stu-id="1b367-107">Performing Culture-Insensitive String Comparisons</span></span>](performing-culture-insensitive-string-comparisons.md)  
 <span data-ttu-id="1b367-108">Décrit comment utiliser les méthodes <xref:System.String.Compare%2A?displayProperty=nameWithType> et <xref:System.String.CompareTo%2A?displayProperty=nameWithType> pour effectuer des comparaisons de chaînes indépendantes de la culture.</span><span class="sxs-lookup"><span data-stu-id="1b367-108">Describes how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> and <xref:System.String.CompareTo%2A?displayProperty=nameWithType> methods to perform culture-insensitive string comparisons.</span></span>  
  
 [<span data-ttu-id="1b367-109">Exécution de changements de casse indépendants de la culture</span><span class="sxs-lookup"><span data-stu-id="1b367-109">Performing Culture-Insensitive Case Changes</span></span>](performing-culture-insensitive-case-changes.md)  
 <span data-ttu-id="1b367-110">Décrit comment utiliser les méthodes <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType> et <xref:System.Char.ToLower%2A?displayProperty=nameWithType> pour effectuer des changements de casse indépendants de la culture.</span><span class="sxs-lookup"><span data-stu-id="1b367-110">Describes how to use the <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods to perform culture-insensitive case changes.</span></span>  
  
 [<span data-ttu-id="1b367-111">Exécution d’opérations de chaînes indépendantes de la culture dans des collections</span><span class="sxs-lookup"><span data-stu-id="1b367-111">Performing Culture-Insensitive String Operations in Collections</span></span>](performing-culture-insensitive-string-operations-in-collections.md)  
 <span data-ttu-id="1b367-112">Décrit comment utiliser <xref:System.Collections.CaseInsensitiveComparer>, la classe <xref:System.Collections.CaseInsensitiveHashCodeProvider> ainsi que <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> et <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> pour effectuer des opérations indépendantes de la culture dans des collections.</span><span class="sxs-lookup"><span data-stu-id="1b367-112">Describes how to use the <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> and <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> to perform culture-insensitive operations in collections.</span></span>  
  
 [<span data-ttu-id="1b367-113">Exécution d'opérations de chaînes indépendantes de la culture dans des tableaux</span><span class="sxs-lookup"><span data-stu-id="1b367-113">Performing Culture-Insensitive String Operations in Arrays</span></span>](performing-culture-insensitive-string-operations-in-arrays.md)  
 <span data-ttu-id="1b367-114">Décrit comment utiliser les méthodes <xref:System.Array.Sort%2A?displayProperty=nameWithType> et <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> pour effectuer des opérations indépendantes de la culture dans des tableaux.</span><span class="sxs-lookup"><span data-stu-id="1b367-114">Describes how to use the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods to perform culture-insensitive operations in arrays.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1b367-115">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="1b367-115">Related sections</span></span>  
 [<span data-ttu-id="1b367-116">Opérations de chaînes indépendantes de la culture</span><span class="sxs-lookup"><span data-stu-id="1b367-116">Culture-Insensitive String Operations</span></span>](culture-insensitive-string-operations.md)  
 <span data-ttu-id="1b367-117">Décrit pourquoi vous devez connaître la culture lorsque vous exécutez des opérations sur des chaînes et fournit des recommandations sur l’exécution d’opérations dépendantes de la culture et l’exécution d’opérations indépendantes de la culture.</span><span class="sxs-lookup"><span data-stu-id="1b367-117">Describes why you should be aware of culture when performing operations on strings and provides guidelines for when to perform culture-sensitive operations and when to perform culture-insensitive operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b367-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b367-118">See also</span></span>

- [<span data-ttu-id="1b367-119">Sorting Weight Tables (pour .NET sur systèmes Windows)</span><span class="sxs-lookup"><span data-stu-id="1b367-119">Sorting Weight Tables (for .NET on Windows systems)</span></span>](https://www.microsoft.com/download/details.aspx?id=10921)
- [<span data-ttu-id="1b367-120">Default Unicode Collation Element Table (pour .NET Core sur Linux et macOS)</span><span class="sxs-lookup"><span data-stu-id="1b367-120">Default Unicode Collation Element Table (for .NET Core on Linux and macOS)</span></span>](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
