---
title: Or, opérateur (Visual Basic)
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
ms.openlocfilehash: 1d11a6d009f6ecfea9fb1a86b00c67b87d5555dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955840"
---
# <a name="or-operator-visual-basic"></a>Or, opérateur (Visual Basic)
Effectue une disjonction logique sur deux `Boolean` expressions, ou une disjonction d’opérations de bits sur deux expressions numériques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Requis. Toute `Boolean` expression ou numérique. À `Boolean` des fins `result` de comparaison, est la disjonction logique `Boolean` inclusive de deux valeurs. Pour les opérations au `result` niveau du bit, est une valeur numérique représentant la disjonction de bits inclusive de deux modèles binaires numériques.  
  
 `expression1`  
 Requis. Toute `Boolean` expression ou numérique.  
  
 `expression2`  
 Requis. Toute `Boolean` expression ou numérique.  
  
## <a name="remarks"></a>Notes  
 À `Boolean` des fins `result` de `False` comparaison, `expression1` est siet`expression2` seulement si et sont tous deux et ont la valeur. `False` Le tableau suivant illustre la façon `result` dont est déterminé.  
  
|Si `expression1` est|Et `expression2` est|La valeur de `result` est|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> Dans une `Boolean` comparaison, l' `Or` opérateur évalue toujours les deux expressions, ce qui peut inclure des appels de procédure. L' [opérateur OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md) effectue *un court-circuit*, ce qui signifie que `expression1` si `True`est, `expression2` n’est pas évalué.  
  
 Pour les opérations au niveau `Or` du bit, l’opérateur effectue une comparaison au niveau du bit des bits positionnés de manière identique dans `result` deux expressions numériques et définit le bit correspondant dans selon le tableau suivant.  
  
|Si le bit `expression1` dans est|Et le bit `expression2` dans est|Le bit dans `result` est|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> Étant donné que les opérateurs logiques et au niveau du bit ont une priorité inférieure à celle des autres opérateurs arithmétiques et relationnels, toutes les opérations au niveau du bit doivent être mises entre parenthèses pour garantir une exécution précise.  
  
## <a name="data-types"></a>Types de données  
 Si `Boolean` les opérandes se composent d’une expression et d’une expression numérique, Visual Basic convertit l’expression en une valeur numérique (– 1 pour `True` et 0 pour `False`) et effectue une opération au niveau du `Boolean` bit.  
  
 Pour une `Boolean` comparaison, le type de données du résultat est `Boolean`. Pour une comparaison au niveau du bit, le type de données de résultat est un type numérique approprié `expression1` pour `expression2`les types de données de et. Consultez la table «comparaisons et comparaisons au niveau du bit» dans [types de données des résultats d’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Surcharge  
 L' `Or` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `Or` opérateur pour effectuer une disjonction logique inclusive sur deux expressions. Le résultat est une `Boolean` valeur qui indique si l’une ou l’autre des `True`deux expressions est.  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 L’exemple précédent produit les résultats `True`de `True`, et `False`, respectivement.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `Or` opérateur pour effectuer une disjonction logique inclusive sur les bits individuels de deux expressions numériques. Le bit dans le modèle de résultat est défini si l’un des bits correspondants dans les opérandes a la valeur 1.  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 L’exemple précédent produit respectivement les résultats 10, 14 et 14.  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs logiques/de bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [OrElse (opérateur)](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [Opérateurs logiques et au niveau du bit dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
