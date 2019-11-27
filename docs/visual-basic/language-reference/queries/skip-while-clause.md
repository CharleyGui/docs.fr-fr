---
title: Skip While, clause
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 47703e445865435f5bf5312c3fe41833ac21aa3f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333144"
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
|`expression`|Requis. Expression qui représente une condition pour laquelle tester des éléments. L’expression doit retourner une valeur `Boolean` ou un équivalent fonctionnel, tel qu’un `Integer` à évaluer en tant que `Boolean`.|  
  
## <a name="remarks"></a>Notes  
 La clause `Skip While` ignore les éléments à partir du début d’un résultat de requête jusqu’à ce que le `expression` fourni retourne `false`. Une fois que `expression` a retourné `false`, la requête retourne tous les éléments restants. La `expression` est ignorée pour les résultats restants.  
  
 La clause `Skip While` diffère de la clause `Where` dans la mesure où la clause `Where` peut être utilisée pour exclure tous les éléments d’une requête qui ne respectent pas une condition particulière. La clause `Skip While` exclut les éléments uniquement jusqu’à la première fois que la condition n’est pas satisfaite. La clause `Skip While` est très utile lorsque vous travaillez avec un résultat de requête ordonné.  
  
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
