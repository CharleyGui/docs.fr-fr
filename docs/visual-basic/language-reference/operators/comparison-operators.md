---
title: Opérateurs de comparaison
ms.date: 07/20/2015
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basic
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: ea7604626ede66da818e4bc22fe4922bc752dc2c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336082"
---
# <a name="comparison-operators-visual-basic"></a>Opérateurs de comparaison (Visual Basic)
Voici les opérateurs de comparaison définis dans Visual Basic.

 opérateur `<`

 opérateur `<=`

 opérateur `>`

 opérateur `>=`

 opérateur `=`

 opérateur `<>`

 [Is (opérateur)](../../../visual-basic/language-reference/operators/is-operator.md)

 [IsNot (opérateur)](../../../visual-basic/language-reference/operators/isnot-operator.md)

 [Like (opérateur)](../../../visual-basic/language-reference/operators/like-operator.md)

 Ces opérateurs comparent deux expressions pour déterminer si elles sont égales, et dans le cas contraire, en quoi elles diffèrent. `Is`, `IsNot`et `Like` sont abordés en détail sur des pages d’aide distinctes. Les opérateurs de comparaison relationnels sont décrits en détail dans cette page.

## <a name="syntax"></a>Syntaxe
  
```vb
result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>Composants
 `result`  
 Requis. Valeur `Boolean` représentant le résultat de la comparaison.

 `expression1`, `expression2`  
 Requis. N'importe quelle expression.

 `comparisonoperator`  
 Requis. N’importe quel opérateur de comparaison relationnel.

 `object1`, `object2`  
 Requis. Noms d’objets de référence.

 `string`  
 Requis. Toute expression `String` .

 `pattern`  
 Requis. Toute expression `String` ou plage de caractères.

## <a name="remarks"></a>Notes
 Le tableau suivant contient une liste des opérateurs de comparaison relationnelle et des conditions qui déterminent si `result` est `True` ou `False`.

|Opérateur|`True` si|`False` si|
|--------------|---------------|----------------|
|`<` (inférieur à)|`expression1` < `expression2`|`expression1` >= `expression2`|
|`<=` (inférieur ou égal à)|`expression1` <= `expression2`|`expression1` > `expression2`|
|`>` (supérieur à)|`expression1` > `expression2`|`expression1` <= `expression2`|
|`>=` (supérieur ou égal à)|`expression1` >= `expression2`|`expression1` < `expression2`|
|`=` (égal à)|`expression1` = `expression2`|`expression1` <> `expression2`|
|`<>` (différent de)|`expression1` <> `expression2`|`expression1` = `expression2`|

> [!NOTE]
> L' [opérateur =](../../../visual-basic/language-reference/operators/assignment-operator.md) est également utilisé comme opérateur d’assignation.

 L’opérateur `Is`, l’opérateur `IsNot` et l’opérateur `Like` ont des fonctionnalités de comparaison spécifiques qui diffèrent des opérateurs dans le tableau précédent.

## <a name="comparing-numbers"></a>Comparaison de nombres
 Lorsque vous comparez une expression de type `Single` à l’une des `Double`de type, l’expression `Single` est convertie en `Double`. Ce comportement est opposé au comportement trouvé dans Visual Basic 6.

 De même, lorsque vous comparez une expression de type `Decimal` à une expression de type `Single` ou `Double`, l’expression `Decimal` est convertie en `Single` ou `Double`. Pour les expressions `Decimal`, toute valeur fractionnaire inférieure à 1E-28 peut être perdue. Une telle perte de valeur fractionnaire peut entraîner une comparaison de deux valeurs égales lorsqu’elles ne le sont pas. Pour cette raison, vous devez prendre soin de l’utilisation de l’égalité (`=`) pour comparer deux variables à virgule flottante. Il est plus sûr de tester si la valeur absolue de la différence entre les deux nombres est inférieure à une petite tolérance acceptable.

### <a name="floating-point-imprecision"></a>Imprécision à virgule flottante
 Lorsque vous travaillez avec des nombres à virgule flottante, gardez à l’esprit qu’ils n’ont pas toujours une représentation précise en mémoire. Cela peut entraîner des résultats inattendus de certaines opérations, telles que la comparaison de valeurs et l' [opérateur mod](../../../visual-basic/language-reference/operators/mod-operator.md). Pour plus d’informations, consultez [Dépannage des types de données](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).

## <a name="comparing-strings"></a>Comparaison de chaînes
 Lorsque vous comparez des chaînes, les expressions de chaîne sont évaluées en fonction de leur ordre de tri alphabétique, qui dépend du paramètre de `Option Compare`.

 `Option Compare Binary` base les comparaisons de chaînes sur un ordre de tri dérivé des représentations binaires internes des caractères. L’ordre de tri est déterminé par la page de codes. L’exemple suivant montre un ordre de tri binaire standard.

 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

 `Option Compare Text` base les comparaisons de chaînes sur un ordre de tri textuel qui ne respecte pas la casse et déterminé par les paramètres régionaux de votre application. Lorsque vous définissez `Option Compare Text` et triez les caractères dans l’exemple précédent, l’ordre de tri de texte suivant s’applique :

 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`

### <a name="locale-dependence"></a>Dépendance des paramètres régionaux
 Lorsque vous définissez `Option Compare Text`, le résultat d’une comparaison de chaînes peut dépendre des paramètres régionaux dans lesquels l’application s’exécute. Deux caractères peuvent être considérés comme égaux dans un paramètre régional, mais pas dans un autre. Si vous utilisez une comparaison de chaînes pour prendre des décisions importantes, par exemple si vous souhaitez accepter une tentative de connexion, vous devez être averti de la sensibilité des paramètres régionaux. Vous pouvez soit définir `Option Compare Binary`, soit appeler l' <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, qui prend en compte les paramètres régionaux.

## <a name="typeless-programming-with-relational-comparison-operators"></a>Programmation sans type avec des opérateurs de comparaison relationnels
 L’utilisation d’opérateurs de comparaison relationnelle avec des expressions `Object` n’est pas autorisée sous `Option Strict On`. Lorsque `Option Strict` est `Off`et que `expression1` ou `expression2` est une expression `Object`, les types au moment de l’exécution déterminent la façon dont ils sont comparés. Le tableau suivant montre comment les expressions sont comparées et le résultat de la comparaison, en fonction du type de Runtime des opérandes.

|Si les opérandes sont|La comparaison est|
|---------------------|-------------------|
|Les deux `String`|Comparaison de tri basée sur les caractéristiques de tri des chaînes.|
|Valeurs numériques|Objets convertis en `Double`, comparaison numérique.|
|Un chiffre et un `String`|La `String` est convertie en `Double` et la comparaison numérique est effectuée. Si la `String` ne peut pas être convertie en `Double`, une <xref:System.InvalidCastException> est levée.|
|L’un ou l’autre ou les deux sont des types référence autres que `String`|Un objet <xref:System.InvalidCastException> est levé.|

 Les comparaisons numériques traitent `Nothing` comme 0. Les comparaisons de chaînes traitent `Nothing` comme `""` (une chaîne vide).

## <a name="overloading"></a>Surcharge
 Les opérateurs de comparaison relationnelles (`<`. `<=`, `>`, `>=`, `=`, `<>`) peuvent être *surchargés*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise l’un de ces opérateurs sur ce type de classe ou de structure, assurez-vous de bien comprendre le comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

 Notez que l' [opérateur =](../../../visual-basic/language-reference/operators/assignment-operator.md) peut être surchargé uniquement comme un opérateur de comparaison relationnel, et non comme un opérateur d’assignation.

## <a name="example"></a>Exemple
 L’exemple suivant illustre différentes utilisations des opérateurs de comparaison relationnelles, que vous utilisez pour comparer des expressions. Les opérateurs de comparaison relationnelles retournent un résultat `Boolean` qui indique si l’expression indiquée prend la valeur `True`. Lorsque vous appliquez les opérateurs `>` et `<` à des chaînes, la comparaison s’effectue à l’aide de l’ordre de tri alphabétique normal des chaînes. Cet ordre peut dépendre de vos paramètres régionaux. Le fait que le tri respecte la casse ou non dépend du paramètre [option compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) .

 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]

 Dans l’exemple précédent, la première comparaison retourne `False` et les comparaisons restantes retournent `True`.

## <a name="see-also"></a>Voir aussi

- <xref:System.InvalidCastException>
- [=, opérateur](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Dépannage des types de données](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Opérateurs de comparaison dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
