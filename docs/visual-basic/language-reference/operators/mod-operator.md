---
title: Mod, opérateur
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
ms.openlocfilehash: 32065567799b023556a018ae2f5ba338796e0b49
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401509"
---
# <a name="mod-operator-visual-basic"></a>Mod, opérateur (Visual Basic)

Divise deux nombres et retourne uniquement le reste.

## <a name="syntax"></a>Syntaxe

```vb
result = number1 Mod number2
```

## <a name="parts"></a>Éléments

`result` \
Obligatoire. Toute variable ou propriété numérique.

`number1` \
Obligatoire. Toute expression numérique.

`number2` \
Obligatoire. Toute expression numérique.

## <a name="supported-types"></a>Types pris en charge

tous les types numériques Cela comprend les types à virgule flottante non signée et `Decimal` .

## <a name="result"></a>Résultats

Le résultat est le reste de la `number1` Division de par `number2` . Par exemple, l’expression `14 Mod 4` prend la valeur 2.

> [!NOTE]
> Il existe une différence entre le *reste* et le *modulo* en mathématiques, avec des résultats différents pour les nombres négatifs. L' `Mod` opérateur dans Visual Basic, l' `op_Modulus` opérateur .NET Framework, et l’instruction [REM](<xref:System.Reflection.Emit.OpCodes.Rem>) il sous-jacente effectuent toutes une opération de reste.

Le résultat d’une `Mod` opération conserve le signe du dividende, `number1` et peut donc être positif ou négatif. Le résultat est toujours dans la plage (- `number2` , `number2` ), exclusif. Par exemple :

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a>Notes

Si `number1` ou `number2` est une valeur à virgule flottante, le reste à virgule flottante de la Division est retourné. Le type de données du résultat est le plus petit type de données qui peut contenir toutes les valeurs possibles qui résultent de la division avec les types de données de `number1` et `number2` .

Si `number1` ou `number2` a la valeur [Nothing](../nothing.md), il est traité comme zéro.

Les opérateurs connexes sont les suivants :

- L' [opérateur \ (Visual Basic)](integer-division-operator.md) retourne le quotient entier d’une division. Par exemple, l’expression `14 \ 4` prend la valeur 3.

- L' [opérateur/(Visual Basic)](floating-point-division-operator.md) retourne le quotient complet, y compris le reste, sous la forme d’un nombre à virgule flottante. Par exemple, l’expression `14 / 4` prend la valeur 3,5.

## <a name="attempted-division-by-zero"></a>Division par zéro

Si `number2` prend la valeur zéro, le comportement de l' `Mod` opérateur dépend du type de données des opérandes :

- Une division intégrale lève une <xref:System.DivideByZeroException> exception si `number2` ne peut pas être déterminée au moment de la compilation et génère une erreur au moment de la compilation `BC30542 Division by zero occurred while evaluating this expression` si `number2` est évalué à zéro au moment de la compilation.
- Une division à virgule flottante retourne <xref:System.Double.NaN?displayProperty=nameWithType> .

## <a name="equivalent-formula"></a>Formule équivalente

L’expression `a Mod b` est équivalente à l’une des formules suivantes :

`a - (b * (a \ b))`

`a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a>Imprécision à virgule flottante

Lorsque vous utilisez des nombres à virgule flottante, n’oubliez pas qu’ils n’ont pas toujours une représentation décimale précise en mémoire. Cela peut entraîner des résultats inattendus de certaines opérations, telles que la comparaison de valeurs et l' `Mod` opérateur. Pour plus d’informations, consultez [Dépannage des types de données](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).

## <a name="overloading"></a>Surcharge

L' `Mod` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement. Si votre code s’applique `Mod` à une instance d’une classe ou d’une structure qui comprend une telle surcharge, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).

## <a name="example"></a>Exemple

L’exemple suivant utilise l' `Mod` opérateur pour diviser deux nombres et retourner uniquement le reste. Si un nombre est un nombre à virgule flottante, le résultat est un nombre à virgule flottante qui représente le reste.

[!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a>Exemple

L’exemple suivant illustre le imprécision potentiel des opérandes à virgule flottante. Dans la première instruction, les opérandes sont `Double` et 0,2 est une fraction binaire à répétition infinie avec une valeur stockée de 0.20000000000000001. Dans la deuxième instruction, le caractère de type de littéral `D` force les deux opérandes à `Decimal` , et 0,2 a une représentation précise.

[!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [Opérateurs arithmétiques](arithmetic-operators.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [Dépannage des types de données](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Opérateurs arithmétiques en Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [\, Opérateur (Visual Basic)](integer-division-operator.md)
