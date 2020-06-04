---
title: Absence de souris
ms.date: 07/20/2015
f1_keywords:
- vbrMouse_NoMouseIsPresent
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
ms.openlocfilehash: 748661cae35292968aae989789a96d1df855b6ce
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84376119"
---
# <a name="no-mouse-is-present"></a><span data-ttu-id="dae49-102">Absence de souris</span><span class="sxs-lookup"><span data-stu-id="dae49-102">No mouse is present</span></span>
<span data-ttu-id="dae49-103">L’une des propriétés de l’objet `My.Computer.Mouse` a été appelée, mais aucune souris ou aucun port de souris n’est installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="dae49-103">One of the properties of the `My.Computer.Mouse` object was called, but the computer has no mouse or mouse port installed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dae49-104">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="dae49-104">To correct this error</span></span>  
  
- <span data-ttu-id="dae49-105">Ajoutez un bloc `Try...Catch` autour de l’appel à la propriété de l’objet `My.Computer.Mouse` .</span><span class="sxs-lookup"><span data-stu-id="dae49-105">Add a `Try...Catch` block around the call to the property of the `My.Computer.Mouse` object.</span></span>  
  
     <span data-ttu-id="dae49-106">— ou —</span><span class="sxs-lookup"><span data-stu-id="dae49-106">— or —</span></span>  
  
- <span data-ttu-id="dae49-107">Installez une souris sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="dae49-107">Install a mouse on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dae49-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dae49-108">See also</span></span>

- [<span data-ttu-id="dae49-109">My.Computer.Mouse</span><span class="sxs-lookup"><span data-stu-id="dae49-109">My.Computer.Mouse</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse)
- [<span data-ttu-id="dae49-110">Gestion et levée d’exceptions dans .NET</span><span class="sxs-lookup"><span data-stu-id="dae49-110">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="dae49-111">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="dae49-111">Try...Catch...Finally Statement</span></span>](../language-reference/statements/try-catch-finally-statement.md)
