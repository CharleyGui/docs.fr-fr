---
title: Let (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: a6ff3fc80a2b6752c61a8b8f7d4ce62b5a46baad
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869885"
---
# <a name="let-clause-visual-basic"></a>Let, clause (Visual Basic)

Calcule une valeur et l’assigne à une nouvelle variable dans la requête.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|---|---|  
|`variable`|Obligatoire. Alias qui peut être utilisé pour référencer les résultats de l’expression fournie.|  
|`expression`|Obligatoire. Expression qui sera évaluée et assignée à la variable spécifiée.|  
  
## <a name="remarks"></a>Notes  

 La `Let` clause vous permet de calculer des valeurs pour chaque résultat de la requête et de les référencer à l’aide d’un alias. L’alias peut être utilisé dans d’autres clauses, telles que la `Where` clause. La `Let` clause vous permet de créer une instruction de requête qui est plus facile à lire, car vous pouvez spécifier un alias pour une clause d’expression incluse dans la requête et substituer l’alias chaque fois que la clause d’expression est utilisée.  
  
 Vous pouvez inclure n’importe quel nombre d' `variable` `expression` affectations et dans la `Let` clause. Séparez chaque assignation par une virgule (,).  
  
## <a name="example"></a>Exemple  

 L’exemple de code suivant utilise la `Let` clause pour calculer une remise de 10 pour cent sur les produits.  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](index.md)
- [Clause SELECT](select-clause.md)
- [From, clause](from-clause.md)
- [Clause WHERE](where-clause.md)
