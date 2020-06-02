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
ms.openlocfilehash: 79ff899e2964ae2c1e90b7178616c612dddf6d86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287504"
---
# <a name="performing-culture-insensitive-string-operations"></a>Exécution d’opérations de chaînes indépendantes de la culture
La plupart des méthodes .NET Framework qui exécutent des opérations de chaînes dépendantes de la culture fournissent par défaut des surcharges de méthode qui vous permettent de spécifier explicitement la culture à utiliser en passant un paramètre <xref:System.Globalization.CultureInfo>. Ces surcharges vous permettent d’éliminer les différences culturelles dans les règles de mappages et de tri de casse et de garantir des résultats indépendants de la culture.  
  
 Cette section fournit les rubriques suivantes pour montrer comment exécuter des opérations de chaînes indépendantes de la culture à l’aide de méthodes .NET Framework qui sont dépendantes de la culture par défaut.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Exécution de comparaisons de chaînes indépendantes de la culture](performing-culture-insensitive-string-comparisons.md)  
 Décrit comment utiliser les méthodes <xref:System.String.Compare%2A?displayProperty=nameWithType> et <xref:System.String.CompareTo%2A?displayProperty=nameWithType> pour effectuer des comparaisons de chaînes indépendantes de la culture.  
  
 [Exécution de changements de casse indépendants de la culture](performing-culture-insensitive-case-changes.md)  
 Décrit comment utiliser les méthodes <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType> et <xref:System.Char.ToLower%2A?displayProperty=nameWithType> pour effectuer des changements de casse indépendants de la culture.  
  
 [Exécution d’opérations de chaînes indépendantes de la culture dans des collections](performing-culture-insensitive-string-operations-in-collections.md)  
 Décrit comment utiliser <xref:System.Collections.CaseInsensitiveComparer>, la classe <xref:System.Collections.CaseInsensitiveHashCodeProvider> ainsi que <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> et <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> pour effectuer des opérations indépendantes de la culture dans des collections.  
  
 [Exécution d'opérations de chaînes indépendantes de la culture dans des tableaux](performing-culture-insensitive-string-operations-in-arrays.md)  
 Décrit comment utiliser les méthodes <xref:System.Array.Sort%2A?displayProperty=nameWithType> et <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> pour effectuer des opérations indépendantes de la culture dans des tableaux.  
  
## <a name="related-sections"></a>Sections connexes  
 [Opérations de chaînes indépendantes de la culture](culture-insensitive-string-operations.md)  
 Décrit pourquoi vous devez connaître la culture lorsque vous exécutez des opérations sur des chaînes et fournit des recommandations sur l’exécution d’opérations dépendantes de la culture et l’exécution d’opérations indépendantes de la culture.

## <a name="see-also"></a>Voir aussi

- [Sorting Weight Tables (pour .NET sur systèmes Windows)](https://www.microsoft.com/download/details.aspx?id=10921)
- [Default Unicode Collation Element Table (pour .NET Core sur Linux et macOS)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
