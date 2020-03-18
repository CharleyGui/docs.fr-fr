---
title: Exécution d'opérations de chaînes indépendantes de la culture
ms.date: 08/22/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- case mappings
- custom case mappings
- culture, custom sorting rules
- custom sorting rules
- culture-insensitive string operations, options for performing
- culture, custom case mappings
- culture-insensitive string operations, method overloads
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
ms.openlocfilehash: 183078b1f7a3eb3530fea8af06dbb59055d7d25d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120797"
---
# <a name="performing-culture-insensitive-string-operations"></a><span data-ttu-id="1f9c3-102">Exécution d’opérations de chaînes indépendantes de la culture</span><span class="sxs-lookup"><span data-stu-id="1f9c3-102">Performing culture-insensitive string operations</span></span>
<span data-ttu-id="1f9c3-103">La plupart des méthodes .NET Framework qui exécutent des opérations de chaînes dépendantes de la culture fournissent par défaut des surcharges de méthode qui vous permettent de spécifier explicitement la culture à utiliser en passant un paramètre <xref:System.Globalization.CultureInfo>.</span><span class="sxs-lookup"><span data-stu-id="1f9c3-103">Most .NET Framework methods that perform culture-sensitive string operations by default provide method overloads that allow you to explicitly specify the culture to use by passing a <xref:System.Globalization.CultureInfo> parameter.</span></span> <span data-ttu-id="1f9c3-104">Ces surcharges vous permettent d’éliminer les différences culturelles dans les règles de mappages et de tri de casse et de garantir des résultats indépendants de la culture.</span><span class="sxs-lookup"><span data-stu-id="1f9c3-104">These overloads allow you to eliminate cultural variations in case mappings and sorting rules and guarantee culture-insensitive results.</span></span>  
  
 <span data-ttu-id="1f9c3-105">Cette section fournit les rubriques suivantes pour montrer comment exécuter des opérations de chaînes indépendantes de la culture à l’aide de méthodes .NET Framework qui sont dépendantes de la culture par défaut.</span><span class="sxs-lookup"><span data-stu-id="1f9c3-105">This section provides the following topics to demonstrate how to perform culture-insensitive string operations using .NET Framework methods that are culture-sensitive by default.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1f9c3-106">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="1f9c3-106">In this section</span></span>  
 [<span data-ttu-id="1f9c3-107">Exécution de comparaisons de chaînes indépendantes de la culture</span><span class="sxs-lookup"><span data-stu-id="1f9c3-107">Performing Culture-Insensitive String Comparisons</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 <span data-ttu-id="1f9c3-108">Décrit comment utiliser les méthodes <xref:System.String.Compare%2A?displayProperty=nameWithType> et <xref:System.String.CompareTo%2A?displayProperty=nameWithType> pour effectuer des comparaisons de chaînes indépendantes de la culture.</span><span class="sxs-lookup"><span data-stu-id="1f9c3-108">Describes how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> and <xref:System.String.CompareTo%2A?displayProperty=nameWithType> methods to perform culture-insensitive string comparisons.</span></span>  
  
 [<span data-ttu-id="1f9c3-109">Exécution de changements de casse indépendants de la culture</span><span class="sxs-lookup"><span data-stu-id="1f9c3-109">Performing Culture-Insensitive Case Changes</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 <span data-ttu-id="1f9c3-110">Décrit comment utiliser les méthodes <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType> et <xref:System.Char.ToLower%2A?displayProperty=nameWithType> pour effectuer des changements de casse indépendants de la culture.</span><span class="sxs-lookup"><span data-stu-id="1f9c3-110">Describes how to use the <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods to perform culture-insensitive case changes.</span></span>  
  
 [<span data-ttu-id="1f9c3-111">Exécution d’opérations de chaînes indépendantes de la culture dans des collections</span><span class="sxs-lookup"><span data-stu-id="1f9c3-111">Performing Culture-Insensitive String Operations in Collections</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 <span data-ttu-id="1f9c3-112">Décrit comment utiliser <xref:System.Collections.CaseInsensitiveComparer>, la classe <xref:System.Collections.CaseInsensitiveHashCodeProvider> ainsi que <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> et <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> pour effectuer des opérations indépendantes de la culture dans des collections.</span><span class="sxs-lookup"><span data-stu-id="1f9c3-112">Describes how to use the <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> and <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> to perform culture-insensitive operations in collections.</span></span>  
  
 [<span data-ttu-id="1f9c3-113">Exécution d'opérations de chaînes indépendantes de la culture dans des tableaux</span><span class="sxs-lookup"><span data-stu-id="1f9c3-113">Performing Culture-Insensitive String Operations in Arrays</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 <span data-ttu-id="1f9c3-114">Décrit comment utiliser les méthodes <xref:System.Array.Sort%2A?displayProperty=nameWithType> et <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> pour effectuer des opérations indépendantes de la culture dans des tableaux.</span><span class="sxs-lookup"><span data-stu-id="1f9c3-114">Describes how to use the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods to perform culture-insensitive operations in arrays.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1f9c3-115">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="1f9c3-115">Related sections</span></span>  
 [<span data-ttu-id="1f9c3-116">Opérations à cordes culturelles insensibles</span><span class="sxs-lookup"><span data-stu-id="1f9c3-116">Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 <span data-ttu-id="1f9c3-117">Décrit pourquoi vous devez connaître la culture lorsque vous exécutez des opérations sur des chaînes et fournit des recommandations sur l’exécution d’opérations dépendantes de la culture et l’exécution d’opérations indépendantes de la culture.</span><span class="sxs-lookup"><span data-stu-id="1f9c3-117">Describes why you should be aware of culture when performing operations on strings and provides guidelines for when to perform culture-sensitive operations and when to perform culture-insensitive operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f9c3-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f9c3-118">See also</span></span>

- [<span data-ttu-id="1f9c3-119">Sorting Weight Tables (pour .NET sur systèmes Windows)</span><span class="sxs-lookup"><span data-stu-id="1f9c3-119">Sorting Weight Tables (for .NET on Windows systems)</span></span>](https://www.microsoft.com/download/details.aspx?id=10921)
- [<span data-ttu-id="1f9c3-120">Default Unicode Collation Element Table (pour .NET Core sur Linux et macOS)</span><span class="sxs-lookup"><span data-stu-id="1f9c3-120">Default Unicode Collation Element Table (for .NET Core on Linux and macOS)</span></span>](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
