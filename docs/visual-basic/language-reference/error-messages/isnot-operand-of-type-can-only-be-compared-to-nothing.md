---
title: L’opérande 'IsNot' du type 'NomType' ne peut être comparé qu’à 'Nothing', car 'NomType' est un type nullable
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: fb61b04021bd844fade94413b4f3b28b82f6411b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402796"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a><span data-ttu-id="cab73-102">L’opérande 'IsNot' du type 'NomType' ne peut être comparé qu’à 'Nothing', car 'NomType' est un type nullable</span><span class="sxs-lookup"><span data-stu-id="cab73-102">'IsNot' operand of type 'typename' can only be compared to 'Nothing', because 'typename' is a nullable type</span></span>

<span data-ttu-id="cab73-103">Une variable déclarée en tant que type valeur Nullable a été comparée à une expression autre que l' `Nothing` `IsNot` opérateur.</span><span class="sxs-lookup"><span data-stu-id="cab73-103">A variable declared as a nullable value type has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>

<span data-ttu-id="cab73-104">**ID d’erreur :** BC32128</span><span class="sxs-lookup"><span data-stu-id="cab73-104">**Error ID:** BC32128</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="cab73-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="cab73-105">To correct this error</span></span>

<span data-ttu-id="cab73-106">Pour comparer un type nullable à une expression autre que `Nothing` à l’aide de l’opérateur `IsNot` , appelez la méthode `GetType` sur le type nullable et comparez le résultat à l’expression, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="cab73-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a><span data-ttu-id="cab73-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cab73-107">See also</span></span>

- [<span data-ttu-id="cab73-108">Types valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="cab73-108">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="cab73-109">IsNot, opérateur</span><span class="sxs-lookup"><span data-stu-id="cab73-109">IsNot Operator</span></span>](../operators/isnot-operator.md)
