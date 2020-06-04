---
title: Or, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: 657b2a473b23789a8ba25fbd11c6b83538fa7803
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401418"
---
# <a name="or-operator-visual-basic"></a>Or, opérateur (Visual Basic)
Effectue une disjonction logique sur deux `Boolean` expressions, ou une disjonction d’opérations de bits sur deux expressions numériques.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Éléments  
 `result`  
 Obligatoire. Toute expression `Boolean` ou numérique. À des fins de `Boolean` comparaison, `result` est la disjonction logique inclusive de deux `Boolean` valeurs. Pour les opérations au niveau du bit, `result` est une valeur numérique représentant la disjonction de bits inclusive de deux modèles binaires numériques.  
  
 `expression1`  
 Obligatoire. Toute expression `Boolean` ou numérique.  
  
 `expression2`  
 Obligatoire. Toute expression `Boolean` ou numérique.  
  
## <a name="remarks"></a>Notes  
 À des fins de `Boolean` comparaison, `result` est `False` si et seulement si et sont tous deux `expression1` et `expression2` ont la valeur `False` . Le tableau suivant illustre la façon dont `result` est déterminé.  
  
|Si `expression1` est |Et `expression2` est|La valeur de `result` est|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> Dans une `Boolean` comparaison, l' `Or` opérateur évalue toujours les deux expressions, ce qui peut inclure des appels de procédure. L' [opérateur OrElse](orelse-operator.md) effectue *un court-circuit*, ce qui signifie que si `expression1` est `True` , n' `expression2` est pas évalué.  
  
 Pour les opérations au niveau du bit, l' `Or` opérateur effectue une comparaison au niveau du bit des bits positionnés de manière identique dans deux expressions numériques et définit le bit correspondant dans `result` selon le tableau suivant.  
  
|Si le bit dans `expression1` est|Et le bit dans `expression2` est|Le bit dans `result` est|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> Étant donné que les opérateurs logiques et au niveau du bit ont une priorité inférieure à celle des autres opérateurs arithmétiques et relationnels, toutes les opérations au niveau du bit doivent être mises entre parenthèses pour garantir une exécution précise.  
  
## <a name="data-types"></a>Types de données  
 Si les opérandes se composent d’une `Boolean` expression et d’une expression numérique, Visual Basic convertit l' `Boolean` expression en une valeur numérique (– 1 pour `True` et 0 pour `False` ) et effectue une opération au niveau du bit.  
  
 Pour une `Boolean` comparaison, le type de données du résultat est `Boolean` . Pour une comparaison au niveau du bit, le type de données de résultat est un type numérique approprié pour les types de données de `expression1` et `expression2` . Consultez la table « comparaisons et comparaisons au niveau du bit » dans [types de données des résultats d’opérateur](data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Surcharge  
 L' `Or` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `Or` opérateur pour effectuer une disjonction logique inclusive sur deux expressions. Le résultat est une `Boolean` valeur qui indique si l’une ou l’autre des deux expressions est `True` .  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 L’exemple précédent produit les résultats de `True` , `True` et `False` , respectivement.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `Or` opérateur pour effectuer une disjonction logique inclusive sur les bits individuels de deux expressions numériques. Le bit dans le modèle de résultat est défini si l’un des bits correspondants dans les opérandes a la valeur 1.  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 L’exemple précédent produit respectivement les résultats 10, 14 et 14.  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs logiques/de bits (Visual Basic)](logical-bitwise-operators.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [OrElse, opérateur](orelse-operator.md)
- [Opérateurs de bits et opérateurs logiques en Visual Basic](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
