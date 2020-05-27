---
title: IGCHostControl::RequestVirtualMemLimit, méthode
ms.date: 03/30/2017
api_name:
- IGCHostControl.RequestVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type:
- apiref
ms.openlocfilehash: d4814e44b1a5311cf6800c804df7a7e11000cbab
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805134"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="e2eed-102">IGCHostControl::RequestVirtualMemLimit, méthode</span><span class="sxs-lookup"><span data-stu-id="e2eed-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="e2eed-103">Demande à l’hôte de modifier les limites de la mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="e2eed-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2eed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2eed-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2eed-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e2eed-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="e2eed-106">dans Taille de mémoire demandée à allouer.</span><span class="sxs-lookup"><span data-stu-id="e2eed-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="e2eed-107">[in, out] Pointeur vers la taille réelle de la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="e2eed-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2eed-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e2eed-108">Requirements</span></span>  
 <span data-ttu-id="e2eed-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2eed-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2eed-110">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e2eed-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e2eed-111">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e2eed-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2eed-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2eed-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2eed-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2eed-113">See also</span></span>

- [<span data-ttu-id="e2eed-114">IGCHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="e2eed-114">IGCHostControl Interface</span></span>](igchostcontrol-interface.md)
