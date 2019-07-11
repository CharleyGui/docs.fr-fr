---
title: IGCHost::SetVirtualMemLimit, méthode
ms.date: 03/30/2017
api_name:
- IGCHost.SetVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetVirtualMemLimit
helpviewer_keywords:
- IGCHost::SetVirtualMemLimit method [.NET Framework hosting]
- SetVirtualMemLimit method [.NET Framework hosting]
ms.assetid: c7e7c2d0-e58c-4650-b40c-47b2be2cda45
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c43c2259d5b899f05e42437aa121dde57ce4b0c8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766483"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="41d53-102">IGCHost::SetVirtualMemLimit, méthode</span><span class="sxs-lookup"><span data-stu-id="41d53-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="41d53-103">Définit la taille maximale de mémoire virtuelle du runtime.</span><span class="sxs-lookup"><span data-stu-id="41d53-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41d53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41d53-104">Syntax</span></span>  
  
```cpp  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41d53-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="41d53-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="41d53-106">[in] La taille maximale, en mégaoctets, de mémoire virtuelle du runtime.</span><span class="sxs-lookup"><span data-stu-id="41d53-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41d53-107">Notes</span><span class="sxs-lookup"><span data-stu-id="41d53-107">Remarks</span></span>  
 <span data-ttu-id="41d53-108">La taille maximale de mémoire virtuelle du runtime peut être modifiée dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="41d53-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41d53-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="41d53-109">Requirements</span></span>  
 <span data-ttu-id="41d53-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41d53-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41d53-111">**En-tête :** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="41d53-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="41d53-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="41d53-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41d53-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41d53-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41d53-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41d53-114">See also</span></span>

- [<span data-ttu-id="41d53-115">IGCHost, interface</span><span class="sxs-lookup"><span data-stu-id="41d53-115">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
