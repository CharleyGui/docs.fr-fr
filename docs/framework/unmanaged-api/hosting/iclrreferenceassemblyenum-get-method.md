---
title: ICLRReferenceAssemblyEnum::Get, méthode
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum::Get
helpviewer_keywords:
- ICLRReferenceAssemblyEnum::Get method [.NET Framework hosting]
- Get method, ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: f21c1612-9c5d-4abc-a337-577086d29c17
topic_type:
- apiref
ms.openlocfilehash: 8f479443e168c3fc7c627c3227e59f1e8b54f0e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120504"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="4b443-102">ICLRReferenceAssemblyEnum::Get, méthode</span><span class="sxs-lookup"><span data-stu-id="4b443-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="4b443-103">Obtient l’identité de l’assembly à l’index fourni.</span><span class="sxs-lookup"><span data-stu-id="4b443-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b443-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b443-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b443-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4b443-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="4b443-106">dans Index de base zéro de l’identité de l’assembly à retourner.</span><span class="sxs-lookup"><span data-stu-id="4b443-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="4b443-107">à Mémoire tampon contenant les données d’identité de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="4b443-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="4b443-108">[in, out] Taille de la mémoire tampon de `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="4b443-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b443-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4b443-109">Return Value</span></span>  
  
|<span data-ttu-id="4b443-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4b443-110">HRESULT</span></span>|<span data-ttu-id="4b443-111">Description</span><span class="sxs-lookup"><span data-stu-id="4b443-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4b443-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="4b443-112">S_OK</span></span>|<span data-ttu-id="4b443-113">`Get` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="4b443-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="4b443-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="4b443-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="4b443-115">`pwzBuffer` est trop petit.</span><span class="sxs-lookup"><span data-stu-id="4b443-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="4b443-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="4b443-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="4b443-117">L’énumération ne contient plus d’éléments.</span><span class="sxs-lookup"><span data-stu-id="4b443-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="4b443-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4b443-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4b443-119">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="4b443-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4b443-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4b443-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4b443-121">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="4b443-121">The call timed out.</span></span>|  
|<span data-ttu-id="4b443-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4b443-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4b443-123">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="4b443-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4b443-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4b443-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4b443-125">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="4b443-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4b443-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4b443-126">E_FAIL</span></span>|<span data-ttu-id="4b443-127">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="4b443-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4b443-128">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="4b443-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4b443-129">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4b443-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b443-130">Notes</span><span class="sxs-lookup"><span data-stu-id="4b443-130">Remarks</span></span>  
 <span data-ttu-id="4b443-131">`Get` est généralement appelée deux fois.</span><span class="sxs-lookup"><span data-stu-id="4b443-131">`Get` is typically called twice.</span></span> <span data-ttu-id="4b443-132">Le premier appel fournit une valeur null pour `pwzBuffer`et définit `pcchBufferSize` à la taille appropriée pour `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="4b443-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="4b443-133">Le deuxième appel fournit un `pwzBuffer`de taille appropriée et contient les données d’identité de l’assembly canoniques à l’achèvement.</span><span class="sxs-lookup"><span data-stu-id="4b443-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b443-134">spécifications</span><span class="sxs-lookup"><span data-stu-id="4b443-134">Requirements</span></span>  
 <span data-ttu-id="4b443-135">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b443-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b443-136">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4b443-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4b443-137">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4b443-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b443-138">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b443-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b443-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b443-139">See also</span></span>

- [<span data-ttu-id="4b443-140">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="4b443-140">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="4b443-141">ICLRReferenceAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="4b443-141">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
