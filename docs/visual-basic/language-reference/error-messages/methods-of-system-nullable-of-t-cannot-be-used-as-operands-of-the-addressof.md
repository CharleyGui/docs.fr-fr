---
title: Les méthodes de 'System.Nullable(Of T)' ne peuvent pas être utilisées en tant qu’opérandes de l’opérateur 'AddressOf'
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 173cf19537e3f9ffc4cff6cef71f34b6d365e5d3
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160390"
---
# <a name="bc32126-methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a>BC32126 : les méthodes de’System. Nullable (Of T) 'ne peuvent pas être utilisées en tant qu’opérandes de l’opérateur’AddressOf'

Une instruction utilise l' `AddressOf` opérateur avec un opérande qui représente une procédure de la <xref:System.Nullable%601> structure.

 **ID d’erreur :** BC32126

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Remplacez le nom de la procédure dans la `AddressOf` clause par un opérande qui n’est pas un membre de <xref:System.Nullable%601> .

- Écrivez une classe qui encapsule la méthode de <xref:System.Nullable%601> que vous souhaitez utiliser. Dans l’exemple suivant, la `NullableWrapper` classe définit une nouvelle méthode nommée `GetValueOrDefault` . Étant donné que cette nouvelle méthode n’est pas membre de <xref:System.Nullable%601> , elle peut être appliquée à `nullInstance` , une instance d’un type Nullable, pour former un argument pour `AddressOf` .

```vb
Module Module1

    Delegate Function Deleg() As Integer

    Sub Main()
        Dim nullInstance As New Nullable(Of Integer)(1)

        Dim del As Deleg

        ' GetValueOrDefault is a method of the Nullable generic
        ' type. It cannot be used as an operand of AddressOf.
        ' del = AddressOf nullInstance.GetValueOrDefault

        ' The following line uses the GetValueOrDefault method
        ' defined in the NullableWrapper class.
        del = AddressOf (New NullableWrapper(
            Of Integer)(nullInstance)).GetValueOrDefault

        Console.WriteLine(del.Invoke())
    End Sub

    Class NullableWrapper(Of T As Structure)
        Private m_Value As Nullable(Of T)

        Sub New(ByVal Value As Nullable(Of T))
            m_Value = Value
        End Sub

        Public Function GetValueOrDefault() As T
            Return m_Value.Value
        End Function
    End Class
End Module
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Nullable%601>
- [AddressOf, opérateur](../operators/addressof-operator.md)
- [Types valeur Nullable](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
