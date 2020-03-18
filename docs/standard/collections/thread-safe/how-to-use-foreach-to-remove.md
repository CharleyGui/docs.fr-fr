---
title: "Comment : utiliser la boucle ForEach pour supprimer les éléments d'un BlockingCollection"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collection
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
ms.openlocfilehash: f9a858dea74be63634f887c4204aefa8ac338ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711231"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a>Comment : utiliser la boucle ForEach pour supprimer les éléments d'un BlockingCollection

Outre l’extraction d’éléments à partir d’un <xref:System.Collections.Concurrent.BlockingCollection%601> à l’aide des méthodes <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> et <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A>, vous pouvez également utiliser une boucle [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) en Visual Basic) pour supprimer des éléments jusqu’à ce que l’ajout soit terminé et que la collection soit vide. Cela s’appelle une *énumération de mutation* ou *énumération de consommation* car, contrairement à une boucle `foreach` (`For Each`) typique, cet énumérateur modifie la collection source en supprimant ses éléments.

## <a name="example"></a> Exemple

L’exemple suivant indique comment supprimer tous les éléments d’un <xref:System.Collections.Concurrent.BlockingCollection%601> à l’aide d’une boucle `foreach` (`For Each`).

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

Cet exemple utilise une boucle `foreach` avec la méthode <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> dans le thread consommateur, ce qui provoque la suppression de chaque élément de la collection pendant son énumération. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limite le nombre maximal d’éléments présents dans la collection à tout moment. Cette façon d’énumérer la collection bloque le thread consommateur si aucun élément n’est disponible ou si la collection est vide. Dans cet exemple, le blocage n’est pas un problème, car le thread producteur ajoute des éléments plus vite qu’ils ne peuvent être consommés.

Il n’y a aucune garantie que les éléments soient énumérés dans le même ordre que celui dans lequel ils ont été ajoutés par les threads producteurs.

Pour énumérer la collection sans la modifier, utilisez seulement `foreach` (`For Each`) sans la méthode <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A>. Toutefois, il est important de comprendre que ce genre d’énumération représente un instantané de la collection à un moment donné. Si d’autres threads ajoutent ou suppriment des éléments simultanément pendant l’exécution de la boucle, la boucle peut ne pas représenter l’état réel de la collection.

## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Programmation parallèle](../../../../docs/standard/parallel-programming/index.md)
