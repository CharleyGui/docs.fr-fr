---
title: IGCHost::SetGCStartupLimits, méthode
ms.date: 03/30/2017
api_name:
- IGCHost.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type:
- apiref
ms.openlocfilehash: 1ae50fb3ff15097f9a6ca5839f3832bcfc58d3f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134853"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="f7fd8-102">IGCHost::SetGCStartupLimits, méthode</span><span class="sxs-lookup"><span data-stu-id="f7fd8-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="f7fd8-103">Définit la taille du segment et la taille maximale de la génération 0.</span><span class="sxs-lookup"><span data-stu-id="f7fd8-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f7fd8-104">À partir de la .NET Framework 4,5, vous pouvez définir la taille du segment et la taille maximale de la génération 0 sur des valeurs supérieures à `DWORD` à l’aide de la méthode [IGCHost2 :: setgcstartuplimitsex,](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f7fd8-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7fd8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7fd8-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7fd8-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f7fd8-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="f7fd8-107">dans Taille du segment utilisé par le système de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f7fd8-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="f7fd8-108">dans Taille maximale de la génération 0.</span><span class="sxs-lookup"><span data-stu-id="f7fd8-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7fd8-109">Notes</span><span class="sxs-lookup"><span data-stu-id="f7fd8-109">Remarks</span></span>  
 <span data-ttu-id="f7fd8-110">La méthode `SetGCStartupLimits` ne peut être appelée qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="f7fd8-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="f7fd8-111">Ces valeurs ne peuvent pas être modifiées ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="f7fd8-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7fd8-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="f7fd8-112">Requirements</span></span>  
 <span data-ttu-id="f7fd8-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7fd8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7fd8-114">**En-tête :** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="f7fd8-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="f7fd8-115">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f7fd8-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7fd8-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7fd8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7fd8-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7fd8-117">See also</span></span>

- [<span data-ttu-id="f7fd8-118">IGCHost, interface</span><span class="sxs-lookup"><span data-stu-id="f7fd8-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
