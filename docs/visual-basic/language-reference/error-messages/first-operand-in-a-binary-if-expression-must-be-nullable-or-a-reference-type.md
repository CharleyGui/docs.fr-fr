---
title: Le premier opérande d'une expression binaire 'If' doit être de type nullable ou référence
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: bca9b74a68815b4e5a3bb2dc114b9031cdf24099
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162737"
---
# <a name="bc33107-first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a><span data-ttu-id="0dacd-102">BC33107 : le premier opérande d’une expression binaire’If’doit être Nullable ou un type référence</span><span class="sxs-lookup"><span data-stu-id="0dacd-102">BC33107: First operand in a binary 'If' expression must be nullable or a reference type</span></span>

<span data-ttu-id="0dacd-103">Une `If` expression peut accepter deux ou trois arguments.</span><span class="sxs-lookup"><span data-stu-id="0dacd-103">An `If` expression can take either two or three arguments.</span></span> <span data-ttu-id="0dacd-104">Lorsque vous envoyez uniquement deux arguments, le premier argument doit être un type référence ou un type valeur Nullable.</span><span class="sxs-lookup"><span data-stu-id="0dacd-104">When you send only two arguments, the first argument must be a reference type or a nullable value type.</span></span> <span data-ttu-id="0dacd-105">Si le premier argument est évalué à une valeur autre que `Nothing` , sa valeur est retournée.</span><span class="sxs-lookup"><span data-stu-id="0dacd-105">If the first argument evaluates to anything other than `Nothing`, its value is returned.</span></span> <span data-ttu-id="0dacd-106">Si le premier argument a la valeur `Nothing` , le deuxième argument est évalué et retourné.</span><span class="sxs-lookup"><span data-stu-id="0dacd-106">If the first argument evaluates to `Nothing`, the second argument is evaluated and returned.</span></span>

 <span data-ttu-id="0dacd-107">Par exemple, le code suivant contient deux `If` expressions, une avec trois arguments et une avec deux arguments.</span><span class="sxs-lookup"><span data-stu-id="0dacd-107">For example, the following code contains two `If` expressions, one with three arguments and one with two arguments.</span></span> <span data-ttu-id="0dacd-108">Les expressions calculent et retournent la même valeur.</span><span class="sxs-lookup"><span data-stu-id="0dacd-108">The expressions calculate and return the same value.</span></span>

```vb
' firstChoice is a nullable value type.
Dim firstChoice? As Integer = Nothing
Dim secondChoice As Integer = 1128
' If expression with three arguments.
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))
' If expression with two arguments.
Console.WriteLine(If(firstChoice, secondChoice))
```

 <span data-ttu-id="0dacd-109">Les expressions suivantes provoquent cette erreur :</span><span class="sxs-lookup"><span data-stu-id="0dacd-109">The following expressions cause this error:</span></span>

```vb
Dim choice1 = 4
Dim choice2 = 5
Dim booleanVar = True

' Not valid.
'Console.WriteLine(If(choice1 < choice2, 1))
' Not valid.
'Console.WriteLine(If(booleanVar, "Test returns True."))
```

 <span data-ttu-id="0dacd-110">**ID d’erreur :** BC33107</span><span class="sxs-lookup"><span data-stu-id="0dacd-110">**Error ID:** BC33107</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="0dacd-111">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="0dacd-111">To correct this error</span></span>

- <span data-ttu-id="0dacd-112">Si vous ne pouvez pas modifier le code afin que le premier argument soit un type valeur Nullable ou un type référence, envisagez d’effectuer la conversion en une expression à trois arguments `If` ou en une `If...Then...Else` instruction.</span><span class="sxs-lookup"><span data-stu-id="0dacd-112">If you cannot change the code so that the first argument is a nullable value type or reference type, consider converting to a three-argument `If` expression, or to an `If...Then...Else` statement.</span></span>

```vb
Console.WriteLine(If(choice1 < choice2, 1, 2))
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))
```

## <a name="see-also"></a><span data-ttu-id="0dacd-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0dacd-113">See also</span></span>

- [<span data-ttu-id="0dacd-114">If, opérateur</span><span class="sxs-lookup"><span data-stu-id="0dacd-114">If Operator</span></span>](../operators/if-operator.md)
- [<span data-ttu-id="0dacd-115">If...Then...Else (instruction)</span><span class="sxs-lookup"><span data-stu-id="0dacd-115">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="0dacd-116">Types valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="0dacd-116">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
