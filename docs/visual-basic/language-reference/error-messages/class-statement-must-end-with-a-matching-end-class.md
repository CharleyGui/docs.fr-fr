---
title: Une instruction 'Class' doit se terminer par une 'End Class' correspondante
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 01c231f577d21028e9ef92f37c7ac5f7f1fe2aa3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415386"
---
# <a name="class-statement-must-end-with-a-matching-end-class"></a><span data-ttu-id="02ebf-102">Une instruction 'Class' doit se terminer par une 'End Class' correspondante</span><span class="sxs-lookup"><span data-stu-id="02ebf-102">'Class' statement must end with a matching 'End Class'</span></span>
<span data-ttu-id="02ebf-103">`Class`est utilisé pour initier un `Class` bloc. il ne peut donc apparaître qu’au début du bloc, avec une instruction correspondante qui `End Class` termine le bloc.</span><span class="sxs-lookup"><span data-stu-id="02ebf-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="02ebf-104">Soit vous avez une instruction redondante `Class` , soit vous n’avez pas terminé votre `Class` bloc avec `End Class` .</span><span class="sxs-lookup"><span data-stu-id="02ebf-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>  
  
 <span data-ttu-id="02ebf-105">**ID d’erreur :** BC30481</span><span class="sxs-lookup"><span data-stu-id="02ebf-105">**Error ID:** BC30481</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="02ebf-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="02ebf-106">To correct this error</span></span>  
  
- <span data-ttu-id="02ebf-107">Recherchez et supprimez l’instruction `Class` inutile.</span><span class="sxs-lookup"><span data-stu-id="02ebf-107">Locate and remove the unnecessary `Class` statement.</span></span>  
  
- <span data-ttu-id="02ebf-108">Conclut le `Class` bloc avec un correspondant `End Class` .</span><span class="sxs-lookup"><span data-stu-id="02ebf-108">Conclude the `Class` block with a matching `End Class`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02ebf-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02ebf-109">See also</span></span>

- [<span data-ttu-id="02ebf-110">End ( \<keyword> instruction)</span><span class="sxs-lookup"><span data-stu-id="02ebf-110">End \<keyword> Statement</span></span>](../statements/end-keyword-statement.md)
- [<span data-ttu-id="02ebf-111">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="02ebf-111">Class Statement</span></span>](../statements/class-statement.md)
