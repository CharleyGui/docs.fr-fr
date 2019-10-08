---
title: Skip, clause (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: e52de186e1475bfabd02821a0cd2384d8350eed3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004765"
---
# <a name="skip-clause-visual-basic"></a>Skip, clause (Visual Basic)
Ignore un nombre spécifié d’éléments dans une collection, puis retourne les éléments restants.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a>Composants  
 `count`  
 Obligatoire. Valeur ou expression qui prend la valeur du nombre d’éléments de la séquence à ignorer.  
  
## <a name="remarks"></a>Notes  
 La clause `Skip` provoque une requête qui ignore les éléments au début d’une liste de résultats et retourne les éléments restants. Le nombre d’éléments à ignorer est identifié par le paramètre `count`.  
  
 Vous pouvez utiliser la clause `Skip` avec la clause `Take` pour retourner une plage de données à partir de n’importe quel segment d’une requête. Pour ce faire, transmettez l’index du premier élément de la plage à la clause `Skip` et la taille de la plage à la clause `Take`.  
  
 Lorsque vous utilisez la clause `Skip` dans une requête, vous devrez peut-être également vous assurer que les résultats sont retournés dans un ordre qui permettra à la clause `Skip` de contourner les résultats prévus. Pour plus d’informations sur la façon de classer les résultats d’une requête, consultez [clause ORDER BY](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Vous pouvez utiliser la clause `SkipWhile` pour spécifier que seuls certains éléments sont ignorés, en fonction d’une condition fournie.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant utilise la clause `Skip` conjointement avec la clause `Take` pour retourner des données d’une requête dans des pages. La fonction `GetCustomers` utilise la clause `Skip` pour contourner les clients de la liste jusqu’à la valeur d’index de départ fournie et utilise la clause `Take` pour retourner une page de clients à partir de cette valeur d’index.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](../../../visual-basic/language-reference/queries/index.md)
- [Select (clause)](../../../visual-basic/language-reference/queries/select-clause.md)
- [From (clause)](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By (clause)](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Skip While (clause)](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take (clause)](../../../visual-basic/language-reference/queries/take-clause.md)
