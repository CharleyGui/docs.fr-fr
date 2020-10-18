---
title: L’opérande 'IsNot' du type 'NomType' ne peut être comparé qu’à 'Nothing', car 'NomType' est un type nullable
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 084978c1e047eebd60149af63c0ec9a1135225be
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163335"
---
# <a name="bc32128-isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a><span data-ttu-id="abf89-102">BC32128 : l’opérande’IsNot’de type’TypeName’ne peut être comparé qu’à’Nothing', car’TypeName’est un type Nullable</span><span class="sxs-lookup"><span data-stu-id="abf89-102">BC32128: 'IsNot' operand of type 'typename' can only be compared to 'Nothing', because 'typename' is a nullable type</span></span>

<span data-ttu-id="abf89-103">Une variable déclarée en tant que type valeur Nullable a été comparée à une expression autre que l' `Nothing` `IsNot` opérateur.</span><span class="sxs-lookup"><span data-stu-id="abf89-103">A variable declared as a nullable value type has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>

<span data-ttu-id="abf89-104">**ID d’erreur :** BC32128</span><span class="sxs-lookup"><span data-stu-id="abf89-104">**Error ID:** BC32128</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="abf89-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="abf89-105">To correct this error</span></span>

<span data-ttu-id="abf89-106">Pour comparer un type nullable à une expression autre que `Nothing` à l’aide de l’opérateur `IsNot` , appelez la méthode `GetType` sur le type nullable et comparez le résultat à l’expression, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="abf89-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a><span data-ttu-id="abf89-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="abf89-107">See also</span></span>

- [<span data-ttu-id="abf89-108">Types valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="abf89-108">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="abf89-109">IsNot, opérateur</span><span class="sxs-lookup"><span data-stu-id="abf89-109">IsNot Operator</span></span>](../operators/isnot-operator.md)
