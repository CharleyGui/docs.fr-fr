---
title: Format de Presse-papiers non valide
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 429d1e120a0044152a358a87663eb09989f45b0e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874584"
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="615ed-102">Format de Presse-papiers non valide</span><span class="sxs-lookup"><span data-stu-id="615ed-102">Clipboard format is not valid</span></span>

<span data-ttu-id="615ed-103">Le format de presse-papiers spécifié est incompatible avec la méthode en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="615ed-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="615ed-104">Cette erreur peut avoir plusieurs causes :</span><span class="sxs-lookup"><span data-stu-id="615ed-104">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="615ed-105">Utilisation de la méthode ou du presse-papiers `GetText` `SetText` avec un format de presse-papiers autre que `vbCFText` ou `vbCFLink` .</span><span class="sxs-lookup"><span data-stu-id="615ed-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
- <span data-ttu-id="615ed-106">Utilisation de la méthode ou du presse-papiers `GetData` `SetData` avec un format de presse-papiers autre que `vbCFBitmap` , `vbCFDIB` ou `vbCFMetafile` .</span><span class="sxs-lookup"><span data-stu-id="615ed-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
- <span data-ttu-id="615ed-107">L’utilisation `GetData` `SetData` des méthodes ou d’un `DataObject` avec un format de presse-papiers dans la plage réservée par Microsoft Windows pour les formats enregistrés (&HC000-&HFFFF), lorsque ce format de presse-papiers n’a pas été inscrit auprès de Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="615ed-107">Using the `GetData` or `SetData` methods of a `DataObject` with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="615ed-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="615ed-108">To correct this error</span></span>  
  
- <span data-ttu-id="615ed-109">Supprimez le format non valide et spécifiez un format valide.</span><span class="sxs-lookup"><span data-stu-id="615ed-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="615ed-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="615ed-110">See also</span></span>

- [<span data-ttu-id="615ed-111">Presse-papiers : ajout d’autres formats</span><span class="sxs-lookup"><span data-stu-id="615ed-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
