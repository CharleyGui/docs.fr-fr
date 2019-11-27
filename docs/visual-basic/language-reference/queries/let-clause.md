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
Calcule une valeur et l’assigne à une nouvelle variable dans la requête.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`variable`|Requis. Alias qui peut être utilisé pour référencer les résultats de l’expression fournie.|  
|`expression`|Requis. Expression qui sera évaluée et assignée à la variable spécifiée.|  
  
## <a name="remarks"></a>Notes  
 La clause `Let` vous permet de calculer des valeurs pour chaque résultat de requête et de les référencer à l’aide d’un alias. L’alias peut être utilisé dans d’autres clauses, telles que la clause `Where`. La clause `Let` vous permet de créer une instruction de requête qui est plus facile à lire, car vous pouvez spécifier un alias pour une clause d’expression incluse dans la requête et remplacer l’alias chaque fois que la clause expression est utilisée.  
  
 Vous pouvez inclure n’importe quel nombre de `variable` et `expression` assignations dans la clause `Let`. Séparez chaque assignation par une virgule (,).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant utilise la clause `Let` pour calculer une remise de 10% sur les produits.  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](../../../visual-basic/language-reference/queries/index.md)
- [Select (clause)](../../../visual-basic/language-reference/queries/select-clause.md)
- [From (clause)](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where (clause)](../../../visual-basic/language-reference/queries/where-clause.md)
