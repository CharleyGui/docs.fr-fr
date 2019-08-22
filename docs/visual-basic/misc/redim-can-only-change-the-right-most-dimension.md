---
title: "'ReDim' ne peut changer que la dimension la plus à droite"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: f38bcb99b682ace497859b67fe3bb829bbc80c4d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664405"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="aeb0a-102">'ReDim' ne peut changer que la dimension la plus à droite</span><span class="sxs-lookup"><span data-stu-id="aeb0a-102">'ReDim' can only change the right-most dimension</span></span>
<span data-ttu-id="aeb0a-103">Une instruction `ReDim` a tenté d’utiliser le mot clé `Preserve` pour modifier une dimension d’un tableau qui n’est pas la dernière dimension.</span><span class="sxs-lookup"><span data-stu-id="aeb0a-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="aeb0a-104">Lors de l’utilisation de `Preserve`, vous pouvez redimensionner uniquement la dernière dimension d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="aeb0a-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="aeb0a-105">Pour toutes les autres dimensions, vous devez spécifier la même taille que pour le tableau existant.</span><span class="sxs-lookup"><span data-stu-id="aeb0a-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aeb0a-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="aeb0a-106">To correct this error</span></span>  
  
- <span data-ttu-id="aeb0a-107">Supprimez le mot clé `Preserve` .</span><span class="sxs-lookup"><span data-stu-id="aeb0a-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeb0a-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aeb0a-108">See also</span></span>

- [<span data-ttu-id="aeb0a-109">Tableaux en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aeb0a-109">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="aeb0a-110">Dimensions de tableau dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aeb0a-110">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="aeb0a-111">ReDim (instruction)</span><span class="sxs-lookup"><span data-stu-id="aeb0a-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="aeb0a-112">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="aeb0a-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
