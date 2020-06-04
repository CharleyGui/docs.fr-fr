---
title: Where (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: b80bb047551dee8ab23cfac06b961996992d69b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359539"
---
# <a name="where-clause-visual-basic"></a>Where, clause (Visual Basic)
Spécifie la condition de filtrage pour une requête.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a>Éléments  
 `condition`  
 Obligatoire. Expression qui détermine si les valeurs de l’élément actuel dans la collection sont incluses dans la collection de sortie. L’expression doit correspondre à une `Boolean` valeur ou à l’équivalent d’une `Boolean` valeur. Si la condition a la valeur `True` , l’élément est inclus dans le résultat de la requête ; sinon, l’élément est exclu du résultat de la requête.  
  
## <a name="remarks"></a>Notes  
 La `Where` clause vous permet de filtrer les données de requête en sélectionnant uniquement les éléments qui répondent à certains critères. Les éléments dont les valeurs provoquent l’évaluation de la `Where` clause `True` sont inclus dans le résultat de la requête ; d’autres éléments sont exclus. L’expression utilisée dans une `Where` clause doit avoir la `Boolean` valeur ou l’équivalent d’un `Boolean` , tel qu’un entier qui prend la `False` valeur lorsque sa valeur est égale à zéro. Vous pouvez combiner plusieurs expressions dans une `Where` clause à l’aide d’opérateurs logiques tels que,,,, `And` `Or` `AndAlso` `OrElse` `Is` et `IsNot` .  
  
 Par défaut, les expressions de requête ne sont pas évaluées tant qu’elles ne sont pas accessibles, par exemple lorsqu’elles sont liées aux données ou itérées dans une `For` boucle. Par conséquent, la `Where` clause n’est pas évaluée tant que la requête n’est pas accédée. Si vous avez des valeurs externes à la requête utilisées dans la `Where` clause, assurez-vous que la valeur appropriée est utilisée dans la `Where` clause au moment de l’exécution de la requête. Pour plus d’informations sur l’exécution des requêtes, consultez [écriture de votre première requête LINQ](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 Vous pouvez appeler des fonctions dans une `Where` clause pour effectuer un calcul ou une opération sur une valeur de l’élément actuel dans la collection. L’appel d’une fonction dans une `Where` clause peut entraîner l’exécution immédiate de la requête lorsqu’elle est définie au lieu de l’accès. Pour plus d’informations sur l’exécution des requêtes, consultez [écriture de votre première requête LINQ](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="example"></a>Exemple  
 L’expression de requête suivante utilise une `From` clause pour déclarer une variable `cust` de portée pour chaque `Customer` objet de la `customers` collection. La `Where` clause utilise la variable de portée pour limiter la sortie aux clients de la région spécifiée. La `For Each` boucle affiche le nom de la société pour chaque client dans le résultat de la requête.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise `And` les `Or` opérateurs logiques et dans la `Where` clause.  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](index.md)
- [From, clause](from-clause.md)
- [Clause SELECT](select-clause.md)
- [For Each...Next (instruction)](../statements/for-each-next-statement.md)
