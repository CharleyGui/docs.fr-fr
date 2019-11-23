---
title: IsNot, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 616506f64d20e1f150b443433f1b69040136a5ba
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336073"
---
# <a name="isnot-operator-visual-basic"></a>Opérateur IsNot (Visual Basic)

Compares two object reference variables.

## <a name="syntax"></a>Syntaxe

```vb
result = object1 IsNot object2
```

## <a name="parts"></a>Composants
 `result` Obligatoire. Valeur `Boolean`.

 `object1` Obligatoire. Any `Object` variable or expression.

 `object2` Obligatoire. Any `Object` variable or expression.

## <a name="remarks"></a>Notes
 The `IsNot` operator determines if two object references refer to different objects. However, it does not perform value comparisons. If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.

 `IsNot` is the opposite of the `Is` operator. The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.

 You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.

## <a name="example"></a>Exemple
 The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a>Voir aussi

- [Is (opérateur)](is-operator.md)
- [TypeOf (opérateur)](typeof-operator.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Guide pratique : déterminer si deux objets sont identiques](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
