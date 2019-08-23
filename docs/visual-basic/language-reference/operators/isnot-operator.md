---
title: Opérateur IsNot (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 0a83b48e5e415bd6ca0c777cef6d34f7127691b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966934"
---
# <a name="isnot-operator-visual-basic"></a>Opérateur IsNot (Visual Basic)
Compare deux variables de référence d’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Requis. Valeur `Boolean`.  
  
 `object1`  
 Requis. Toute `Object` variable ou expression.  
  
 `object2`  
 Requis. Toute `Object` variable ou expression.  
  
## <a name="remarks"></a>Notes  
 L' `IsNot` opérateur détermine si deux références d’objet font référence à des objets différents. Toutefois, il n’effectue pas de comparaisons de valeurs. Si `object1` et `False` `result` `result` `True`font tous deux référence à la même instance d’objet, est; dans le cas contraire, est. `object2`  
  
 `IsNot`est l’opposé de l' `Is` opérateur. L’avantage de `IsNot` est que vous pouvez éviter la syntaxe maladroite `Is`avec `Not` et, ce qui peut être difficile à lire.  
  
 Vous pouvez utiliser les `Is` opérateurs `IsNot` et pour tester à la fois les objets à liaison anticipée et les objets à liaison tardive.  
  
> [!NOTE]
> L' `IsNot` opérateur ne peut pas être utilisé pour comparer des expressions `TypeOf` retournées par l’opérateur. Au lieu de cela, vous `Not` devez `Is` utiliser les opérateurs et.  
  
## <a name="example"></a>Exemples  
 L’exemple de code suivant utilise à `Is` la fois l' `IsNot` opérateur et l’opérateur pour effectuer la même comparaison.  
  
 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]  
  
## <a name="see-also"></a>Voir aussi

- [Is (opérateur)](../../../visual-basic/language-reference/operators/is-operator.md)
- [TypeOf (opérateur)](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Guide pratique pour Teste si deux objets sont identiques](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
