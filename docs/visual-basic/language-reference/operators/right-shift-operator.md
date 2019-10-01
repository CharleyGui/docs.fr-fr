---
title: '>> (Visual Basic), opérateur'
ms.date: 07/20/2015
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
ms.openlocfilehash: 337d651e831dc2ab132056f6e9a1f2b5300bf7f8
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701330"
---
# <a name="-operator-visual-basic"></a>> >, opérateur (Visual Basic)
Effectue un décalage arithmétique vers la droite sur un modèle binaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Obligatoire. Valeur numérique intégrale. Résultat de l’évolution du modèle binaire. Le type de données est le même que celui `pattern`de.  
  
 `pattern`  
 Obligatoire. Expression numérique intégrale. Modèle binaire à décaler. Le type de données doit être un type intégral`SByte`( `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, ou `ULong`).  
  
 `amount`  
 Obligatoire. Expression numérique. Nombre de bits de décalage du modèle binaire. Le type de données doit `Integer` être ou étendu `Integer`à.  
  
## <a name="remarks"></a>Notes  
 Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés d’une extrémité du résultat ne sont pas réintroduits à l’autre extrémité. Dans un décalage arithmétique vers la droite, les bits décalés au-delà de la position du bit le plus à droite sont ignorés, et le bit le plus à gauche (signe) est propagé dans les positions de bits libérées à gauche. Cela signifie que si `pattern` a une valeur négative, les positions libérées sont définies sur un. dans le cas contraire, elles ont la valeur zéro.  
  
 Notez que les types de données `Byte`, `UShort`, `UInteger` et `ULong` ne sont pas signés, ce qui signifie qu’il n’y a aucun bit de signe à propager. Si `pattern` est de type non signé, les positions libérées sont toujours définies sur zéro.  
  
 Pour empêcher le décalage par plus de bits que le résultat ne peut en contenir, Visual Basic masque la valeur de `amount` avec un masque de taille correspondant au type de données de `pattern`. Le binaire et de ces valeurs est utilisé pour la valeur de décalage. Les masques de taille sont les suivants :  
  
|Type de données de `pattern`|Masque de taille (décimal)|Masque de taille (hexadécimal)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 Si `amount` est égal à zéro, la valeur de `result` est identique à la valeur de `pattern`. Si `amount` est négatif, il est considéré comme une valeur non signée et masqué avec le masque de taille approprié.  
  
 Les décalages arithmétiques ne génèrent jamais d’exceptions de dépassement de capacité.  
  
## <a name="overloading"></a>Surcharge  
 L’opérateur `>>` peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’opérateur `>>` pour effectuer des décalages arithmétiques vers la droite sur les valeurs intégrales. Le résultat a toujours le même type de données que celui de l’expression en cours de décalage.  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 Les résultats de l’exemple précédent sont les suivants :  
  
- `result1` est 2560 (0000 1010 0000 0000).  
  
- `result2` est 160 (0000 0000 1010 0000).  
  
- `result3` correspond à 2 (0000 0000 0000 0010).  
  
- `result4` est 640 (0000 0010 1000 0000).  
  
- `result5` correspond à 0 (décalage de 15 places à droite).  
  
 Le nombre de décalages pour `result4` est calculé comme 18 et 15, ce qui équivaut à 2.  
  
 L’exemple suivant montre des décalages arithmétiques sur une valeur négative.  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 Les résultats de l’exemple précédent sont les suivants :  
  
- `negresult1` est-512 (1111 1110 0000 0000).  
  
- `negresult2` est égal à-1 (le bit de signe est propagé).  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs de décalage de bits](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Opérateurs d’assignation](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [>>= (opérateur)](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Opérateurs arithmétiques dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
