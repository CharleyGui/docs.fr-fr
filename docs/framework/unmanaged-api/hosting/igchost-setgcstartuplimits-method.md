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
ms.openlocfilehash: 0eea9dba57886edfef13c31948a9cff94c6c1bfd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687871"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="cf3c7-102">IGCHost::SetGCStartupLimits, méthode</span><span class="sxs-lookup"><span data-stu-id="cf3c7-102">IGCHost::SetGCStartupLimits Method</span></span>

<span data-ttu-id="cf3c7-103">Définit la taille du segment et la taille maximale de la génération 0.</span><span class="sxs-lookup"><span data-stu-id="cf3c7-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cf3c7-104">À partir de la .NET Framework 4,5, vous pouvez définir la taille du segment et la taille maximale de la génération 0 sur des valeurs supérieures à à `DWORD` l’aide de la méthode [IGCHost2 :: setgcstartuplimitsex,](igchost2-setgcstartuplimitsex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cf3c7-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf3c7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf3c7-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf3c7-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cf3c7-106">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="cf3c7-107">dans Taille du segment utilisé par le système de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="cf3c7-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="cf3c7-108">dans Taille maximale de la génération 0.</span><span class="sxs-lookup"><span data-stu-id="cf3c7-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf3c7-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="cf3c7-109">Remarks</span></span>  

 <span data-ttu-id="cf3c7-110">La `SetGCStartupLimits` méthode ne peut être appelée qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="cf3c7-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="cf3c7-111">Ces valeurs ne peuvent pas être modifiées ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="cf3c7-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf3c7-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cf3c7-112">Requirements</span></span>  

 <span data-ttu-id="cf3c7-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf3c7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf3c7-114">**En-tête :** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="cf3c7-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="cf3c7-115">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf3c7-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf3c7-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf3c7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf3c7-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf3c7-117">See also</span></span>

- [<span data-ttu-id="cf3c7-118">IGCHost, interface</span><span class="sxs-lookup"><span data-stu-id="cf3c7-118">IGCHost Interface</span></span>](igchost-interface.md)
