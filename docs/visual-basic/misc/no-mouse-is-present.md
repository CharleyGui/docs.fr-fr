---
title: Absence de souris
ms.date: 07/20/2015
f1_keywords:
- vbrMouse_NoMouseIsPresent
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
ms.openlocfilehash: ceb850d98d29c232da304fbdfaddf5611714ef1a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078851"
---
# <a name="no-mouse-is-present"></a><span data-ttu-id="e47b4-102">Absence de souris</span><span class="sxs-lookup"><span data-stu-id="e47b4-102">No mouse is present</span></span>

<span data-ttu-id="e47b4-103">L’une des propriétés de l’objet `My.Computer.Mouse` a été appelée, mais aucune souris ou aucun port de souris n’est installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e47b4-103">One of the properties of the `My.Computer.Mouse` object was called, but the computer has no mouse or mouse port installed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e47b4-104">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="e47b4-104">To correct this error</span></span>  
  
- <span data-ttu-id="e47b4-105">Ajoutez un bloc `Try...Catch` autour de l’appel à la propriété de l’objet `My.Computer.Mouse` .</span><span class="sxs-lookup"><span data-stu-id="e47b4-105">Add a `Try...Catch` block around the call to the property of the `My.Computer.Mouse` object.</span></span>  
  
     <span data-ttu-id="e47b4-106">— ou —</span><span class="sxs-lookup"><span data-stu-id="e47b4-106">— or —</span></span>  
  
- <span data-ttu-id="e47b4-107">Installez une souris sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e47b4-107">Install a mouse on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e47b4-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e47b4-108">See also</span></span>

- [<span data-ttu-id="e47b4-109">My.Computer.Mouse</span><span class="sxs-lookup"><span data-stu-id="e47b4-109">My.Computer.Mouse</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse)
- [<span data-ttu-id="e47b4-110">Gestion et levée d’exceptions dans .NET</span><span class="sxs-lookup"><span data-stu-id="e47b4-110">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="e47b4-111">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="e47b4-111">Try...Catch...Finally Statement</span></span>](../language-reference/statements/try-catch-finally-statement.md)
