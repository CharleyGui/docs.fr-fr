---
title: Les expressions lambda ne sont pas valides dans la première expression d’une instruction ’Select Case’
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: 9f200ea44e7505c407c7df56e596435024394875
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873871"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a><span data-ttu-id="3f318-102">Les expressions lambda ne sont pas valides dans la première expression d’une instruction ’Select Case’</span><span class="sxs-lookup"><span data-stu-id="3f318-102">Lambda expressions are not valid in the first expression of a 'Select Case' statement</span></span>

<span data-ttu-id="3f318-103">Vous ne pouvez pas utiliser une expression lambda pour l’expression de test dans une `Select Case` instruction.</span><span class="sxs-lookup"><span data-stu-id="3f318-103">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="3f318-104">Les définitions d’expression lambda retournent des fonctions, et l’expression de test d’une `Select Case` instruction doit être un type de données élémentaire.</span><span class="sxs-lookup"><span data-stu-id="3f318-104">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>  
  
 <span data-ttu-id="3f318-105">Le code suivant génère cette erreur :</span><span class="sxs-lookup"><span data-stu-id="3f318-105">The following code causes this error:</span></span>  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 <span data-ttu-id="3f318-106">**ID d’erreur :** BC36635</span><span class="sxs-lookup"><span data-stu-id="3f318-106">**Error ID:** BC36635</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3f318-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="3f318-107">To correct this error</span></span>  
  
- <span data-ttu-id="3f318-108">Examinez votre code pour déterminer si une construction conditionnelle différente, comme une instruction `If...Then...Else` , répond à vos besoins.</span><span class="sxs-lookup"><span data-stu-id="3f318-108">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>  
  
- <span data-ttu-id="3f318-109">Vous avez peut-être prévu d’appeler la fonction, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="3f318-109">You may have intended to call the function, as shown in the following code:</span></span>  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f318-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f318-110">See also</span></span>

- [<span data-ttu-id="3f318-111">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="3f318-111">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="3f318-112">If...Then...Else (instruction)</span><span class="sxs-lookup"><span data-stu-id="3f318-112">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="3f318-113">Select...Case (instruction)</span><span class="sxs-lookup"><span data-stu-id="3f318-113">Select...Case Statement</span></span>](../statements/select-case-statement.md)
