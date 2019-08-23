---
title: And, opérateur (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: a1802d3a7018b1b6190ff5601eba055e16e62371
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913167"
---
# <a name="and-operator-visual-basic"></a>And, opérateur (Visual Basic)
Effectue une conjonction logique sur `Boolean` deux expressions ou une conjonction au niveau du bit sur deux expressions numériques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Requis. Toute `Boolean` expression ou numérique. Pour la comparaison booléenne `result` , est la conjonction logique `Boolean` de deux valeurs. Pour les opérations au `result` niveau du bit, est une valeur numérique représentant la conjonction au niveau du bit de deux modèles binaires numériques.  
  
 `expression1`  
 Requis. Toute `Boolean` expression ou numérique.  
  
 `expression2`  
 Requis. Toute `Boolean` expression ou numérique.  
  
## <a name="remarks"></a>Notes  
 Pour la comparaison booléenne `result` , `True` est `expression1` si et seulement `True`si et `expression2` ont la valeur. Le tableau suivant illustre la façon `result` dont est déterminé.  
  
|Si `expression1` est|Et `expression2` est|La valeur de `result` est|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> Dans une comparaison booléenne, l' `And` opérateur évalue toujours les deux expressions, ce qui peut inclure des appels de procédure. L' [opérateur AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) effectue *un court-circuit*, ce qui signifie que `expression1` si `False`est, `expression2` n’est pas évalué.  
  
 Lorsqu’il est appliqué à des valeurs `And` numériques, l’opérateur effectue une comparaison au niveau du bit des bits positionnés de manière identique dans deux `result` expressions numériques et définit le bit correspondant dans selon le tableau suivant.  
  
|Si le bit `expression1` dans est|Et le bit `expression2` dans est|Le bit dans `result` est|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
> Étant donné que les opérateurs logiques et au niveau du bit ont une priorité inférieure à celle des autres opérateurs arithmétiques et relationnels, toutes les opérations au niveau du bit doivent être mises entre parenthèses pour garantir des résultats précis.  
  
## <a name="data-types"></a>Types de données  
 Si `Boolean` les opérandes se composent d’une expression et d’une expression numérique, Visual Basic convertit l’expression en une valeur numérique (– 1 pour `True` et 0 pour `False`) et effectue une opération au niveau du `Boolean` bit.  
  
 Pour une comparaison booléenne, le type de données du résultat est `Boolean`. Pour une comparaison au niveau du bit, le type de données de résultat est un type numérique approprié `expression1` pour `expression2`les types de données de et. Consultez la table «comparaisons et comparaisons au niveau du bit» dans [types de données des résultats d’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
> [!NOTE]
> L' `And` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `And` opérateur pour effectuer une conjonction logique sur deux expressions. Le résultat est une `Boolean` valeur qui indique si les deux expressions sont. `True`  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 L’exemple précédent produit les résultats `True` de `False`et, respectivement.  
  
## <a name="example"></a>Exemples  
 L’exemple suivant utilise l' `And` opérateur pour effectuer une conjonction logique sur les bits individuels de deux expressions numériques. Le bit dans le modèle de résultat est défini si les bits correspondants dans les opérandes ont tous les deux la valeur 1.  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 L’exemple précédent produit respectivement les résultats 8, 2 et 0.  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs logiques/de bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [AndAlso (opérateur)](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [Opérateurs logiques et au niveau du bit dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
