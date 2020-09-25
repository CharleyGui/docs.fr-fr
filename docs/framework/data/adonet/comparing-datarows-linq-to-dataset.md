---
title: Comparaison de DataRows (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: 8cce52734c83e42312d71806d4151ef21e4df0ba
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203798"
---
# <a name="comparing-datarows-linq-to-dataset"></a>Comparaison de DataRows (LINQ to DataSet)

LINQ (Language-Integrated Query) définit plusieurs opérateurs de jeu pour comparer des éléments sources afin de déterminer s’ils sont égaux. LINQ fournit les opérateurs de jeu suivants :  
  
- <xref:System.Linq.Enumerable.Distinct%2A>  
  
- <xref:System.Linq.Enumerable.Union%2A>  
  
- <xref:System.Linq.Enumerable.Intersect%2A>  
  
- <xref:System.Linq.Enumerable.Except%2A>  
  
 Ces opérateurs comparent des éléments de code source en appelant <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> et les méthodes <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> sur chaque collection d'éléments. Dans le cas d'un <xref:System.Data.DataRow>, ces opérateurs effectuent une comparaison de référence, ce qui n'est généralement pas le comportement idéal pour des opérations de jeu sur des données de tableau. Pour les opérations de jeu, il vous faut en général déterminer si les valeurs de l'élément sont égales, et pas les références d'élément. Par conséquent, la <xref:System.Data.DataRowComparer> classe a été ajoutée à LINQ to DataSet. Cette classe peut être utilisée pour comparer des valeurs de ligne.  
  
 La classe <xref:System.Data.DataRowComparer> contient une implémentation de comparaison de valeur pour <xref:System.Data.DataRow>, ce qui fait qu'elle peut être utilisée pour des opérations de jeu telles que <xref:System.Linq.Enumerable.Distinct%2A>. Cette classe ne peut pas être instanciée directement ; vous devez utiliser à la place la propriété <xref:System.Data.DataRowComparer.Default%2A> pour retourner une instance du <xref:System.Data.DataRowComparer%601>. La méthode <xref:System.Data.DataRowComparer%601.Equals%2A> est ensuite appelée et les deux objets <xref:System.Data.DataRow> à comparer sont passés en tant que paramètres d'entrée. La méthode <xref:System.Data.DataRowComparer%601.Equals%2A> retourne `true` si le jeu trié de valeurs de colonne dans les deux objets <xref:System.Data.DataRow> comporte des valeurs égales ; sinon `false`.  
  
## <a name="example"></a>Exemple  

 Cet exemple utilise la méthode `Intersect` pour retourner les contacts qui apparaissent dans les deux tables.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a>Exemple  

 L'exemple suivant compare deux lignes et obtient les codes de hachage.  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataRowComparer>
- [Chargement de données dans un DataSet](loading-data-into-a-dataset.md)
- [Exemples de LINQ to DataSet](linq-to-dataset-examples.md)
