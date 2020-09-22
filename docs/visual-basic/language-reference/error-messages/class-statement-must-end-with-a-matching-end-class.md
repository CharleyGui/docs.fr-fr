---
title: Une instruction 'Class' doit se terminer par une 'End Class' correspondante
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: d67f0e71dbdbf97420ec5b5ba4b6f06acfba1bd9
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874616"
---
# <a name="class-statement-must-end-with-a-matching-end-class"></a><span data-ttu-id="ca561-102">Une instruction 'Class' doit se terminer par une 'End Class' correspondante</span><span class="sxs-lookup"><span data-stu-id="ca561-102">'Class' statement must end with a matching 'End Class'</span></span>

<span data-ttu-id="ca561-103">`Class` est utilisé pour initier un `Class` bloc. il ne peut donc apparaître qu’au début du bloc, avec une instruction correspondante qui `End Class` termine le bloc.</span><span class="sxs-lookup"><span data-stu-id="ca561-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="ca561-104">Soit vous avez une instruction redondante `Class` , soit vous n’avez pas terminé votre `Class` bloc avec `End Class` .</span><span class="sxs-lookup"><span data-stu-id="ca561-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>  
  
 <span data-ttu-id="ca561-105">**ID d’erreur :** BC30481</span><span class="sxs-lookup"><span data-stu-id="ca561-105">**Error ID:** BC30481</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ca561-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ca561-106">To correct this error</span></span>  
  
- <span data-ttu-id="ca561-107">Recherchez et supprimez l’instruction `Class` inutile.</span><span class="sxs-lookup"><span data-stu-id="ca561-107">Locate and remove the unnecessary `Class` statement.</span></span>  
  
- <span data-ttu-id="ca561-108">Conclut le `Class` bloc avec un correspondant `End Class` .</span><span class="sxs-lookup"><span data-stu-id="ca561-108">Conclude the `Class` block with a matching `End Class`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca561-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca561-109">See also</span></span>

- [<span data-ttu-id="ca561-110">End ( \<keyword> instruction)</span><span class="sxs-lookup"><span data-stu-id="ca561-110">End \<keyword> Statement</span></span>](../statements/end-keyword-statement.md)
- [<span data-ttu-id="ca561-111">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="ca561-111">Class Statement</span></span>](../statements/class-statement.md)
