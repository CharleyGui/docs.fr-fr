---
title: Is, opérateur (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: a5481a9bce01e84ce4f078335c8cd15a747a3c51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917214"
---
# <a name="is-operator-visual-basic"></a>Is, opérateur (Visual Basic)
Compare deux variables de référence d’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Requis. Toute `Boolean` valeur.  
  
 `object1`  
 Requis. N' `Object` importe quel nom.  
  
 `object2`  
 Requis. N' `Object` importe quel nom.  
  
## <a name="remarks"></a>Notes  
 L' `Is` opérateur détermine si deux références d’objet font référence au même objet. Toutefois, il n’effectue pas de comparaisons de valeurs. Si `object1` et `True` `result` `result` `False`font tous deux référence à la même instance d’objet, est; dans le cas contraire, est. `object2`  
  
 `Is`peut également être utilisé avec le `TypeOf` mot clé pour créer `TypeOf`un... `Is` expression qui teste si une variable objet est compatible avec un type de données.  
  
> [!NOTE]
> Le `Is` mot clé est également utilisé dans la [sélection... Instruction case](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `Is` opérateur pour comparer des paires de références d’objets. Les résultats sont assignés à une `Boolean` valeur indiquant si les deux objets sont identiques.  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 Comme le montre l’exemple précédent, vous pouvez utiliser `Is` l’opérateur pour tester à la fois les objets à liaison anticipée et les objets à liaison tardive.  
  
## <a name="see-also"></a>Voir aussi

- [TypeOf (opérateur)](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [IsNot (opérateur)](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Opérateurs de comparaison dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
