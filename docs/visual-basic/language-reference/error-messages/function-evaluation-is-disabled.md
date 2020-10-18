---
title: L'évaluation de la fonction est désactivée, car une évaluation de fonction précédente a expiré
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: 6367553df38a7ccf3b4afbeec877f88fc3d3a1da
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160683"
---
# <a name="bc30957-function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="9fbc8-102">BC30957 : l’évaluation de fonction est désactivée, car une évaluation de fonction précédente a expiré</span><span class="sxs-lookup"><span data-stu-id="9fbc8-102">BC30957: Function evaluation is disabled because a previous function evaluation timed out</span></span>

<span data-ttu-id="9fbc8-103">L’évaluation de fonction est désactivée, car une évaluation de fonction précédente a expiré. Pour réactiver l’évaluation de fonction, recommencez l’opération ou redémarrez le débogage.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-103">Function evaluation is disabled because a previous function evaluation timed out. To re-enable function evaluation, step again or restart debugging.</span></span>

 <span data-ttu-id="9fbc8-104">Dans le débogueur Visual Studio, une expression spécifie un appel de procédure, mais une autre évaluation a dépassé le délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-104">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>

 <span data-ttu-id="9fbc8-105">Les causes possibles de l’expiration d’un appel de procédure incluent une boucle infinie ou une *boucle*infinie.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-105">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="9fbc8-106">Pour plus d’informations, consultez [pour... Instruction suivante](../statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9fbc8-106">For more information, see [For...Next Statement](../statements/for-next-statement.md).</span></span>

 <span data-ttu-id="9fbc8-107">La *récursivité*est un cas particulier de boucle infinie.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-107">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="9fbc8-108">Pour plus d’informations, consultez [procédures récursives](../../programming-guide/language-features/procedures/recursive-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9fbc8-108">For more information, see [Recursive Procedures](../../programming-guide/language-features/procedures/recursive-procedures.md).</span></span>

 <span data-ttu-id="9fbc8-109">**ID d’erreur :** BC30957</span><span class="sxs-lookup"><span data-stu-id="9fbc8-109">**Error ID:** BC30957</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="9fbc8-110">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="9fbc8-110">To correct this error</span></span>

1. <span data-ttu-id="9fbc8-111">Si possible, déterminez l’évaluation de la fonction précédente et la raison de l’expiration du délai d’attente. Dans le cas contraire, vous risquez de rencontrer cette erreur.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-111">If possible, determine what the previous function evaluation was and what caused it to time out. Otherwise, you might encounter this error again.</span></span>

2. <span data-ttu-id="9fbc8-112">Effectuez une nouvelle opération sur le débogueur, ou arrêtez et redémarrez le débogage.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-112">Either step the debugger again, or terminate and restart debugging.</span></span>

## <a name="see-also"></a><span data-ttu-id="9fbc8-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9fbc8-113">See also</span></span>

- [<span data-ttu-id="9fbc8-114">Débogage dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9fbc8-114">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="9fbc8-115">Naviguer dans le code avec le débogueur</span><span class="sxs-lookup"><span data-stu-id="9fbc8-115">Navigating through Code with the Debugger</span></span>](/visualstudio/debugger/navigating-through-code-with-the-debugger)
