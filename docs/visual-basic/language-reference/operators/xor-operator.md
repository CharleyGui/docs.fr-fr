---
title: Xor, opérateur (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Xor
helpviewer_keywords:
- exclusive OR operator [Visual Basic]
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator [Visual Basic]
- operators [Visual Basic], bitwise
- bitwise operators [Visual Basic], XOR operator
- Xor operator [Visual Basic]
- Xor keyword [Visual Basic]
- bitwise comparison [Visual Basic]
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
ms.openlocfilehash: d82018a3018e2cf4362b9904ed127c20f56f6f0c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701270"
---
# <a name="xor-operator-visual-basic"></a>Xor, opérateur (Visual Basic)
Effectue une exclusion logique sur deux expressions `Boolean`, ou une exclusion de bits sur deux expressions numériques.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Obligatoire. Toute variable `Boolean` ou numérique. Pour la comparaison booléenne, `result` est l’exclusion logique (disjonction logique exclusive) de deux valeurs `Boolean`. Pour les opérations au niveau du bit, `result` est une valeur numérique qui représente l’exclusion de bits (disjonction de bits exclusive) de deux modèles binaires numériques.  
  
 `expression1`  
 Obligatoire. Toute `Boolean` expression ou numérique.  
  
 `expression2`  
 Obligatoire. Toute `Boolean` expression ou numérique.  
  
## <a name="remarks"></a>Notes  
 Pour la comparaison booléenne, `result` est `True` si et seulement si un seul des `expression1` et `expression2` a la valeur `True`. Autrement dit, si et seulement si `expression1` et `expression2` correspondent à des valeurs `Boolean` opposées. Le tableau suivant illustre la façon dont `result` est déterminé.  
  
|Si `expression1` est|Et `expression2` est|La valeur de `result` est|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> Dans une comparaison booléenne, l’opérateur `Xor` évalue toujours les deux expressions, ce qui peut inclure des appels de procédure. Il n’existe pas d’équivalent court-circuit à `Xor`, car le résultat dépend toujours des deux opérandes. Pour les opérateurs logiques de *court-circuit* , consultez l' [opérateur AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) et l' [opérateur OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
 Pour les opérations au niveau du bit, l’opérateur `Xor` effectue une comparaison au niveau du bit des bits positionnés de manière identique dans deux expressions numériques et définit le bit correspondant dans `result` selon le tableau suivant.  
  
|Si le bit de `expression1` est|Et bit dans `expression2` est|Le bit dans `result` est|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> Étant donné que les opérateurs logiques et au niveau du bit ont une priorité inférieure à celle des autres opérateurs arithmétiques et relationnels, toutes les opérations au niveau du bit doivent être mises entre parenthèses pour garantir une exécution précise.  
  
 Par exemple, 5 `Xor` 3 est 6. Pour comprendre pourquoi c’est le cas, convertissez 5 et 3 en leurs représentations binaires, 101 et 011. Utilisez ensuite le tableau précédent pour déterminer que 101 XOR 011 est 110, qui est la représentation binaire du nombre décimal 6.  
  
## <a name="data-types"></a>Types de données  
 Si les opérandes se composent d’une expression `Boolean` et d’une expression numérique, Visual Basic convertit l’expression `Boolean` en valeur numérique (– 1 pour `True` et 0 pour `False`) et effectue une opération au niveau du bit.  
  
 Pour une comparaison `Boolean`, le type de données du résultat est `Boolean`. Pour une comparaison au niveau du bit, le type de données de résultat est un type numérique approprié pour les types de données de `expression1` et `expression2`. Consultez la table « comparaisons et comparaisons au niveau du bit » dans [types de données des résultats d’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Surcharge  
 L’opérateur `Xor` peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur ce type de classe ou de structure, assurez-vous que vous comprenez son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’opérateur `Xor` pour effectuer une exclusion logique (disjonction logique exclusive) sur deux expressions. Le résultat est une valeur `Boolean` qui indique si exactement une des expressions est `True`.  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 L’exemple précédent produit les résultats de `False`, `True` et `False`, respectivement.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’opérateur `Xor` pour effectuer une exclusion logique (disjonction logique exclusive) sur les bits individuels de deux expressions numériques. Le bit dans le modèle de résultat est défini si exactement l’un des bits correspondants dans les opérandes a la valeur 1.  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 L’exemple précédent produit respectivement les résultats 2, 12 et 14.  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs logiques/de bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Opérateurs logiques et au niveau du bit dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
