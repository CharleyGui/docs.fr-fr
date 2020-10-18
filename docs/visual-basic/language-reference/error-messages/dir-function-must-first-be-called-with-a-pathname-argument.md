---
title: La fonction ’Dir’ doit d’abord être appelée avec un argument ’Pathname’
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 7f8191b0ef5452fcf6f3a20c3e0f28ca84ef9c4a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163426"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="c4ccb-102">La fonction ’Dir’ doit d’abord être appelée avec un argument ’Pathname’</span><span class="sxs-lookup"><span data-stu-id="c4ccb-102">'Dir' function must first be called with a 'PathName' argument</span></span>

<span data-ttu-id="c4ccb-103">Un appel initial à la `Dir` fonction n’inclut pas l' `PathName` argument.</span><span class="sxs-lookup"><span data-stu-id="c4ccb-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="c4ccb-104">Le premier appel à `Dir` doit inclure un `PathName` , mais les appels suivants à `Dir` n’ont pas besoin d’inclure des paramètres pour récupérer l’élément suivant.</span><span class="sxs-lookup"><span data-stu-id="c4ccb-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c4ccb-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="c4ccb-105">To correct this error</span></span>

- <span data-ttu-id="c4ccb-106">Fournissez un `PathName` argument dans l’appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="c4ccb-106">Supply a `PathName` argument in the function call.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4ccb-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4ccb-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
