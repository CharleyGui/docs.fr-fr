---
title: "'#ElseIf' doit être précédé d'un '#If' ou '#ElseIf' correspondant"
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 142c142afe0d9be0ecd4d8a0340f0f1957b20470
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162776"
---
# <a name="bc30014-elseif-must-be-preceded-by-a-matching-if-or-elseif"></a><span data-ttu-id="4ee76-102">BC30014 : ' #ElseIf’doit être précédé d’un' #If’ou' #ElseIf’correspondant</span><span class="sxs-lookup"><span data-stu-id="4ee76-102">BC30014: '#ElseIf' must be preceded by a matching '#If' or '#ElseIf'</span></span>

<span data-ttu-id="4ee76-103">`#ElseIf` est une directive de compilation conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="4ee76-103">`#ElseIf` is a conditional compilation directive.</span></span> <span data-ttu-id="4ee76-104">Une `#ElseIf` clause doit être précédée d’une `#If` clause ou correspondante `#ElseIf` .</span><span class="sxs-lookup"><span data-stu-id="4ee76-104">An `#ElseIf` clause must be preceded by a matching `#If` or `#ElseIf` clause.</span></span>

 <span data-ttu-id="4ee76-105">**ID d’erreur :** BC30014</span><span class="sxs-lookup"><span data-stu-id="4ee76-105">**Error ID:** BC30014</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="4ee76-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="4ee76-106">To correct this error</span></span>

1. <span data-ttu-id="4ee76-107">Vérifiez que le précédent `#If` ou `#ElseIf` le n’a pas été séparé de ce `#ElseIf` par un bloc de compilation conditionnelle intermédiaire ou qu’il a été placé de manière incorrecte `#End If` .</span><span class="sxs-lookup"><span data-stu-id="4ee76-107">Check that a preceding `#If` or `#ElseIf` has not been separated from this `#ElseIf` by an intervening conditional compilation block or an incorrectly placed `#End If`.</span></span>

2. <span data-ttu-id="4ee76-108">Si le `#ElseIf` est précédé d’une `#Else` directive, supprimez `#Else` ou remplacez-le par un `#ElseIf` .</span><span class="sxs-lookup"><span data-stu-id="4ee76-108">If the `#ElseIf` is preceded by a `#Else` directive, either remove the `#Else` or change it to an `#ElseIf`.</span></span>

3. <span data-ttu-id="4ee76-109">Si tout le reste est en ordre, ajoutez une directive `#If` au début du bloc de compilation conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="4ee76-109">If everything else is in order, add an `#If` directive to the beginning of the conditional compilation block.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ee76-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ee76-110">See also</span></span>

- [<span data-ttu-id="4ee76-111">#If... Then... #Else directives</span><span class="sxs-lookup"><span data-stu-id="4ee76-111">#If...Then...#Else Directives</span></span>](../directives/if-then-else-directives.md)
