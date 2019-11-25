---
title: Take, clause
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 3082954ef84560ccb70f7a47cd3532f622829392
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349647"
---
# <a name="take-clause-visual-basic"></a>Take, clause (Visual Basic)
Retourne un nombre spécifié d'éléments contigus à partir du début d'une collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Take count  
```  
  
## <a name="parts"></a>Composants  
 `count`  
 Requis. A value or an expression that evaluates to the number of elements of the sequence to return.  
  
## <a name="remarks"></a>Notes  
 The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list. The number of elements to include is specified by the `count` parameter.  
  
 You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query. To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause. In this case, the `Take` clause must be specified after the `Skip` clause.  
  
 When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results. For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.  
  
## <a name="example"></a>Exemple  
 The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages. The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](../../../visual-basic/language-reference/queries/index.md)
- [Select (clause)](../../../visual-basic/language-reference/queries/select-clause.md)
- [From (clause)](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By (clause)](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Take While (clause)](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Skip (clause)](../../../visual-basic/language-reference/queries/skip-clause.md)
