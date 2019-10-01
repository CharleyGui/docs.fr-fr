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
ms.openlocfilehash: 03decb4ad32e8ff2c03e3b64a272bce779282973
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701240"
---
# <a name="or-operator-visual-basic"></a>Or, opérateur (Visual Basic)
Effectue une disjonction logique sur deux expressions `Boolean`, ou une disjonction d’opérations de bits sur deux expressions numériques.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Obligatoire. Toute `Boolean` expression ou numérique. Pour la comparaison `Boolean`, `result` est la disjonction logique inclusive de deux valeurs `Boolean`. Pour les opérations au niveau du bit, `result` est une valeur numérique représentant la disjonction de bits inclusive de deux modèles binaires numériques.  
  
 `expression1`  
 Obligatoire. Toute `Boolean` expression ou numérique.  
  
 `expression2`  
 Obligatoire. Toute `Boolean` expression ou numérique.  
  
## <a name="remarks"></a>Notes  
 Pour la comparaison `Boolean`, `result` est `False` si et seulement si les `expression1` et `expression2` prennent la valeur `False`. Le tableau suivant illustre la façon dont `result` est déterminé.  
  
|Si `expression1` est|Et `expression2` est|La valeur de `result` est|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> Dans une comparaison `Boolean`, l’opérateur `Or` évalue toujours les deux expressions, ce qui peut inclure des appels de procédure. L' [opérateur OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md) effectue *un court-circuit*, ce qui signifie que si `expression1` est `True`, `expression2` n’est pas évalué.  
  
 Pour les opérations au niveau du bit, l’opérateur `Or` effectue une comparaison au niveau du bit des bits positionnés de manière identique dans deux expressions numériques et définit le bit correspondant dans `result` selon le tableau suivant.  
  
|Si le bit de `expression1` est|Et bit dans `expression2` est|Le bit dans `result` est|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> Étant donné que les opérateurs logiques et au niveau du bit ont une priorité inférieure à celle des autres opérateurs arithmétiques et relationnels, toutes les opérations au niveau du bit doivent être mises entre parenthèses pour garantir une exécution précise.  
  
## <a name="data-types"></a>Types de données  
 Si les opérandes se composent d’une expression `Boolean` et d’une expression numérique, Visual Basic convertit l’expression `Boolean` en valeur numérique (– 1 pour `True` et 0 pour `False`) et effectue une opération au niveau du bit.  
  
 Pour une comparaison `Boolean`, le type de données du résultat est `Boolean`. Pour une comparaison au niveau du bit, le type de données de résultat est un type numérique approprié pour les types de données de `expression1` et `expression2`. Consultez la table « comparaisons et comparaisons au niveau du bit » dans [types de données des résultats d’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Surcharge  
 L’opérateur `Or` peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’opérateur `Or` pour effectuer une disjonction logique inclusive sur deux expressions. Le résultat est une valeur `Boolean` qui indique si l’une ou l’autre des deux expressions est `True`.  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 L’exemple précédent produit les résultats de `True`, `True` et `False`, respectivement.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’opérateur `Or` pour effectuer une disjonction logique inclusive sur les bits individuels de deux expressions numériques. Le bit dans le modèle de résultat est défini si l’un des bits correspondants dans les opérandes a la valeur 1.  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 L’exemple précédent produit respectivement les résultats 10, 14 et 14.  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs logiques/de bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [OrElse (opérateur)](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [Opérateurs logiques et au niveau du bit dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
