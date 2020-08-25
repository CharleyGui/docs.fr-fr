---
title: IsNot (opérateur)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- comparison operators [Visual Basic]
- TypeOf...IsNot expression
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: ea978f8874cee20fb3a005189fd846f7564da777
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811039"
---
# <a name="isnot-operator-visual-basic"></a>Opérateur IsNot (Visual Basic)

Compare deux variables de référence d’objet.

## <a name="syntax"></a>Syntaxe

```vb
result = object1 IsNot object2
```

## <a name="parts"></a>Éléments

- `result`

  Obligatoire. Valeur `Boolean`.

- `object1`

  Obligatoire. Toute `Object` variable ou expression.

- `object2`

  Obligatoire. Toute `Object` variable ou expression.

## <a name="remarks"></a>Notes

L' `IsNot` opérateur détermine si deux références d’objet font référence à des objets différents. Toutefois, il n’effectue pas de comparaisons de valeurs. Si `object1` et `object2` les deux font référence exactement à la même instance d’objet, `result` est `False` ; sinon, `result` est `True` .

`IsNot` est l’opposé de l' `Is` opérateur. L’avantage de `IsNot` est que vous pouvez éviter la syntaxe maladroite avec `Not` et `Is` , ce qui peut être difficile à lire.

 Vous pouvez utiliser les `Is` `IsNot` opérateurs et pour tester à la fois les objets à liaison anticipée et les objets à liaison tardive.

## <a name="example"></a>Exemple

L’exemple de code suivant utilise à la fois l' `Is` opérateur et l' `IsNot` opérateur pour effectuer la même comparaison.

[!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="use-typeof-operator-with-isnot-operator"></a>Utiliser l’opérateur TypeOf avec l’opérateur IsNot

À partir de Visual Basic 14, vous pouvez utiliser l' `TypeOf` opérateur avec l' `IsNot` opérateur pour tester si un objet n’est *pas* compatible avec un type de données. Par exemple :

```vb
If TypeOf sender IsNot Button Then
```

## <a name="see-also"></a>Voir aussi

- [Is, opérateur](is-operator.md)
- [TypeOf, opérateur](typeof-operator.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Comment : déterminer si deux objets sont identiques](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
