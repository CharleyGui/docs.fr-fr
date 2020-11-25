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
ms.openlocfilehash: 4dca62903a123765ceb8bb251b79455ad0e4730a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726806"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="27a68-102">IGCHost2::SetGCStartupLimitsEx, méthode</span><span class="sxs-lookup"><span data-stu-id="27a68-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>

<span data-ttu-id="27a68-103">Définit la taille du segment et la taille maximale de la génération 0.</span><span class="sxs-lookup"><span data-stu-id="27a68-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27a68-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27a68-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27a68-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="27a68-105">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="27a68-106">dans Taille du segment utilisé par le système de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="27a68-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="27a68-107">dans Taille maximale de la génération 0.</span><span class="sxs-lookup"><span data-stu-id="27a68-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27a68-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="27a68-108">Remarks</span></span>  

 <span data-ttu-id="27a68-109">Les valeurs définies par `SetGCStartupLimitsEx` ne peuvent être spécifiées qu’avant le démarrage de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="27a68-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="27a68-110">Ces valeurs ne peuvent pas être modifiées ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="27a68-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27a68-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="27a68-111">Requirements</span></span>  

 <span data-ttu-id="27a68-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27a68-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27a68-113">**En-tête :** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="27a68-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="27a68-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="27a68-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27a68-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27a68-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27a68-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27a68-116">See also</span></span>

- [<span data-ttu-id="27a68-117">IGCHost2, interface</span><span class="sxs-lookup"><span data-stu-id="27a68-117">IGCHost2 Interface</span></span>](igchost2-interface.md)
