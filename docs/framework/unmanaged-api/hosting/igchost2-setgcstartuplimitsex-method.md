---
title: IGCHost2::SetGCStartupLimitsEx, méthode
ms.date: 03/30/2017
api_name:
- IGCHost2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type:
- apiref
ms.openlocfilehash: d78f81093e61c40eaec334f957d8583eeb593f5e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134817"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="4e3ef-102">IGCHost2::SetGCStartupLimitsEx, méthode</span><span class="sxs-lookup"><span data-stu-id="4e3ef-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="4e3ef-103">Définit la taille du segment et la taille maximale de la génération 0.</span><span class="sxs-lookup"><span data-stu-id="4e3ef-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e3ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e3ef-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e3ef-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4e3ef-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="4e3ef-106">dans Taille du segment utilisé par le système de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4e3ef-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="4e3ef-107">dans Taille maximale de la génération 0.</span><span class="sxs-lookup"><span data-stu-id="4e3ef-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e3ef-108">Notes</span><span class="sxs-lookup"><span data-stu-id="4e3ef-108">Remarks</span></span>  
 <span data-ttu-id="4e3ef-109">Les valeurs que `SetGCStartupLimitsEx` définit peuvent être spécifiées uniquement avant le démarrage de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="4e3ef-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="4e3ef-110">Ces valeurs ne peuvent pas être modifiées ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="4e3ef-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e3ef-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="4e3ef-111">Requirements</span></span>  
 <span data-ttu-id="4e3ef-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e3ef-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e3ef-113">**En-tête :** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="4e3ef-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="4e3ef-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4e3ef-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e3ef-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e3ef-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e3ef-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e3ef-116">See also</span></span>

- [<span data-ttu-id="4e3ef-117">IGCHost2, interface</span><span class="sxs-lookup"><span data-stu-id="4e3ef-117">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
