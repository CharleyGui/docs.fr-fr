---
title: Une instruction 'Class' doit se terminer par une 'End Class' correspondante
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 6889e97aad913f6911ce438892752542de0d10f0
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163192"
---
# <a name="bc30481-class-statement-must-end-with-a-matching-end-class"></a><span data-ttu-id="80fef-102">BC30481 : l’instruction’class’doit se terminer par un’End Class’correspondant</span><span class="sxs-lookup"><span data-stu-id="80fef-102">BC30481: 'Class' statement must end with a matching 'End Class'</span></span>

<span data-ttu-id="80fef-103">`Class` est utilisé pour initier un `Class` bloc. il ne peut donc apparaître qu’au début du bloc, avec une instruction correspondante qui `End Class` termine le bloc.</span><span class="sxs-lookup"><span data-stu-id="80fef-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="80fef-104">Soit vous avez une instruction redondante `Class` , soit vous n’avez pas terminé votre `Class` bloc avec `End Class` .</span><span class="sxs-lookup"><span data-stu-id="80fef-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>

 <span data-ttu-id="80fef-105">**ID d’erreur :** BC30481</span><span class="sxs-lookup"><span data-stu-id="80fef-105">**Error ID:** BC30481</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="80fef-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="80fef-106">To correct this error</span></span>

- <span data-ttu-id="80fef-107">Recherchez et supprimez l’instruction `Class` inutile.</span><span class="sxs-lookup"><span data-stu-id="80fef-107">Locate and remove the unnecessary `Class` statement.</span></span>

- <span data-ttu-id="80fef-108">Conclut le `Class` bloc avec un correspondant `End Class` .</span><span class="sxs-lookup"><span data-stu-id="80fef-108">Conclude the `Class` block with a matching `End Class`.</span></span>

## <a name="see-also"></a><span data-ttu-id="80fef-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80fef-109">See also</span></span>

- [<span data-ttu-id="80fef-110">End ( \<keyword> instruction)</span><span class="sxs-lookup"><span data-stu-id="80fef-110">End \<keyword> Statement</span></span>](../statements/end-keyword-statement.md)
- [<span data-ttu-id="80fef-111">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="80fef-111">Class Statement</span></span>](../statements/class-statement.md)
