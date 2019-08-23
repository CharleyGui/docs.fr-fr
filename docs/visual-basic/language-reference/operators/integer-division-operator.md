---
title: '\, opérateur (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: 276071fef3632d1a617f177b6fe18026b290103a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917236"
---
# <a name="-operator-visual-basic"></a>\, opérateur (Visual Basic)
Divise deux nombres et retourne un résultat entier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression1 \ expression2  
```  
  
## <a name="parts"></a>Composants  
 `expression1`  
 Requis. Toute expression numérique.  
  
 `expression2`  
 Requis. Toute expression numérique.  
  
## <a name="supported-types"></a>Types pris en charge  
 Tous les types numériques, y compris les types `Decimal`à virgule flottante non signée et.  
  
## <a name="result"></a>Résultat  
 Le résultat est le quotient entier de `expression1` divisé par `expression2`, qui ignore tout reste et conserve uniquement la partie entière. C’est ce quel’on appelle la troncation.  
  
 Le type de données de résultat est un type numérique approprié pour les types `expression1` de `expression2`données de et. Consultez les tables «arithmétiques sur les entiers» dans [types de données des résultats d’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
 L' [opérateur/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) retourne le quotient complet, qui conserve le reste dans la partie fractionnaire.  
  
## <a name="remarks"></a>Notes  
 Avant d’effectuer la Division, Visual Basic tente de convertir une expression numérique à virgule flottante en `Long`. Si `Option Strict` est`On`, une erreur de compilateur se produit. Si `Option Strict` est `Off`, un<xref:System.OverflowException> est possible si la valeur est en dehors de la plage du [type de données long](../../../visual-basic/language-reference/data-types/long-data-type.md). La conversion vers `Long` est également soumise à l' *arrondi bancaire*. Pour plus d’informations, consultez «parties fractionnaires» dans les [fonctions de conversion de type](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Si `expression1` ou`expression2` a la valeur [Nothing](../../../visual-basic/language-reference/nothing.md), il est traité comme zéro.  
  
## <a name="attempted-division-by-zero"></a>Division par zéro  
 Si `expression2` la valeur de est égale à `\` zéro, l’opérateur <xref:System.DivideByZeroException> lève une exception. Cela est vrai pour tous les types de données numériques des opérandes.  
  
> [!NOTE]
> L' `\` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `\` opérateur pour effectuer une division d’entier. Le résultat est un entier qui représente le quotient entier des deux opérandes, le reste étant ignoré.  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 Dans l’exemple précédent, les expressions retournent respectivement les valeurs 2, 3, 33 et-22.  
  
## <a name="see-also"></a>Voir aussi

- [\\= (Opérateur)](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [/, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [Option Strict (instruction)](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Opérateurs arithmétiques dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
