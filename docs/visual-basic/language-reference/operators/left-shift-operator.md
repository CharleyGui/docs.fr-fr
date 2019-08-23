---
title: < <, opérateur (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: d6b186ad519bcd7cf82cce12523f2d75e09317cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966888"
---
# <a name="-operator-visual-basic"></a>\<\<(Visual Basic), opérateur
Effectue un décalage arithmétique vers la gauche sur un modèle binaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Requis. Valeur numérique intégrale. Résultat de l’évolution du modèle binaire. Le type de données est le même que celui `pattern`de.  
  
 `pattern`  
 Requis. Expression numérique intégrale. Modèle binaire à décaler. Le type de données doit être un type intégral`SByte`( `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, ou `ULong`).  
  
 `amount`  
 Requis. Expression numérique. Nombre de bits de décalage du modèle binaire. Le type de données doit `Integer` être ou étendu `Integer`à.  
  
## <a name="remarks"></a>Notes  
 Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés d’une extrémité du résultat ne sont pas réintroduits à l’autre extrémité. Dans un décalage arithmétique vers la gauche, les bits décalés au-delà de la plage du type de données de résultat sont ignorés, et les positions de bits libérées à droite sont définies sur zéro.  
  
 Pour empêcher un décalage de plus de bits que le résultat ne peut en contenir, Visual Basic masque `amount` la valeur de avec un masque de taille qui correspond au `pattern`type de données de. Le binaire et de ces valeurs est utilisé pour la valeur de décalage. Les masques de taille sont les suivants:  
  
|Type de données de`pattern`|Masque de taille (décimal)|Masque de taille (hexadécimal)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 Si `amount` est égal à zéro, la `result` valeur de est identique à la `pattern`valeur de. Si `amount` est négatif, il est considéré comme une valeur non signée et masqué avec le masque de taille approprié.  
  
 Les décalages arithmétiques ne génèrent jamais d’exceptions de dépassement de capacité.  
  
> [!NOTE]
> L' `<<` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur ce type de classe ou de structure, assurez-vous que vous comprenez son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `<<` opérateur pour effectuer des décalages arithmétiques vers la gauche sur les valeurs intégrales. Le résultat a toujours le même type de données que celui de l’expression en cours de décalage.  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 Les résultats de l’exemple précédent sont les suivants:  
  
- `result1`est 192 (0000 0000 1100 0000).  
  
- `result2`est 3072 (0000 1100 0000 0000).  
  
- `result3`est-32768 (1000 0000 0000 0000).  
  
- `result4`est 384 (0000 0001 1000 0000).  
  
- `result5`est 0 (décalé de 15 places vers la gauche).  
  
 Le nombre de décalages pour `result4` est calculé comme 17 et 15, ce qui équivaut à 1.  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs de décalage de bits](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Opérateurs d’assignation](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<<= (opérateur)](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Opérateurs arithmétiques dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
