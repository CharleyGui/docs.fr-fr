---
title: '\, opérateur'
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
ms.openlocfilehash: cf2dc66532925d56cea6fd141f44a245bc2dd8dd
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873395"
---
# <a name="-operator-visual-basic"></a>\, opérateur (Visual Basic)

Effectue la division entre deux nombres et retourne un résultat sous forme d'entier.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
expression1 \ expression2  
```  
  
## <a name="parts"></a>Éléments  

 `expression1`  
 Obligatoire. Toute expression numérique.  
  
 `expression2`  
 Obligatoire. Toute expression numérique.  
  
## <a name="supported-types"></a>Types pris en charge  

 Tous les types numériques, y compris les types à virgule flottante non signée et `Decimal` .  
  
## <a name="result"></a>Résultats  

 Le résultat est le quotient entier de `expression1` divisé par `expression2` , qui ignore tout reste et conserve uniquement la partie entière. C’est ce que l’on appelle la *troncation*.  
  
 Le type de données de résultat est un type numérique approprié pour les types de données de `expression1` et `expression2` . Consultez les tables « arithmétiques sur les entiers » dans [types de données des résultats d’opérateur](data-types-of-operator-results.md).  
  
 L' [opérateur/(Visual Basic)](floating-point-division-operator.md) retourne le quotient complet, qui conserve le reste dans la partie fractionnaire.  
  
## <a name="remarks"></a>Notes  

 Avant d’effectuer la Division, Visual Basic tente de convertir une expression numérique à virgule flottante en `Long` . Si `Option Strict` est `On` , une erreur de compilateur se produit. Si `Option Strict` est `Off` , un <xref:System.OverflowException> est possible si la valeur est en dehors de la plage du [type de données long](../data-types/long-data-type.md). La conversion vers `Long` est également soumise à l' *arrondi bancaire*. Pour plus d’informations, consultez « parties fractionnaires » dans les [fonctions de conversion de type](../functions/type-conversion-functions.md).  
  
 Si `expression1` ou `expression2` a la valeur [Nothing](../nothing.md), il est traité comme zéro.  
  
## <a name="attempted-division-by-zero"></a>Division par zéro  

 Si `expression2` la valeur de est égale à zéro, l' `\` opérateur lève une <xref:System.DivideByZeroException> exception. Cela est vrai pour tous les types de données numériques des opérandes.  
  
> [!NOTE]
> L' `\` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise l' `\` opérateur pour effectuer une division d’entier. Le résultat est un entier qui représente le quotient entier des deux opérandes, le reste étant ignoré.  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 Dans l’exemple précédent, les expressions retournent respectivement les valeurs 2, 3, 33 et-22.  
  
## <a name="see-also"></a>Voir aussi

- [\\= (Opérateur)](integer-division-assignment-operator.md)
- [/, Opérateur (Visual Basic)](floating-point-division-operator.md)
- [Option Strict Statement](../statements/option-strict-statement.md)
- [Opérateurs arithmétiques](arithmetic-operators.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [Opérateurs arithmétiques en Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
