---
title: Une instruction 'Class' doit se terminer par une 'End Class' correspondante
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 559595e9902ec2f0a19fd6b13e2c89fa1c2b52d7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602414"
---
# <a name="class-statement-must-end-with-a-matching-end-class"></a><span data-ttu-id="a35c5-102">Une instruction 'Class' doit se terminer par une 'End Class' correspondante</span><span class="sxs-lookup"><span data-stu-id="a35c5-102">'Class' statement must end with a matching 'End Class'</span></span>
<span data-ttu-id="a35c5-103">`Class` permet de lancer un `Class` bloquer ; il ne peut donc apparaître au début du bloc, avec une mise en correspondance `End Class` instruction fin du bloc.</span><span class="sxs-lookup"><span data-stu-id="a35c5-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="a35c5-104">Soit vous avez un redondant `Class` instruction, ou vous n’avez pas terminé votre `Class` bloc avec `End Class`.</span><span class="sxs-lookup"><span data-stu-id="a35c5-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>  
  
 <span data-ttu-id="a35c5-105">**ID d’erreur :** BC30481</span><span class="sxs-lookup"><span data-stu-id="a35c5-105">**Error ID:** BC30481</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a35c5-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="a35c5-106">To correct this error</span></span>  
  
- <span data-ttu-id="a35c5-107">Recherchez et supprimez l’instruction `Class` inutile.</span><span class="sxs-lookup"><span data-stu-id="a35c5-107">Locate and remove the unnecessary `Class` statement.</span></span>  
  
- <span data-ttu-id="a35c5-108">Conclure le `Class` bloc avec une mise en correspondance `End Class`.</span><span class="sxs-lookup"><span data-stu-id="a35c5-108">Conclude the `Class` block with a matching `End Class`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a35c5-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a35c5-109">See also</span></span>

- [<span data-ttu-id="a35c5-110">Fin \<mot clé > instruction</span><span class="sxs-lookup"><span data-stu-id="a35c5-110">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
- [<span data-ttu-id="a35c5-111">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="a35c5-111">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
