---
title: ^, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponentiation
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: e139becf74ae367266a23513e18d0bdbdd24cdea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371386"
---
# <a name="-operator-visual-basic"></a>^, opérateur (Visual Basic)

Élève un nombre à la puissance d'un autre nombre.

## <a name="syntax"></a>Syntaxe

```vb
number ^ exponent
```

## <a name="parts"></a>Éléments

`number`\
Obligatoire. Toute expression numérique.

`exponent`\
Obligatoire. Toute expression numérique.

## <a name="result"></a>Résultats

Le résultat est `number` élevé à la puissance de `exponent` , toujours en tant que `Double` valeur.

## <a name="supported-types"></a>Types pris en charge

`Double`. Les opérandes de tout type différent sont convertis en `Double` .

## <a name="remarks"></a>Notes

Visual Basic effectue toujours une élévation à la puissance dans le [type de données double](../data-types/double-data-type.md).

La valeur de `exponent` peut être fractionnaire, négative ou les deux.

Lorsque plusieurs élévations à une puissance sont effectuées dans une même expression, l' `^` opérateur est évalué à mesure qu’il est rencontré de gauche à droite.

> [!NOTE]
> L' `^` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).

## <a name="example"></a>Exemple

L’exemple suivant utilise l' `^` opérateur pour élever un nombre à la puissance d’un exposant. Le résultat est le premier opérande élevé à la puissance de la seconde.

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

L’exemple précédent produit les résultats suivants :

`exp1`a la valeur 4 (2 au carré).

`exp2`est défini sur 19683 (3 cube, puis sur cette valeur cube).

`exp3`a la valeur-125 (-5 Cubed).

`exp4`est défini sur 625 (-5 sur la quatrième puissance).

`exp5`a la valeur 2 (racine du cube de 8).

`exp6`a la valeur 0,5 (1,0 divisée par la racine du cube de 8).

Notez l’importance des parenthèses dans les expressions de l’exemple précédent. En raison de la *priorité des opérateurs*, Visual Basic exécute normalement l' `^` opérateur avant les autres, même l’opérateur unaire `–` . Si `exp4` et ont `exp6` été calculés sans parenthèses, ils auraient produit les résultats suivants :

`exp4 = -5 ^ 4`serait calculé comme-(5 à la quatrième puissance), ce qui se traduirait par-625.

`exp6 = 8 ^ -1.0 / 3.0`est calculé comme (8 à – 1 puissance, ou 0,125) divisé par 3,0, ce qui se traduirait par 0.041666666666666666666666666666667.

## <a name="see-also"></a>Voir aussi

- [^ = (Opérateur)](exponentiation-assignment-operator.md)
- [Opérateurs arithmétiques](arithmetic-operators.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [Opérateurs arithmétiques en Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
