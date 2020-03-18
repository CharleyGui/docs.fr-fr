---
title: Exécution d'opérations de chaînes indépendantes de la culture dans des tableaux
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
ms.openlocfilehash: 051ee77ae5d6552e26e0216d58734d90188475f9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120809"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Exécution d'opérations de chaînes indépendantes de la culture dans des tableaux

Les surcharges des méthodes <xref:System.Array.Sort%2A?displayProperty=nameWithType> et <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> effectuent des tris dépendants de la culture par défaut à l’aide de la propriété <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType>. Les résultats dépendants de la culture retournés par ces méthodes peuvent varier selon la culture en raison de différences dans les ordres de tri. Pour supprimer un comportement dépendant de la culture, utilisez l’une des surcharges de cette méthode qui accepte un paramètre `comparer`. Le paramètre `comparer` spécifie l’implémentation <xref:System.Collections.IComparer> à utiliser lors de la comparaison d’éléments dans le tableau. Pour le paramètre, spécifiez une classe de comparateur indifférent personnalisée qui utilise <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Un exemple d’une classe de comparateur indifférent personnalisée est fourni dans la sous-rubrique « Utilisation de la classe SortedList » de la rubrique [Exécution d'opérations de chaînes indépendantes de la culture dans des collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md).

> [!NOTE]
> Passer **CultureInfo.InvariantCulture** à une méthode de comparaison effectue une comparaison culturelle-insensible. Toutefois, elle n’entraîne pas une comparaison non linguistique, par exemple, pour les chemins d’accès de fichier, les clés de Registre et les variables d’environnement. Elle ne prend pas non plus en charge les décisions de sécurité basées sur le résultat de la comparaison. Pour une comparaison non linguistique ou la prise en charge des décisions de sécurité basées sur le résultat, l’application doit utiliser une méthode de comparaison qui accepte une valeur <xref:System.StringComparison>. L’application doit ensuite transmettre <xref:System.StringComparison.Ordinal>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>
- <xref:System.Collections.IComparer>
- [Exécution d’opérations de chaînes indépendantes de la culture](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
