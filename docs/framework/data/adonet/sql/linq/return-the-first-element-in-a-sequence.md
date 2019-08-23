---
title: Retourner le premier élément d'une séquence
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 39cf9270b08fce64590fef418bb428c5a781b0e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963813"
---
# <a name="return-the-first-element-in-a-sequence"></a>Retourner le premier élément d'une séquence
Utilisez l'opérateur <xref:System.Linq.Enumerable.First%2A> pour retourner le premier élément d'une séquence. Les requêtes qui utilisent <xref:System.Linq.Enumerable.First%2A> sont exécutées immédiatement.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne prend pas en charge l'opérateur <xref:System.Linq.Enumerable.Last%2A>.  
  
## <a name="example"></a>Exemples  
 Le code suivant recherche le premier `Shipper` dans une table :  
  
 Si vous exécutez cette requête sur l'exemple de base de données Northwind, vous obtenez le résultat suivant :  
  
 `ID = 1, Company = Speedy Express`.  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a>Exemples  
 Le code suivant recherche le seul `Customer` qui a BONAP comme `CustomerID`.  
  
 Si vous exécutez cette requête sur l'exemple de base de données Northwind, vous obtenez `ID = BONAP, Contact = Laurence Lebihan`.  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a>Voir aussi

- [Exemples de requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Téléchargement d’exemples de base de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
