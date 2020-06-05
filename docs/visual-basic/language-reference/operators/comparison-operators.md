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
ms.openlocfilehash: bcd51d70c5c7bd08991c7433e244316a82daa9da
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371789"
---
# <a name="comparison-operators-visual-basic"></a>Opérateurs de comparaison (Visual Basic)
Voici les opérateurs de comparaison définis dans Visual Basic.

 `<`and

 `<=`and

 `>`and

 `>=`and

 `=`and

 `<>`and

 [Is, opérateur](is-operator.md)

 [IsNot, opérateur](isnot-operator.md)

 [Like, opérateur](like-operator.md)

 Ces opérateurs comparent deux expressions pour déterminer si elles sont égales, et dans le cas contraire, en quoi elles diffèrent. `Is`, `IsNot` et `Like` sont abordés en détail sur des pages d’aide distinctes. Les opérateurs de comparaison relationnels sont décrits en détail dans cette page.

## <a name="syntax"></a>Syntaxe
  
```vb
result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>Éléments
 `result`  
 Obligatoire. `Boolean`Valeur représentant le résultat de la comparaison.

 `expression1`, `expression2`  
 Obligatoire. Toute expression.

 `comparisonoperator`  
 Obligatoire. N’importe quel opérateur de comparaison relationnel.

 `object1`, `object2`  
 Obligatoire. Noms d’objets de référence.

 `string`  
 Obligatoire. Toute expression `String` .

 `pattern`  
 Obligatoire. Toute `String` expression ou plage de caractères.

## <a name="remarks"></a>Notes
 Le tableau suivant contient une liste des opérateurs de comparaison relationnelle et des conditions qui déterminent si a la valeur `result` `True` ou `False` .

|Opérateur|`True` si|`False` si|
|--------------|---------------|----------------|
|`<`(Inférieur à)|`expression1` < `expression2`|`expression1` >= `expression2`|
|`<=`(Inférieur ou égal à)|`expression1` <= `expression2`|`expression1` > `expression2`|
|`>`(Supérieur à)|`expression1` > `expression2`|`expression1` <= `expression2`|
|`>=`(Supérieur ou égal à)|`expression1` >= `expression2`|`expression1` < `expression2`|
|`=`(Égal à)|`expression1` = `expression2`|`expression1` <> `expression2`|
|`<>`(Différent de)|`expression1` <> `expression2`|`expression1` = `expression2`|

> [!NOTE]
> L' [opérateur =](assignment-operator.md) est également utilisé comme opérateur d’assignation.

 L’opérateur `Is` , l' `IsNot` opérateur et l' `Like` opérateur ont des fonctionnalités de comparaison spécifiques qui diffèrent des opérateurs dans le tableau précédent.

## <a name="comparing-numbers"></a>Comparaison de nombres
 Lorsque vous comparez une expression de type `Single` à l’un des types `Double` , l' `Single` expression est convertie en `Double` . Ce comportement est opposé au comportement trouvé dans Visual Basic 6.

 De même, lorsque vous comparez une expression de type `Decimal` à une expression de type `Single` ou `Double` , l' `Decimal` expression est convertie en `Single` ou `Double` . Pour les `Decimal` expressions, toute valeur fractionnaire inférieure à 1e-28 peut être perdue. Une telle perte de valeur fractionnaire peut entraîner une comparaison de deux valeurs égales lorsqu’elles ne le sont pas. Pour cette raison, vous devez prendre soin de l’utilisation de l’égalité ( `=` ) pour comparer deux variables à virgule flottante. Il est plus sûr de tester si la valeur absolue de la différence entre les deux nombres est inférieure à une petite tolérance acceptable.

### <a name="floating-point-imprecision"></a>Imprécision à virgule flottante
 Lorsque vous travaillez avec des nombres à virgule flottante, gardez à l’esprit qu’ils n’ont pas toujours une représentation précise en mémoire. Cela peut entraîner des résultats inattendus de certaines opérations, telles que la comparaison de valeurs et l' [opérateur mod](mod-operator.md). Pour plus d’informations, consultez [Dépannage des types de données](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).

## <a name="comparing-strings"></a>Comparaison de chaînes
 Lorsque vous comparez des chaînes, les expressions de chaîne sont évaluées en fonction de leur ordre de tri alphabétique, qui dépend du `Option Compare` paramètre.

 `Option Compare Binary`base les comparaisons de chaînes sur un ordre de tri dérivé des représentations binaires internes des caractères. L’ordre de tri est déterminé par la page de codes. L’exemple suivant montre un ordre de tri binaire standard.

 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

 `Option Compare Text`base les comparaisons de chaînes sur un ordre de tri textuel qui ne respecte pas la casse et déterminé par les paramètres régionaux de votre application. Lorsque vous définissez `Option Compare Text` et triez les caractères dans l’exemple précédent, l’ordre de tri de texte suivant s’applique :

 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`

### <a name="locale-dependence"></a>Dépendance des paramètres régionaux
 Lorsque vous définissez `Option Compare Text` , le résultat d’une comparaison de chaînes peut dépendre des paramètres régionaux dans lesquels l’application s’exécute. Deux caractères peuvent être considérés comme égaux dans un paramètre régional, mais pas dans un autre. Si vous utilisez une comparaison de chaînes pour prendre des décisions importantes, par exemple si vous souhaitez accepter une tentative de connexion, vous devez être averti de la sensibilité des paramètres régionaux. Envisagez de définir `Option Compare Binary` ou d’appeler le <xref:Microsoft.VisualBasic.Strings.StrComp%2A> , qui prend en compte les paramètres régionaux.

## <a name="typeless-programming-with-relational-comparison-operators"></a>Programmation sans type avec des opérateurs de comparaison relationnels
 L’utilisation d’opérateurs de comparaison relationnels avec des `Object` expressions n’est pas autorisée sous `Option Strict On` . Lorsque `Option Strict` a `Off` la valeur et `expression1` ou ou `expression2` est une `Object` expression, les types d’exécution déterminent la façon dont ils sont comparés. Le tableau suivant montre comment les expressions sont comparées et le résultat de la comparaison, en fonction du type de Runtime des opérandes.

|Si les opérandes sont|La comparaison est|
|---------------------|-------------------|
|Versions`String`|Comparaison de tri basée sur les caractéristiques de tri des chaînes.|
|Valeurs numériques|Objets convertis en `Double` , comparaison numérique.|
|Un numérique et un`String`|La `String` est convertie en une `Double` comparaison numérique et est effectuée. Si `String` ne peut pas être converti en `Double` , une <xref:System.InvalidCastException> exception est levée.|
|L’un ou l’autre ou les deux sont des types référence autres que`String`|Un objet <xref:System.InvalidCastException> est levé.|

 Les comparaisons numériques sont traitées `Nothing` comme 0. Les comparaisons de chaînes traitent `Nothing` comme `""` (une chaîne vide).

## <a name="overloading"></a>Surcharge
 Opérateurs de comparaison relationnelles ( `<` . `<=`, `>` , `>=` , `=` , `<>` ) peuvent être *surchargés*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure. Si votre code utilise l’un de ces opérateurs sur ce type de classe ou de structure, assurez-vous de bien comprendre le comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).

 Notez que l' [opérateur =](assignment-operator.md) peut être surchargé uniquement comme un opérateur de comparaison relationnel, et non comme un opérateur d’assignation.

## <a name="example"></a>Exemple
 L’exemple suivant illustre différentes utilisations des opérateurs de comparaison relationnelles, que vous utilisez pour comparer des expressions. Les opérateurs de comparaison relationnels retournent un `Boolean` résultat qui indique si l’expression indiquée prend la valeur `True` . Lorsque vous appliquez les `>` `<` opérateurs et à des chaînes, la comparaison s’effectue à l’aide de l’ordre de tri alphabétique normal des chaînes. Cet ordre peut dépendre de vos paramètres régionaux. Le fait que le tri respecte la casse ou non dépend du paramètre [option compare](../statements/option-compare-statement.md) .

 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]

 Dans l’exemple précédent, la première comparaison retourne `False` et les comparaisons restantes retournent `True` .

## <a name="see-also"></a>Voir aussi

- <xref:System.InvalidCastException>
- [= (Opérateur)](assignment-operator.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [Dépannage des types de données](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Comparison Operators in Visual Basic](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
