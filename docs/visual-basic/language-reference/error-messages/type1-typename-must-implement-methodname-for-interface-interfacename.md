---
title: <type1><typename> doit implémenter <methodname> pour l’interface <interfacename>
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 68c6f65e6be229cc74458fa56fe3d3aa889c18f7
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161866"
---
# <a name="bc30149-type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="eca6e-102">BC30149 : \<type1> ' \<typename> 'doit implémenter' \<methodname> 'pour l’interface' \<interfacename> '</span><span class="sxs-lookup"><span data-stu-id="eca6e-102">BC30149: \<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>

<span data-ttu-id="eca6e-103">Une classe ou une structure prétend implémenter une interface, mais n’implémente pas une procédure définie par l’interface.</span><span class="sxs-lookup"><span data-stu-id="eca6e-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="eca6e-104">Chaque membre de l’interface doit être implémenté.</span><span class="sxs-lookup"><span data-stu-id="eca6e-104">Every member of the interface must be implemented.</span></span>

 <span data-ttu-id="eca6e-105">**ID d’erreur :** BC30149</span><span class="sxs-lookup"><span data-stu-id="eca6e-105">**Error ID:** BC30149</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="eca6e-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="eca6e-106">To correct this error</span></span>

1. <span data-ttu-id="eca6e-107">Déclarez une procédure avec les mêmes nom et signature que ceux définis dans l’interface.</span><span class="sxs-lookup"><span data-stu-id="eca6e-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="eca6e-108">Veillez à inclure au moins l' `End Function` `End Sub` instruction ou.</span><span class="sxs-lookup"><span data-stu-id="eca6e-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>

2. <span data-ttu-id="eca6e-109">Ajoutez une `Implements` clause à la fin de l' `Function` `Sub` instruction ou.</span><span class="sxs-lookup"><span data-stu-id="eca6e-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="eca6e-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="eca6e-110">For example:</span></span>

    ```vb
    Public Sub DoSomething() Implements IBaseInterface.DoSomething
    ```

## <a name="see-also"></a><span data-ttu-id="eca6e-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eca6e-111">See also</span></span>

- [<span data-ttu-id="eca6e-112">Implements, instruction</span><span class="sxs-lookup"><span data-stu-id="eca6e-112">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="eca6e-113">Interfaces</span><span class="sxs-lookup"><span data-stu-id="eca6e-113">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
