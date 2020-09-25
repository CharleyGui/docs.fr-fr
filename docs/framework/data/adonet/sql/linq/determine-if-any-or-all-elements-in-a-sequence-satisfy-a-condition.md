---
title: "Comment : déterminer si certains ou tous les éléments d'une séquence remplissent une condition"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: 65a9a7cf289c2006bab14cb384efb07eaea7f7a0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194425"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a>Comment : déterminer si certains ou tous les éléments d'une séquence remplissent une condition

L'opérateur <xref:System.Linq.Enumerable.All%2A> retourne `true` si tous les éléments d'une séquence remplissent une condition.  
  
 L'opérateur <xref:System.Linq.Queryable.Any%2A> retourne `true` si un élément d'une séquence remplit une condition.  
  
## <a name="example"></a>Exemple  

 L'exemple suivant retourne une séquence de clients possédant au moins une commande. La `Where` / `where` clause prend la valeur `true` si le donné `Customer` a un `Order` .  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a>Exemple  

 Le code Visual Basic suivant détermine la liste des clients qui n'ont pas passé de commande et vérifie qu'un nom de contact est fourni pour chaque client de cette liste.  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a>Exemple  

 L'exemple C# suivant retourne une séquence de clients dont la `ShipCity` des commandes commence par la lettre C. Il retourne également les clients qui n'ont pas de commandes. (Par conception, l' <xref:System.Linq.Queryable.All%2A> opérateur retourne `true` pour une séquence vide.) Les clients sans commande sont éliminés dans la sortie de la console à l’aide de l' `Count` opérateur.  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a>Voir aussi

- [Exemples de requêtes](query-examples.md)
