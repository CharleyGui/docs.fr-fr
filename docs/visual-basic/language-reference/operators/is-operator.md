---
title: Opérateur is
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 1c2d87ef0a8202332c87af552f488d652c400213
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812261"
---
# <a name="is-operator-visual-basic"></a>Opérateur is (Visual Basic)

Compare deux variables de référence d’objet.

## <a name="syntax"></a>Syntaxe

```vb
result = object1 Is object2
```

## <a name="parts"></a>Éléments

 `result`  
 Obligatoire. Toute `Boolean` valeur.  
  
 `object1`  
 Obligatoire. N’importe quel `Object` nom.  
  
 `object2`  
 Obligatoire. N’importe quel `Object` nom.  
  
## <a name="remarks"></a>Notes

L' `Is` opérateur détermine si deux références d’objet font référence au même objet. Toutefois, il n’effectue pas de comparaisons de valeurs. Si `object1` et `object2` font tous deux référence à la même instance d’objet, `result` est ; dans le `True` cas contraire, `result` est `False` .

> [!NOTE]
> Le `Is` mot clé est également utilisé dans la [sélection... Instruction case](../statements/select-case-statement.md).
  
## <a name="example"></a>Exemple

L’exemple suivant utilise l' `Is` opérateur pour comparer des paires de références d’objets. Les résultats sont assignés à une `Boolean` valeur indiquant si les deux objets sont identiques.

[!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]

Comme le montre l’exemple précédent, vous pouvez utiliser l' `Is` opérateur pour tester à la fois les objets à liaison anticipée et les objets à liaison tardive.

## <a name="use-typeof-operator-with-is-operator"></a>Utiliser l’opérateur TypeOf avec opérateur is

`Is` l’opérateur peut également être utilisé avec le `TypeOf` mot clé pour créer une `TypeOf` expression... `Is` , qui teste si une variable objet est compatible avec un type de données. Par exemple :

```vb
If TypeOf sender Is Button Then
```

## <a name="see-also"></a>Voir aussi

- [TypeOf, opérateur](typeof-operator.md)
- [IsNot, opérateur](isnot-operator.md)
- [Comparison Operators in Visual Basic](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [Opérateurs et expressions](../../programming-guide/language-features/operators-and-expressions/index.md)
