---
title: <<, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 77bf26d4e6bb068f9130deed5eb1ecbaee62afce
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866788"
---
# <a name="-operator-visual-basic"></a>\<\< (Visual Basic), opérateur

Effectue un décalage arithmétique vers la gauche sur un modèle binaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a>Éléments  

 `result`  
 Obligatoire. Valeur numérique intégrale. Résultat du décalage du modèle binaire. Le type de données est le même que celui de `pattern`.  
  
 `pattern`  
 Obligatoire. Expression numérique entière. Modèle binaire qui doit être décalé. Le type de données doit être un type entier (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` ou `ULong`).  
  
 `amount`  
 Obligatoire. Expression numérique. Nombre de bits pour décaler le modèle binaire. Le type de données doit être `Integer` ou étendu à `Integer`.  
  
## <a name="remarks"></a>Notes  

 Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés d’une extrémité du résultat ne sont pas réintroduits à l’autre extrémité. Dans un décalage arithmétique vers la gauche, les bits décalés au-delà de la plage du type de données de résultat sont ignorés, et les positions de bits libérées à droite sont définies sur zéro.  
  
 Pour empêcher un décalage de plus de bits que le résultat ne peut en contenir, Visual Basic masque la valeur de `amount` avec un masque de taille qui correspond au type de données de `pattern` . Le binaire et de ces valeurs est utilisé pour la valeur de décalage. Les masques de taille sont les suivants :  
  
|Type de données de `pattern`|Masque de taille (décimal)|Masque de taille (hexadécimal)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 Si `amount` est égal à zéro, la valeur de `result` est identique à la valeur de `pattern` . Si `amount` est négatif, il est considéré comme une valeur non signée et masqué avec le masque de taille approprié.  
  
 Les décalages arithmétiques ne génèrent jamais d’exceptions de dépassement de capacité.  
  
> [!NOTE]
> L' `<<` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur ce type de classe ou de structure, assurez-vous que vous comprenez son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise l' `<<` opérateur pour effectuer des décalages arithmétiques vers la gauche sur les valeurs intégrales. Le résultat a toujours le même type de données que celui de l’expression en cours de décalage.  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 Les résultats de l’exemple précédent sont les suivants :  
  
- `result1` est 192 (0000 0000 1100 0000).  
  
- `result2` est 3072 (0000 1100 0000 0000).  
  
- `result3` est-32768 (1000 0000 0000 0000).  
  
- `result4` est 384 (0000 0001 1000 0000).  
  
- `result5` est 0 (décalé de 15 places vers la gauche).  
  
 Le nombre de décalages pour `result4` est calculé comme 17 et 15, ce qui équivaut à 1.  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs de décalage de bits](bit-shift-operators.md)
- [Opérateurs d’assignation](assignment-operators.md)
- [<<=, opérateur](left-shift-assignment-operator.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [Opérateurs arithmétiques en Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
