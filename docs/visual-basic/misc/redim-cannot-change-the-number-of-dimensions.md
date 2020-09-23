---
title: "'ReDim' ne peut pas changer le nombre de dimensions"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: 8d80af7682f27b403e0f463fdbebbcac71f18b01
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077369"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="f501a-102">'ReDim' ne peut pas changer le nombre de dimensions</span><span class="sxs-lookup"><span data-stu-id="f501a-102">'ReDim' cannot change the number of dimensions</span></span>

<span data-ttu-id="f501a-103">Une opération tente d’utiliser l’instruction `ReDim` pour modifier le rang (nombre de dimensions) d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="f501a-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="f501a-104">L’instruction`ReDim` peut modifier la taille d’une ou plusieurs dimensions d’un tableau qui a déjà été déclaré en bonne et due forme, mais elle ne peut pas modifier le rang d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="f501a-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f501a-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="f501a-105">To correct this error</span></span>  
  
- <span data-ttu-id="f501a-106">Assurez-vous de bien vouloir modifier le rang du tableau et non la taille de ses dimensions et, si possible, utilisez `Dim` pour déclarer un nouveau tableau avec le rang souhaité.</span><span class="sxs-lookup"><span data-stu-id="f501a-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f501a-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f501a-107">See also</span></span>

- [<span data-ttu-id="f501a-108">Tableaux dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f501a-108">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="f501a-109">Dimensions de tableau dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f501a-109">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="f501a-110">ReDim (instruction)</span><span class="sxs-lookup"><span data-stu-id="f501a-110">ReDim Statement</span></span>](../language-reference/statements/redim-statement.md)
- [<span data-ttu-id="f501a-111">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="f501a-111">Dim Statement</span></span>](../language-reference/statements/dim-statement.md)
