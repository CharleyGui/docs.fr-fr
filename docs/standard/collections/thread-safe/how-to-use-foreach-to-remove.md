---
title: Utiliser foreach pour supprimer des éléments dans un BlockingCollection
ms.date: 05/04/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collection
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
ms.openlocfilehash: 1255fcda89396ea8ff9abf6cf111e6dd9ea5a87d
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82861013"
---
# <a name="use-foreach-to-remove-items-in-a-blockingcollection"></a>Utiliser foreach pour supprimer des éléments dans un BlockingCollection

En plus de la suppression d’éléments <xref:System.Collections.Concurrent.BlockingCollection%601> d’un à <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> l' <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> aide de la méthode et, vous pouvez également utiliser une [boucle foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([for each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) dans Visual Basic) avec <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> pour supprimer des éléments jusqu’à ce que l’ajout soit terminé et que la collection soit vide. Cela s’appelle une *énumération de mutation* ou *énumération de consommation* car, contrairement à une boucle `foreach` (`For Each`) typique, cet énumérateur modifie la collection source en supprimant ses éléments.

## <a name="example"></a> Exemple

L’exemple suivant indique comment supprimer tous les éléments d’un <xref:System.Collections.Concurrent.BlockingCollection%601> à l’aide d’une boucle `foreach` (`For Each`).

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

Cet exemple utilise une boucle `foreach` avec la méthode <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> dans le thread consommateur, ce qui provoque la suppression de chaque élément de la collection pendant son énumération. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limite le nombre maximal d’éléments présents dans la collection à tout moment. Cette façon d’énumérer la collection bloque le thread consommateur si aucun élément n’est disponible ou si la collection est vide. Dans cet exemple, le blocage n’est pas un problème, car le thread producteur ajoute des éléments plus vite qu’ils ne peuvent être consommés.

Le <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> retourne un `IEnumerable<T>`, par conséquent, l’ordre ne peut pas être garanti. Toutefois, en interne, <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> un est utilisé comme type de collection sous-jacent, ce qui entraîne la mise en file d’attente des objets qui suivent le classement FIFO (premier entré, premier sorti). Si des appels simultanés à <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> sont effectués, ils sont en concurrence. Un élément consommé (déplacé dans la file d’attente) dans une énumération ne peut pas être observé dans l’autre.

Pour énumérer la collection sans la modifier, utilisez seulement `foreach` (`For Each`) sans la méthode <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A>. Toutefois, il est important de comprendre que ce genre d’énumération représente un instantané de la collection à un moment donné. Si d’autres threads ajoutent ou suppriment des éléments simultanément pendant l’exécution de la boucle, la boucle peut ne pas représenter l’état réel de la collection.

## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Programmation parallèle](../../../../docs/standard/parallel-programming/index.md)
