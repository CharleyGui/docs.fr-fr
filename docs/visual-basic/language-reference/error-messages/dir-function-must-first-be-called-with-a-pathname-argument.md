---
title: La fonction ’Dir’ doit d’abord être appelée avec un argument ’Pathname’
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 1064a44f7c266b9dcce05dfddedef6bb1e919999
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874460"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="22c46-102">La fonction ’Dir’ doit d’abord être appelée avec un argument ’Pathname’</span><span class="sxs-lookup"><span data-stu-id="22c46-102">'Dir' function must first be called with a 'PathName' argument</span></span>

<span data-ttu-id="22c46-103">Un appel initial à la `Dir` fonction n’inclut pas l' `PathName` argument.</span><span class="sxs-lookup"><span data-stu-id="22c46-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="22c46-104">Le premier appel à `Dir` doit inclure un `PathName` , mais les appels suivants à `Dir` n’ont pas besoin d’inclure des paramètres pour récupérer l’élément suivant.</span><span class="sxs-lookup"><span data-stu-id="22c46-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="22c46-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="22c46-105">To correct this error</span></span>  
  
1. <span data-ttu-id="22c46-106">Fournissez un `PathName` argument dans l’appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="22c46-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22c46-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22c46-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
