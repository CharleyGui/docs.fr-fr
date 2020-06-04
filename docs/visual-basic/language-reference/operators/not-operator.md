---
title: Not, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 56cdeb80a217dbce15921eddd6a43d8d1b049376
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401457"
---
# <a name="not-operator-visual-basic"></a>Not, opérateur (Visual Basic)
Effectue une négation logique sur une `Boolean` expression ou une négation au niveau du bit sur une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a>Éléments  
 `result`  
 Obligatoire. Toute expression `Boolean` ou numérique.  
  
 `expression`  
 Obligatoire. Toute expression `Boolean` ou numérique.  
  
## <a name="remarks"></a>Notes  
 Pour `Boolean` les expressions, le tableau suivant illustre la façon dont `result` est déterminé.  
  
|Si `expression` est |La valeur de `result` est|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 Pour les expressions numériques, l' `Not` opérateur inverse les valeurs de bit d’une expression numérique et définit le bit correspondant dans `result` selon le tableau suivant.  
  
|Si le bit dans `expression` est|Le bit dans `result` est|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
> Étant donné que les opérateurs logiques et au niveau du bit ont une priorité inférieure à celle des autres opérateurs arithmétiques et relationnels, toutes les opérations au niveau du bit doivent être mises entre parenthèses pour garantir une exécution précise.  
  
## <a name="data-types"></a>Types de données  
 Pour une négation booléenne, le type de données du résultat est `Boolean` . Pour une négation au niveau du bit, le type de données de résultat est le même que celui de `expression` . Toutefois, si l’expression est `Decimal` , le résultat est `Long` .  
  
## <a name="overloading"></a>Surcharge  
 L' `Not` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsque son opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `Not` opérateur pour effectuer une négation logique sur une `Boolean` expression. Le résultat est une `Boolean` valeur qui représente l’inverse de la valeur de l’expression.  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 L’exemple précédent produit les résultats de `False` et `True` , respectivement.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `Not` opérateur pour effectuer une négation logique des bits individuels d’une expression numérique. Le bit dans le modèle de résultat est défini à l’inverse du bit correspondant dans le modèle d’opérande, y compris le bit de signe.  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 L’exemple précédent produit respectivement les résultats-11, – 9 et-7.  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs logiques/de bits (Visual Basic)](logical-bitwise-operators.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [Opérateurs de bits et opérateurs logiques en Visual Basic](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
