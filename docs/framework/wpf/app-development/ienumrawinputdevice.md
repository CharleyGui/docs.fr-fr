---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: 5249d7ea359db5d5c58ae87600f61048b465b4c1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964768"
---
# <a name="ienumrawinputdevice"></a><span data-ttu-id="6c465-102">IEnumRAWINPUTDEVICE</span><span class="sxs-lookup"><span data-stu-id="6c465-102">IEnumRAWINPUTDEVICE</span></span>
<span data-ttu-id="6c465-103">Cette interface énumère les périphériques d'entrée brute ; elle est uniquement utilisée par PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="6c465-103">This interface enumerates the raw input devices, and is only used by PresentationHost.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6c465-104">Cette API est conçue et pris en charge uniquement sur l'ordinateur client local</span><span class="sxs-lookup"><span data-stu-id="6c465-104">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="6c465-105">Membres</span><span class="sxs-lookup"><span data-stu-id="6c465-105">Members</span></span>  
  
|<span data-ttu-id="6c465-106">Membre</span><span class="sxs-lookup"><span data-stu-id="6c465-106">Member</span></span>|<span data-ttu-id="6c465-107">Description</span><span class="sxs-lookup"><span data-stu-id="6c465-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6c465-108">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="6c465-108">IEnumRAWINPUTDEVIC:Next</span></span>](ienumrawinputdevic-next.md)|<span data-ttu-id="6c465-109">Énumère les éléments `celt` suivants (c'est-à-dire les structures RAWINPUTDEVICE) dans la liste de l'énumérateur, en les retournant dans `rgelt` avec le nombre réel d'éléments énumérés dans `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="6c465-109">Enumerates the next `celt` elements (that is, RAWINPUTDEVICE structures) in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>|  
|[<span data-ttu-id="6c465-110">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="6c465-110">IEnumRAWINPUTDEVIC:Skip</span></span>](ienumrawinputdevic-skip.md)|<span data-ttu-id="6c465-111">Indique à l’énumérateur d’ignorer les éléments `celt` suivants dans l’énumération afin que l’appel suivant à [IEnumRAWINPUTDEVIC: Next](ienumrawinputdevic-next.md) ne retourne pas ces éléments.</span><span class="sxs-lookup"><span data-stu-id="6c465-111">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) will not return those elements.</span></span>|  
|[<span data-ttu-id="6c465-112">IEnumRAWINPUTDEVIC:Reset</span><span class="sxs-lookup"><span data-stu-id="6c465-112">IEnumRAWINPUTDEVIC:Reset</span></span>](ienumrawinputdevic-reset.md)|<span data-ttu-id="6c465-113">Réinitialise la séquence d'énumération au début.</span><span class="sxs-lookup"><span data-stu-id="6c465-113">Resets the enumeration sequence to the beginning.</span></span>|  
|[<span data-ttu-id="6c465-114">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="6c465-114">IEnumRAWINPUTDEVIC:Clone</span></span>](ienumrawinputdevic-clone.md)|<span data-ttu-id="6c465-115">Crée un autre énumérateur de périphériques d'entrée brute avec le même état que l'énumérateur actif pour itérer au sein de la même liste.</span><span class="sxs-lookup"><span data-stu-id="6c465-115">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6c465-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c465-116">See also</span></span>

- [<span data-ttu-id="6c465-117">À propos des entrées brutes</span><span class="sxs-lookup"><span data-stu-id="6c465-117">About Raw Input</span></span>](/windows/desktop/inputdev/about-raw-input)
