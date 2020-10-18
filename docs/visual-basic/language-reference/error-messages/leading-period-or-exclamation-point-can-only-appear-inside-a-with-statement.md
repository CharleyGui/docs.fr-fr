---
title: Un caractère '.' ou '!' de début ne peut apparaître que dans une instruction 'With'
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 4ff273d5930fe58a5bccf0f4f4c10e971d777d01
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162503"
---
# <a name="bc30157-leading--or--can-only-appear-inside-a-with-statement"></a><span data-ttu-id="7736d-102">BC30157 : '. 'ou' ! 'de début ne peut apparaître qu’à l’intérieur d’une instruction’with'</span><span class="sxs-lookup"><span data-stu-id="7736d-102">BC30157: Leading '.' or '!' can only appear inside a 'With' statement</span></span>

<span data-ttu-id="7736d-103">Un point (.) ou un point d’exclamation ( !) qui ne se trouve pas à l’intérieur d’un `With` bloc se produit sans une expression à gauche.</span><span class="sxs-lookup"><span data-stu-id="7736d-103">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="7736d-104">L’accès au membre ( `.` ) et l’accès au membre de dictionnaire ( `!` ) requièrent une expression spécifiant l’élément qui contient le membre.</span><span class="sxs-lookup"><span data-stu-id="7736d-104">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="7736d-105">Il doit apparaître immédiatement à gauche de l’accesseur ou en tant que cible d’un `With` bloc contenant l’accès au membre.</span><span class="sxs-lookup"><span data-stu-id="7736d-105">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>

 <span data-ttu-id="7736d-106">**ID d’erreur :** BC30157</span><span class="sxs-lookup"><span data-stu-id="7736d-106">**Error ID:** BC30157</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="7736d-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="7736d-107">To correct this error</span></span>

1. <span data-ttu-id="7736d-108">Assurez-vous que le `With` bloc est correctement mis en forme.</span><span class="sxs-lookup"><span data-stu-id="7736d-108">Ensure that the `With` block is correctly formatted.</span></span>

2. <span data-ttu-id="7736d-109">S’il n’y a aucun `With` bloc, ajoutez une expression à gauche de l’accesseur qui prend la valeur d’un élément défini contenant le membre.</span><span class="sxs-lookup"><span data-stu-id="7736d-109">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>

## <a name="see-also"></a><span data-ttu-id="7736d-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7736d-110">See also</span></span>

- [<span data-ttu-id="7736d-111">Caractères spéciaux dans le code</span><span class="sxs-lookup"><span data-stu-id="7736d-111">Special Characters in Code</span></span>](../../programming-guide/program-structure/special-characters-in-code.md)
- [<span data-ttu-id="7736d-112">With...End With (instruction)</span><span class="sxs-lookup"><span data-stu-id="7736d-112">With...End With Statement</span></span>](../statements/with-end-with-statement.md)
