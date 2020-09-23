---
title: Opérateurs de comparaison
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- comparison operators [Visual Basic], comparing objects
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers [Visual Basic], comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values [Visual Basic], comparing
- comparison operators [Visual Basic], comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
ms.openlocfilehash: fbe81532bb435e54e694f9b5fe9dd497392f31e1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071766"
---
# <a name="comparison-operators-in-visual-basic"></a>Opérateurs de comparaison en Visual Basic

Les opérateurs de comparaison comparent deux expressions et retournent une `Boolean` valeur qui représente la relation de leurs valeurs. Il existe des opérateurs pour comparer des valeurs numériques, des opérateurs pour comparer des chaînes et des opérateurs pour la comparaison d’objets. Les trois types d’opérateurs sont décrits dans le présent document.  
  
## <a name="comparing-numeric-values"></a>Comparaison de valeurs numériques  

 Visual Basic compare les valeurs numériques à l’aide de six opérateurs de comparaison numériques. Chaque opérateur prend comme opérande deux expressions qui correspondent à des valeurs numériques. Le tableau suivant répertorie les opérateurs et donne des exemples de chacun d’eux.  
  
|Opérateur|Condition testée|Exemples|  
|--------------|----------------------|--------------|  
|`=` D’égalité|La valeur de la première expression est-elle égale à la valeur du deuxième ?|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>` D’inégalité|La valeur de la première expression est-elle différente de la valeur du deuxième ?|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<` (Inférieur à)|La valeur de la première expression est-elle inférieure à la valeur du deuxième ?|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>` (Supérieur à)|La valeur de la première expression est-elle supérieure à la valeur du deuxième ?|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=` (Inférieur ou égal à)|La valeur de la première expression est-elle inférieure ou égale à la valeur du deuxième ?|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=` (Supérieur ou égal à)|La valeur de la première expression est-elle supérieure ou égale à la valeur du deuxième ?|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>Comparaison de chaînes  

 Visual Basic compare les chaînes à l’aide de l' [opérateur Like](../../../language-reference/operators/like-operator.md) et des opérateurs de comparaison numériques. L' `Like` opérateur vous permet de spécifier un modèle. La chaîne est ensuite comparée au modèle et, si elle correspond, le résultat est `True` . Sinon, le résultat est `False`. Les opérateurs numériques vous permettent de comparer des `String` valeurs en fonction de leur ordre de tri, comme le montre l’exemple suivant.  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 Le résultat de l’exemple précédent est `True` dû au fait que le premier caractère de la première chaîne est trié avant le premier caractère de la deuxième chaîne. Si les premiers caractères étaient égaux, la comparaison se poursuit jusqu’au caractère suivant dans les deux chaînes, et ainsi de suite. Vous pouvez également tester l’égalité des chaînes à l’aide de l’opérateur d’égalité, comme le montre l’exemple suivant.  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 Si une chaîne est le préfixe d’une autre, telle que « AA » et « AAA », la chaîne la plus longue est considérée comme supérieure à la chaîne la plus petite. L'exemple suivant illustre ce comportement.  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 L’ordre de tri est basé sur une comparaison binaire ou une comparaison textuelle, en fonction du paramètre de `Option Compare` . Pour plus d’informations, consultez [instruction Option Compare](../../../language-reference/statements/option-compare-statement.md).  
  
## <a name="comparing-objects"></a>Comparaison d’objets  

 Visual Basic compare deux variables de référence d’objet à l’aide de l' [opérateur is](../../../language-reference/operators/is-operator.md) et de l' [opérateur IsNot](../../../language-reference/operators/isnot-operator.md). Vous pouvez utiliser l’un de ces opérateurs pour déterminer si deux variables de référence font référence à la même instance d’objet. L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrOperators#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#65)]  
  
 Dans l’exemple précédent, a la `x Is y` valeur `True` , car les deux variables font référence à la même instance. Comparez ce résultat avec l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#66)]  
  
 Dans l’exemple précédent, a la `x Is y` valeur `False` , car bien que les variables fassent référence à des objets du même type, elles font référence à des instances différentes de ce type.  
  
 Lorsque vous souhaitez tester deux objets qui ne pointent pas vers la même instance, l' `IsNot` opérateur vous permet d’éviter une combinaison par programmation de `Not` et `Is` . L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrOperators#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#67)]  
  
 Dans l’exemple précédent, `If a IsNot b` est équivalent à `If Not a Is b` .  
  
### <a name="comparing-object-type"></a>Comparaison du type d’objet  

 Vous pouvez tester si un objet est d’un type particulier avec l' `TypeOf` expression... `Is` . La syntaxe est la suivante :  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 Lorsque `typename` spécifie un type d’interface, l' `TypeOf` expression... `Is` retourne `True` si l’objet implémente le type d’interface. Quand `typename` est un type de classe, l’expression retourne `True` si l’objet est une instance de la classe spécifiée ou d’une classe qui dérive de la classe spécifiée. L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrOperators#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#68)]  
  
 Dans l’exemple précédent, l' `TypeOf x Is Control` expression prend la valeur, `True` car le type de `x` est `Button` , ce qui hérite de `Control` .  
  
 Pour plus d’informations, consultez [opérateur typeof](../../../language-reference/operators/typeof-operator.md).  
  
## <a name="see-also"></a>Voir aussi

- [Comparaisons de valeurs](value-comparisons.md)
- [Opérateurs de comparaison](../../../language-reference/operators/comparison-operators.md)
- [Opérateurs](../../../language-reference/operators/index.md)
- [Opérateurs arithmétiques en Visual Basic](arithmetic-operators.md)
- [Opérateurs de concaténation (Visual Basic)](concatenation-operators.md)
- [Opérateurs de bits et opérateurs logiques en Visual Basic](logical-and-bitwise-operators.md)
