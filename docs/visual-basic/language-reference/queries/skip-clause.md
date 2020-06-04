---
title: Skip (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 427d14453260a54bd3f2ab9a8ac75dedacd291f4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359656"
---
# <a name="skip-clause-visual-basic"></a>Skip, clause (Visual Basic)
Ignore un nombre spécifié d’éléments dans une collection, puis retourne les éléments restants.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a>Éléments  
 `count`  
 Obligatoire. Valeur ou expression qui prend la valeur du nombre d’éléments de la séquence à ignorer.  
  
## <a name="remarks"></a>Notes  
 La `Skip` clause génère une requête qui ignore les éléments au début d’une liste de résultats et retourne les éléments restants. Le nombre d’éléments à ignorer est identifié par le `count` paramètre.  
  
 Vous pouvez utiliser la `Skip` clause avec la `Take` clause pour retourner une plage de données à partir d’un segment d’une requête. Pour ce faire, transmettez l’index du premier élément de la plage à la `Skip` clause et la taille de la plage à la `Take` clause.  
  
 Lorsque vous utilisez la `Skip` clause dans une requête, vous devrez peut-être également vous assurer que les résultats sont retournés dans un ordre qui permettra `Skip` à la clause de contourner les résultats souhaités. Pour plus d’informations sur la façon de classer les résultats d’une requête, consultez [clause ORDER BY](order-by-clause.md).  
  
 Vous pouvez utiliser la `SkipWhile` clause pour spécifier que seuls certains éléments sont ignorés, en fonction d’une condition fournie.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant utilise la `Skip` clause avec la `Take` clause pour retourner des données d’une requête dans des pages. La `GetCustomers` fonction utilise la `Skip` clause pour ignorer les clients de la liste jusqu’à la valeur d’index de départ fournie et utilise la `Take` clause pour retourner une page de clients à partir de cette valeur d’index.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](index.md)
- [Clause SELECT](select-clause.md)
- [From, clause](from-clause.md)
- [Order By (clause)](order-by-clause.md)
- [SkipWhile (clause)](skip-while-clause.md)
- [Take (clause)](take-clause.md)
