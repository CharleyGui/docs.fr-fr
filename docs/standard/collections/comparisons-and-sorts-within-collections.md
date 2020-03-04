---
title: Comparaisons et tris dans les collections
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data, collections
- IComparable.CompareTo method
- Collections classes
- Equals method
- collections [.NET Framework], comparisons
ms.assetid: 5e4d3b45-97f0-423c-a65f-c492ed40e73b
ms.openlocfilehash: 3360652f22ed39ccfd99f9863052fe584b78562f
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159258"
---
# <a name="comparisons-and-sorts-within-collections"></a>Comparaisons et tris dans les collections
Les classes <xref:System.Collections> effectuent des comparaisons dans quasiment tous les processus impliqués dans la gestion des collections, que ce soit pendant la recherche d'un élément à supprimer ou le renvoi d'une valeur d'une paire clé-valeur.  
  
 Les collections utilisent généralement un comparateur d'égalité et/ou un comparateur de classement. Deux constructions sont utilisées pour les comparaisons.  
  
<a name="BKMK_Checkingforequality"></a>
## <a name="checking-for-equality"></a>Vérification de l'égalité  
 Les méthodes telles que `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A> et `Remove` utilisent un comparateur d'égalité pour les éléments de collection. Si la collection est générique, les éléments font l’objet d’une comparaison d’égalité, selon les consignes suivantes :  
  
- Si le type T implémente l'interface générique <xref:System.IEquatable%601> , le comparateur d'égalité est la méthode <xref:System.IEquatable%601.Equals%2A> de cette interface.  
  
- Si le type T n'implémente pas <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> est utilisé.  
  
 De plus, certaines surcharges de constructeur pour les collections de dictionnaires acceptent une implémentation <xref:System.Collections.Generic.IEqualityComparer%601>, qui est utilisée pour comparer l'égalité de clés. Pour obtenir un exemple, consultez le constructeur <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> .  
  
<a name="BKMK_Determiningsortorder"></a>
## <a name="determining-sort-order"></a>Détermination de l'ordre de tri  
 Les méthodes telles que `BinarySearch` et `Sort` utilisent un comparateur de classement pour les éléments de collection. Les comparaisons peuvent être effectuées entre les éléments d’une collection, ou entre un élément et une valeur spécifiée. Pour comparer des objets, il existe le `default comparer` et le `explicit comparer`.  
  
 Le comparateur par défaut repose sur au moins l'un des objets comparés pour implémenter l'interface **IComparable** . Il est recommandé d'implémenter **IComparable** sur toutes les classes utilisées en tant que valeurs dans une collection de listes ou en tant que clés dans une collection de dictionnaires. Pour une collection générique, la comparaison d’égalité est déterminée selon ce qui suit :  
  
- Si le type T implémente l'interface générique <xref:System.IComparable%601?displayProperty=nameWithType> , le comparateur par défaut est la méthode <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> de cette interface.  
  
- Si le type T implémente l'interface non générique <xref:System.IComparable?displayProperty=nameWithType> , le comparateur par défaut est la méthode <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> de cette interface.  
  
- Si le type T n'implémente aucune interface, il n'existe aucun comparateur par défaut. Un comparateur ou un délégué de comparaison doit donc être fourni explicitement.  
  
 Pour fournir des comparaisons explicites, certaines méthodes acceptent une implémentation **IComparer** en tant que paramètre. Par exemple, la méthode <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> accepte une implémentation <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> .  
  
 Le paramètre de culture actuel du système peut affecter les comparaisons et les tris d'une collection. Par défaut, les comparaisons et les tris des classes **Collections** sont dépendants de la culture. Pour ignorer le paramètre de culture et donc obtenir des résultats cohérents de comparaison et de tri, utilisez <xref:System.Globalization.CultureInfo.InvariantCulture%2A> avec des surcharges de membre qui acceptent <xref:System.Globalization.CultureInfo>. Pour plus d’informations, consultez [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) et [Performing Culture-Insensitive String Operations in Arrays](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).  
  
<a name="BKMK_Equalityandsortexample"></a>
## <a name="equality-and-sort-example"></a>Exemple d'égalité et de tri  
 Le code suivant illustre une implémentation de <xref:System.IEquatable%601> et de <xref:System.IComparable%601> dans un objet métier simple. De plus, quand l'objet est stocké dans une liste, puis trié, vous verrez que l'appel de la méthode <xref:System.Collections.Generic.List%601.Sort> se traduit par l'utilisation du comparateur par défaut pour le type `Part` , et par l'implémentation de la méthode <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> à l'aide d'une méthode anonyme.  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.IComparer>
- <xref:System.IEquatable%601>
- <xref:System.Collections.Generic.IComparer%601>
- <xref:System.IComparable>
- <xref:System.IComparable%601>
