---
title: Let, clause
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 63eaf97016db259870eb77199651ecbdc5f809c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350434"
---
# <a name="let-clause-visual-basic"></a>Let, clause (Visual Basic)
Computes a value and assigns it to a new variable within the query.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`variable`|Requis. An alias that can be used to reference the results of the supplied expression.|  
|`expression`|Requis. An expression that will be evaluated and assigned to the specified variable.|  
  
## <a name="remarks"></a>Notes  
 The `Let` clause enables you to compute values for each query result and reference them by using an alias. The alias can be used in other clauses, such as the `Where` clause. The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.  
  
 You can include any number of `variable` and `expression` assignments in the `Let` clause. Separate each assignment with a comma (,).  
  
## <a name="example"></a>Exemple  
 The following code example uses the `Let` clause to compute a 10 percent discount on products.  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](../../../visual-basic/language-reference/queries/index.md)
- [Select (clause)](../../../visual-basic/language-reference/queries/select-clause.md)
- [From (clause)](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where (clause)](../../../visual-basic/language-reference/queries/where-clause.md)
