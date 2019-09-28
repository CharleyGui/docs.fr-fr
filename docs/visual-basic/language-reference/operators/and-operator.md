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
ms.openlocfilehash: bd6ebbf5f53a7cf187b5d8ce7630080d44d46df2
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591613"
---
# <a name="and-operator-visual-basic"></a>And, opérateur (Visual Basic)
Effectue une conjonction logique sur deux expressions `Boolean`, ou une conjonction d’opérations de bits sur deux expressions numériques.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Obligatoire. Toute `Boolean` expression ou numérique. Pour la comparaison booléenne, `result` est la conjonction logique de deux valeurs `Boolean`. Pour les opérations au niveau du bit, `result` est une valeur numérique représentant la conjonction au niveau du bit de deux modèles binaires numériques.  
  
 `expression1`  
 Obligatoire. Toute `Boolean` expression ou numérique.  
  
 `expression2`  
 Obligatoire. Toute `Boolean` expression ou numérique.  
  
## <a name="remarks"></a>Notes  
 Pour la comparaison booléenne, `result` est `True` si et seulement si `expression1` et `expression2` ont pour valeur `True`. Le tableau suivant illustre la façon dont `result` est déterminé.  
  
|Si `expression1` est|Et `expression2` est|La valeur de `result` est|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> Dans une comparaison booléenne, l’opérateur `And` évalue toujours les deux expressions, ce qui peut inclure des appels de procédure. L' [opérateur AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) effectue *un court-circuit*, ce qui signifie que si `expression1` est `False`, `expression2` n’est pas évalué.  
  
 En cas d’application à des valeurs numériques, l’opérateur `And` effectue une comparaison au niveau du bit des bits positionnés de manière identique dans deux expressions numériques et définit le bit correspondant dans `result` en fonction du tableau suivant.  
  
|Si le bit de `expression1` est|Et bit dans `expression2` est|Le bit dans `result` est|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
> Étant donné que les opérateurs logiques et au niveau du bit ont une priorité inférieure à celle des autres opérateurs arithmétiques et relationnels, toutes les opérations au niveau du bit doivent être mises entre parenthèses pour garantir des résultats précis.  
  
## <a name="data-types"></a>Types de données  
 Si les opérandes se composent d’une expression `Boolean` et d’une expression numérique, Visual Basic convertit l’expression `Boolean` en valeur numérique (– 1 pour `True` et 0 pour `False`) et effectue une opération au niveau du bit.  
  
 Pour une comparaison booléenne, le type de données du résultat est `Boolean`. Pour une comparaison au niveau du bit, le type de données de résultat est un type numérique approprié pour les types de données de `expression1` et `expression2`. Consultez la table « comparaisons et comparaisons au niveau du bit » dans [types de données des résultats d’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
> [!NOTE]
> L’opérateur `And` peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’opérateur `And` pour effectuer une conjonction logique sur deux expressions. Le résultat est une valeur `Boolean` qui indique si les deux expressions sont `True`.  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 L’exemple précédent produit les résultats de `True` et `False`, respectivement.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’opérateur `And` pour effectuer une conjonction logique sur les bits individuels de deux expressions numériques. Le bit dans le modèle de résultat est défini si les bits correspondants dans les opérandes ont tous les deux la valeur 1.  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 L’exemple précédent produit respectivement les résultats 8, 2 et 0.  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs logiques/de bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [AndAlso (opérateur)](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [Opérateurs logiques et au niveau du bit dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
