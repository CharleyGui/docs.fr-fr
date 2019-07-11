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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbb0b6191c74c2b7ebdc8267701f246c17b016f9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779526"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="47a7f-102">IGCHostControl::RequestVirtualMemLimit, méthode</span><span class="sxs-lookup"><span data-stu-id="47a7f-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="47a7f-103">Demande à l’hôte de modifier les limites de mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="47a7f-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47a7f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47a7f-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47a7f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="47a7f-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="47a7f-106">[in] La taille de la mémoire à allouer.</span><span class="sxs-lookup"><span data-stu-id="47a7f-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="47a7f-107">[in, out] Pointeur vers la taille réelle de mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="47a7f-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47a7f-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="47a7f-108">Requirements</span></span>  
 <span data-ttu-id="47a7f-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47a7f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47a7f-110">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="47a7f-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="47a7f-111">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="47a7f-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47a7f-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47a7f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47a7f-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47a7f-113">See also</span></span>

- [<span data-ttu-id="47a7f-114">IGCHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="47a7f-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
