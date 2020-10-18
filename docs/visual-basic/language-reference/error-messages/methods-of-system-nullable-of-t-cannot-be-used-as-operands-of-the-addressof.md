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
# <a name="bc32126-methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a><span data-ttu-id="e55d9-102">BC32126 : les méthodes de’System. Nullable (Of T) 'ne peuvent pas être utilisées en tant qu’opérandes de l’opérateur’AddressOf'</span><span class="sxs-lookup"><span data-stu-id="e55d9-102">BC32126: Methods of 'System.Nullable(Of T)' cannot be used as operands of the 'AddressOf' operator</span></span>

<span data-ttu-id="e55d9-103">Une instruction utilise l' `AddressOf` opérateur avec un opérande qui représente une procédure de la <xref:System.Nullable%601> structure.</span><span class="sxs-lookup"><span data-stu-id="e55d9-103">A statement uses the `AddressOf` operator with an operand that represents a procedure of the <xref:System.Nullable%601> structure.</span></span>

 <span data-ttu-id="e55d9-104">**ID d’erreur :** BC32126</span><span class="sxs-lookup"><span data-stu-id="e55d9-104">**Error ID:** BC32126</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e55d9-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="e55d9-105">To correct this error</span></span>

- <span data-ttu-id="e55d9-106">Remplacez le nom de la procédure dans la `AddressOf` clause par un opérande qui n’est pas un membre de <xref:System.Nullable%601> .</span><span class="sxs-lookup"><span data-stu-id="e55d9-106">Replace the procedure name in the `AddressOf` clause with an operand that is not a member of <xref:System.Nullable%601>.</span></span>

- <span data-ttu-id="e55d9-107">Écrivez une classe qui encapsule la méthode de <xref:System.Nullable%601> que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="e55d9-107">Write a class that wraps the method of <xref:System.Nullable%601> that you want to use.</span></span> <span data-ttu-id="e55d9-108">Dans l’exemple suivant, la `NullableWrapper` classe définit une nouvelle méthode nommée `GetValueOrDefault` .</span><span class="sxs-lookup"><span data-stu-id="e55d9-108">In the following example, the `NullableWrapper` class defines a new method named `GetValueOrDefault`.</span></span> <span data-ttu-id="e55d9-109">Étant donné que cette nouvelle méthode n’est pas membre de <xref:System.Nullable%601> , elle peut être appliquée à `nullInstance` , une instance d’un type Nullable, pour former un argument pour `AddressOf` .</span><span class="sxs-lookup"><span data-stu-id="e55d9-109">Because this new method is not a member of <xref:System.Nullable%601>, it can be applied to `nullInstance`, an instance of a nullable type, to form an argument for `AddressOf`.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e55d9-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e55d9-110">See also</span></span>

- <xref:System.Nullable%601>
- [<span data-ttu-id="e55d9-111">AddressOf, opérateur</span><span class="sxs-lookup"><span data-stu-id="e55d9-111">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="e55d9-112">Types valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="e55d9-112">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="e55d9-113">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e55d9-113">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
