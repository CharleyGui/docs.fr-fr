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
ms.openlocfilehash: d88c43efe858d6b81b7d8d2470b234ff5d40632a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353838"
---
# <a name="of-clause-visual-basic"></a>Of, clause (Visual Basic)
Introduit une clause `Of`, qui identifie un *paramètre de type* sur une classe, une structure, une interface, un délégué ou une procédure *générique* . Pour plus d’informations sur les types génériques, consultez [types génériques dans Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).  
  
## <a name="using-the-of-keyword"></a>Utilisation du mot clé of  
 L’exemple de code suivant utilise le mot clé `Of` pour définir le plan d’une classe qui accepte deux paramètres de type. Il *limite* le paramètre `keyType` par l’interface <xref:System.IComparable>, ce qui signifie que le code de consommation doit fournir un argument de type qui implémente <xref:System.IComparable>. Cela est nécessaire pour que la procédure `add` puisse appeler la méthode <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType>. Pour plus d’informations sur les contraintes, consultez [Type List](../../../visual-basic/language-reference/statements/type-list.md).  
  
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
  
 Si vous terminez la définition de classe précédente, vous pouvez construire une variété de `dictionary` classes à partir de celle-ci. Les types que vous fournissez à `entryType` et `keyType` déterminent le type d’entrée que contient la classe et le type de clé qu’elle associe à chaque entrée. En raison de la contrainte, vous devez fournir à `keyType` un type qui implémente <xref:System.IComparable>.  
  
 L’exemple de code suivant crée un objet qui contient des entrées `String` et associe une clé `Integer` à chacune d’entre elles. `Integer` implémente <xref:System.IComparable> et, par conséquent, satisfait la contrainte sur `keyType`.  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 Le mot clé `Of` peut être utilisé dans les contextes suivants :  
  
 [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Delegate (instruction)](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface (instruction)](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IComparable>
- [Liste de types](../../../visual-basic/language-reference/statements/type-list.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
