---
title: '- Opérateur'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: 6539beb5cf8078281357445e2391fac189208087
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406351"
---
# <a name="--operator-visual-basic"></a>-, opérateur (Visual Basic)
Retourne la différence entre deux expressions numériques ou la valeur négative d’une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
expression1 – expression2
```
  
ou

```vb  
–expression1  
```  
  
## <a name="parts"></a>Éléments  
 `expression1`  
 Obligatoire. Toute expression numérique.  
  
 `expression2`  
 Obligatoire, sauf si l' `–` opérateur calcule une valeur négative. Toute expression numérique.  
  
## <a name="result"></a>Résultats  
 Le résultat est la différence entre `expression1` et `expression2` , ou la valeur négative de `expression1` .  
  
 Le type de données de résultat est un type numérique approprié pour les types de données de `expression1` et `expression2` . Consultez les tables « arithmétiques sur les entiers » dans [types de données des résultats d’opérateur](data-types-of-operator-results.md).  
  
## <a name="supported-types"></a>Types pris en charge  
 tous les types numériques Cela comprend les types à virgule flottante non signée et `Decimal` .  
  
## <a name="remarks"></a>Notes  
 Dans la première utilisation indiquée dans la syntaxe indiquée précédemment, l' `–` opérateur est l’opérateur de soustraction arithmétique *binaire* pour la différence entre deux expressions numériques.  
  
 Dans la deuxième utilisation indiquée dans la syntaxe indiquée précédemment, l' `–` opérateur est l’opérateur de négation *unaire* pour la valeur négative d’une expression. Dans ce sens, la négation consiste à inverser le signe de `expression1` afin que le résultat soit positif si `expression1` est négatif.  
  
 Si l’une des expressions a la valeur [Nothing](../nothing.md), l' `–` opérateur la traite comme zéro.  
  
> [!NOTE]
> L' `–` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur ce type de classe ou de structure, assurez-vous que vous comprenez son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `–` opérateur pour calculer et retourner la différence entre deux nombres, puis pour nier un nombre.  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 Après l’exécution de ces instructions, `binaryResult` contient 124,45 et `unaryResult` contient – 334,90.  
  
## <a name="see-also"></a>Voir aussi

- [-=, Opérateur (Visual Basic)](subtraction-assignment-operator.md)
- [Opérateurs arithmétiques](arithmetic-operators.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [Opérateurs arithmétiques en Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
