---
title: Skip While, clause (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 7f37a6fa1c9ba7fdf7978ac6853e4c2985bf72e7
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004697"
---
# <a name="skip-while-clause-visual-basic"></a>Skip While, clause (Visual Basic)
Ignore les éléments d’une collection tant qu’une condition spécifiée a la valeur `true`, puis retourne les éléments restants.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`expression`|Obligatoire. Expression qui représente une condition pour laquelle tester des éléments. L’expression doit retourner une valeur `Boolean` ou un équivalent fonctionnel, tel qu’une `Integer` à évaluer en tant que `Boolean`.|  
  
## <a name="remarks"></a>Notes  
 La clause `Skip While` ignore les éléments à partir du début d’un résultat de requête jusqu’à ce que le `expression` fourni retourne `false`. Après `expression` retourne `false`, la requête retourne tous les éléments restants. La `expression` est ignorée pour les résultats restants.  
  
 La clause `Skip While` est différente de la clause `Where` dans la mesure où la clause `Where` peut être utilisée pour exclure tous les éléments d’une requête qui ne respectent pas une condition particulière. La clause `Skip While` exclut les éléments uniquement jusqu’à la première fois que la condition n’est pas satisfaite. La clause `Skip While` est particulièrement utile lorsque vous travaillez avec un résultat de requête ordonné.  
  
 Vous pouvez ignorer un nombre spécifique de résultats à partir du début d’un résultat de requête à l’aide de la clause `Skip`.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant utilise la clause `Skip While` pour ignorer les résultats jusqu’à ce que le premier client du États-Unis soit trouvé.  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](../../../visual-basic/language-reference/queries/index.md)
- [Select (clause)](../../../visual-basic/language-reference/queries/select-clause.md)
- [From (clause)](../../../visual-basic/language-reference/queries/from-clause.md)
- [Skip (clause)](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Take While (clause)](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Where (clause)](../../../visual-basic/language-reference/queries/where-clause.md)
