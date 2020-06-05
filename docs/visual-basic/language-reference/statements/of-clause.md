---
title: Of (clause)
ms.date: 07/20/2015
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
ms.openlocfilehash: 8497f46453d586fb94e1f7c82c81c6b923dd6f60
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404419"
---
# <a name="of-clause-visual-basic"></a>Of, clause (Visual Basic)
Introduit une `Of` clause qui identifie un *paramètre de type* sur une classe, une structure, une interface, un délégué ou une procédure *générique* . Pour plus d’informations sur les types génériques, consultez [types génériques dans Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).  
  
## <a name="using-the-of-keyword"></a>Utilisation du mot clé of  
 L’exemple de code suivant utilise le `Of` mot clé pour définir le plan d’une classe qui accepte deux paramètres de type. Il *limite* le `keyType` paramètre par l' <xref:System.IComparable> interface, ce qui signifie que le code de consommation doit fournir un argument de type qui implémente <xref:System.IComparable> . Cela est nécessaire pour que la `add` procédure puisse appeler la <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> méthode. Pour plus d’informations sur les contraintes, consultez [Type List](type-list.md).  
  
```vb  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 Si vous terminez la définition de classe précédente, vous pouvez construire diverses `dictionary` classes à partir de celle-ci. Les types que vous fournissez à `entryType` et `keyType` déterminent le type d’entrée que contient la classe et le type de clé qu’elle associe à chaque entrée. En raison de la contrainte, vous devez fournir à `keyType` un type qui implémente <xref:System.IComparable> .  
  
 L’exemple de code suivant crée un objet qui contient des `String` entrées et associe une `Integer` clé à chacune d’entre elles. `Integer`implémente <xref:System.IComparable> et, par conséquent, satisfait la contrainte sur `keyType` .  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 Le mot clé `Of` peut être utilisé dans les contextes suivants :  
  
 [Class (instruction)](class-statement.md)  
  
 [Delegate, instruction](delegate-statement.md)  
  
 [Function (instruction)](function-statement.md)  
  
 [Interface (instruction)](interface-statement.md)  
  
 [Structure, instruction](structure-statement.md)  
  
 [Sub (instruction)](sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IComparable>
- [Type List](type-list.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Dans](../modifiers/in-generic-modifier.md)
- [À](../modifiers/out-generic-modifier.md)
