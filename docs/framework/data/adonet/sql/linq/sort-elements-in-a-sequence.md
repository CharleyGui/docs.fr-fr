---
title: Trier les éléments d'une séquence
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d59b93a9-50c8-4770-a114-d902f6a0ea76
ms.openlocfilehash: b594e756b099aa94e1043fd4256da3eff46d0d95
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155755"
---
# <a name="sort-elements-in-a-sequence"></a>Trier les éléments d'une séquence

Utilisez l'opérateur <xref:System.Linq.Enumerable.OrderBy%2A> pour trier une séquence selon une ou plusieurs clés.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] est conçu pour prendre en charge le classement par types primitifs simples, tels que `string` , `int` , et ainsi de suite. Il ne prend pas en charge le classement des classes complexes à valeurs multiples, telles que les types anonymes. Il ne prend pas non plus en charge de types de données `byte`.  
  
## <a name="example"></a>Exemple  

 L'exemple suivant trie `Employees` par date d'embauche.  
  
 [!code-csharp[DLinqQueryExamples#20](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#20)]
 [!code-vb[DLinqQueryExamples#20](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#20)]  
  
## <a name="example"></a>Exemple  

 L'exemple suivant utilise `where` pour trier des `Orders` expédiées à `London` par fret.  
  
 [!code-csharp[DLinqQueryExamples#21](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#21)]
 [!code-vb[DLinqQueryExamples#21](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#21)]  
  
## <a name="example"></a>Exemple  

 L'exemple suivant trie les `Products` par prix unitaire du plus élevé au plus bas.  
  
 [!code-csharp[DLinqQueryExamples#22](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#22)]
 [!code-vb[DLinqQueryExamples#22](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#22)]  
  
## <a name="example"></a>Exemple  

 L'exemple suivant utilise un `OrderBy` composé pour trier les `Customers` par ville puis par nom de contact.  
  
 [!code-csharp[DLinqQueryExamples#24](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#24)]
 [!code-vb[DLinqQueryExamples#24](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#24)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant trie les commandes de `EmployeeID 1` par, puis de `ShipCountry` fret le plus élevé au plus bas.  
  
 [!code-csharp[DLinqQueryExamples#25](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#25)]
 [!code-vb[DLinqQueryExamples#25](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#25)]  
  
## <a name="example"></a>Exemple  

 L'exemple suivant combine les opérateurs <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A> et <xref:System.Linq.Enumerable.GroupBy%2A> pour rechercher le `Products` qui a le prix unitaire le plus élevé dans chaque catégorie, puis trie le groupe par ID de catégorie.  
  
 [!code-csharp[DLinqQueryExamples#26](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#26)]
 [!code-vb[DLinqQueryExamples#26](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#26)]  
  
 Si vous exécutez la requête précédente sur l'exemple de base de données Northwind, les résultats se présenteront comme suit :  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a>Voir aussi

- [Exemples de requêtes](query-examples.md)
- [Téléchargement d’exemples de base de données](downloading-sample-databases.md)
