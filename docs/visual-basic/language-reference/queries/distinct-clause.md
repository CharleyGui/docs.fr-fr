---
title: Distinct, clause
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 94471898807ef4552564c3e01465f2b2f6211d0c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335378"
---
# <a name="distinct-clause-visual-basic"></a>Distinct, clause (Visual Basic)
Restreint les valeurs de la variable de portée actuelle pour éliminer les valeurs en double dans les clauses de requête suivantes.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la clause `Distinct` pour retourner une liste d’éléments uniques. La clause `Distinct` fait en sorte que la requête ignore les résultats de la requête en double. La clause `Distinct` s’applique aux valeurs dupliquées pour tous les champs de retour spécifiés par la clause `Select`. Si aucune clause `Select` n’est spécifiée, la clause `Distinct` est appliquée à la variable de portée pour la requête identifiée dans la clause `From`. Si la variable de portée n’est pas un type immuable, la requête n’ignore un résultat de requête que si tous les membres du type correspondent à un résultat de requête existant.  
  
## <a name="example"></a>Exemple  
 L’expression de requête suivante joint une liste de clients et une liste de commandes client. La clause `Distinct` est incluse pour retourner une liste de noms de clients uniques et de dates de commande.  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](../../../visual-basic/language-reference/queries/index.md)
- [From (clause)](../../../visual-basic/language-reference/queries/from-clause.md)
- [Select (clause)](../../../visual-basic/language-reference/queries/select-clause.md)
- [Where (clause)](../../../visual-basic/language-reference/queries/where-clause.md)
