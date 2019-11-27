---
title: Precedence, opérateur
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
ms.openlocfilehash: 318fcc3f35276ba0b2061ba9677c5fde29429f6f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348282"
---
# <a name="operator-precedence-in-visual-basic"></a>Priorité des opérateurs en Visual Basic
Lorsque plusieurs opérations se produisent dans une expression, chaque composant est évalué et résolu dans un ordre prédéterminé appelé *priorité d’opérateur*.

## <a name="precedence-rules"></a>Règles de précédence
 Lorsque des expressions contiennent des opérateurs issus de plusieurs catégories, elles sont évaluées en fonction des règles suivantes :

- Les opérateurs arithmétiques et de concaténation ont l’ordre de priorité décrit dans la section suivante, et tous ont une priorité plus élevée que les opérateurs de comparaison, logiques et au niveau du bit.

- Tous les opérateurs de comparaison ont une priorité égale, et tous ont une priorité plus élevée que les opérateurs logiques et au niveau du bit, mais une priorité plus faible que les opérateurs arithmétiques et de concaténation.

- Les opérateurs logiques et au niveau du bit ont l’ordre de priorité décrit dans la section suivante, et tous ont une priorité plus faible que les opérateurs arithmétiques, de concaténation et de comparaison.

- Les opérateurs de même priorité sont évalués de gauche à droite dans l’ordre dans lequel ils apparaissent dans l’expression.

## <a name="precedence-order"></a>Ordre de priorité
 Les opérateurs sont évalués dans l’ordre de priorité suivant :

### <a name="await-operator"></a>Await, opérateur
 Await

### <a name="arithmetic-and-concatenation-operators"></a>Opérateurs arithmétiques et de concaténation
 Élévation à la puissance (`^`)

 Identité et négation unaires (`+`, `–`)

 Multiplication et Division à virgule flottante (`*`, `/`)

 Division d’entier (`\`)

 Arithmétique modulaire (`Mod`)

 Addition et soustraction (`+`, `–`)

 Concaténation de chaînes (`&`)

 Décalage binaire arithmétique (`<<`, `>>`)

### <a name="comparison-operators"></a>Opérateurs de comparaison
 Tous les opérateurs de comparaison (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)

### <a name="logical-and-bitwise-operators"></a>Opérateurs de bits et opérateurs logiques
 Négation (`Not`)

 Conjonction (`And`, `AndAlso`)

 Disjonction inclusive (`Or`, `OrElse`)

 Disjonction exclusive (`Xor`)

### <a name="comments"></a>Commentaires
 L’opérateur `=` est uniquement l’opérateur de comparaison d’égalité, et non l’opérateur d’assignation.

 L’opérateur de concaténation de chaînes (`&`) n’est pas un opérateur arithmétique, mais en priorité il est groupé avec les opérateurs arithmétiques.

 Les opérateurs `Is` et `IsNot` sont des opérateurs de comparaison de référence d’objet. Elles ne comparent pas les valeurs de deux objets ; ils vérifient uniquement si deux variables d’objet font référence à la même instance d’objet.

## <a name="associativity"></a>Associativité
 Lorsque des opérateurs de priorité égale apparaissent ensemble dans une expression, par exemple multiplication et Division, le compilateur évalue chaque opération à mesure qu’elle le rencontre de gauche à droite. L’exemple suivant illustre ces actions.

```vb
Dim n1 As Integer = 96 / 8 / 4
Dim n2 As Integer = (96 / 8) / 4
Dim n3 As Integer = 96 / (8 / 4)
```

 La première expression évalue la division 96/8 (qui donne 12), puis la division 12/4, qui donne trois valeurs. Étant donné que le compilateur évalue les opérations pour `n1` de gauche à droite, l’évaluation est la même lorsque cet ordre est explicitement indiqué pour `n2`. Les deux `n1` et `n2` ont trois résultats. En revanche, `n3` a un résultat de 48, car les parenthèses forcent le compilateur à évaluer 8/4 en premier.

 En raison de ce comportement, on dit que les opérateurs sont *associatifs à gauche* dans Visual Basic.

## <a name="overriding-precedence-and-associativity"></a>Substitution de la priorité et de l’associativité
 Vous pouvez utiliser des parenthèses pour forcer l’évaluation de certaines parties d’une expression avant d’autres. Cela peut remplacer l’ordre de priorité et l’associativité à gauche. Visual Basic effectue toujours des opérations placées entre parenthèses avant celles extérieures à. Toutefois, entre parenthèses, il gère la priorité et l’associativité ordinaires, sauf si vous utilisez des parenthèses entre parenthèses. L’exemple suivant illustre ces actions.

```vb
Dim a, b, c, d, e, f, g As Double
a = 8.0
b = 3.0
c = 4.0
d = 2.0
e = 1.0
f = a - b + c / d * e
' The preceding line sets f to 7.0. Because of natural operator
' precedence and associativity, it is exactly equivalent to the
' following line.
f = (a - b) + ((c / d) * e)
' The following line overrides the natural operator precedence
' and left associativity.
g = (a - (b + c)) / (d * e)
' The preceding line sets g to 0.5.
```

## <a name="see-also"></a>Voir aussi

- [=, opérateur](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [Is (opérateur)](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot (opérateur)](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Like (opérateur)](../../../visual-basic/language-reference/operators/like-operator.md)
- [TypeOf (opérateur)](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Await (opérateur)](../../../visual-basic/language-reference/operators/await-operator.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
