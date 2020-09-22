---
title: Take (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: f2377d8d1635912885a310b2b0429a6a00083b47
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869679"
---
# <a name="take-clause-visual-basic"></a>Take, clause (Visual Basic)

Retourne un nombre spécifié d'éléments contigus à partir du début d'une collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Take count  
```  
  
## <a name="parts"></a>Éléments  

 `count`  
 Obligatoire. Valeur ou expression qui prend la valeur du nombre d’éléments de la séquence à retourner.  
  
## <a name="remarks"></a>Notes  

 La `Take` clause force une requête à inclure un nombre spécifié d’éléments contigus à partir du début d’une liste de résultats. Le nombre d’éléments à inclure est spécifié par le `count` paramètre.  
  
 Vous pouvez utiliser la `Take` clause avec la `Skip` clause pour retourner une plage de données à partir d’un segment d’une requête. Pour ce faire, transmettez l’index du premier élément de la plage à la `Skip` clause et la taille de la plage à la `Take` clause. Dans ce cas, la `Take` clause doit être spécifiée après la `Skip` clause.  
  
 Lorsque vous utilisez la `Take` clause dans une requête, vous devrez peut-être également vous assurer que les résultats sont retournés dans un ordre qui permettra `Take` à la clause d’inclure les résultats souhaités. Pour plus d’informations sur la façon de classer les résultats d’une requête, consultez [clause ORDER BY](order-by-clause.md).  
  
 Vous pouvez utiliser la `TakeWhile` clause pour spécifier que seuls certains éléments doivent être retournés, en fonction d’une condition fournie.  
  
## <a name="example"></a>Exemple  

 L’exemple de code suivant utilise la `Take` clause avec la `Skip` clause pour retourner des données d’une requête dans des pages. La fonction GetCustomers utilise la `Skip` clause pour ignorer les clients de la liste jusqu’à la valeur d’index de départ fournie et utilise la `Take` clause pour retourner une page de clients à partir de cette valeur d’index.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](index.md)
- [Clause SELECT](select-clause.md)
- [From, clause](from-clause.md)
- [Clause ORDER BY](order-by-clause.md)
- [Take While (clause)](take-while-clause.md)
- [Skip (clause)](skip-clause.md)
