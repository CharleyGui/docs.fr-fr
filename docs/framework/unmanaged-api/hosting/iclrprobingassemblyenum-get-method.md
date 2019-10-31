---
title: ICLRProbingAssemblyEnum::Get, méthode
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type:
- apiref
ms.openlocfilehash: 2ff1f9428a92d091a51a4cca12d69d98da0ecba2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120532"
---
# <a name="iclrprobingassemblyenumget-method"></a><span data-ttu-id="4aed0-102">ICLRProbingAssemblyEnum::Get, méthode</span><span class="sxs-lookup"><span data-stu-id="4aed0-102">ICLRProbingAssemblyEnum::Get Method</span></span>
<span data-ttu-id="4aed0-103">Obtient l’identité de l’assembly au niveau de l’index spécifié.</span><span class="sxs-lookup"><span data-stu-id="4aed0-103">Gets the assembly identity at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aed0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4aed0-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4aed0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4aed0-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="4aed0-106">dans Index de base zéro de l’identité de l’assembly à retourner.</span><span class="sxs-lookup"><span data-stu-id="4aed0-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="4aed0-107">à Mémoire tampon contenant les données d’identité de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="4aed0-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="4aed0-108">[in, out] Taille de la mémoire tampon de `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="4aed0-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4aed0-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4aed0-109">Return Value</span></span>  
  
|<span data-ttu-id="4aed0-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4aed0-110">HRESULT</span></span>|<span data-ttu-id="4aed0-111">Description</span><span class="sxs-lookup"><span data-stu-id="4aed0-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4aed0-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="4aed0-112">S_OK</span></span>|<span data-ttu-id="4aed0-113">`Get` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="4aed0-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="4aed0-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="4aed0-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="4aed0-115">`pwzBuffer` est trop petit.</span><span class="sxs-lookup"><span data-stu-id="4aed0-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="4aed0-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="4aed0-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="4aed0-117">L’énumération ne contient plus d’éléments.</span><span class="sxs-lookup"><span data-stu-id="4aed0-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="4aed0-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4aed0-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4aed0-119">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="4aed0-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4aed0-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4aed0-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4aed0-121">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="4aed0-121">The call timed out.</span></span>|  
|<span data-ttu-id="4aed0-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4aed0-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4aed0-123">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="4aed0-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4aed0-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4aed0-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4aed0-125">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="4aed0-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4aed0-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4aed0-126">E_FAIL</span></span>|<span data-ttu-id="4aed0-127">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="4aed0-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4aed0-128">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="4aed0-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4aed0-129">Les appels suivants à toute méthode d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4aed0-129">Subsequent calls to any hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4aed0-130">Notes</span><span class="sxs-lookup"><span data-stu-id="4aed0-130">Remarks</span></span>  
 <span data-ttu-id="4aed0-131">L’identité à l’index 0 est l’identité propre à l’architecture du processeur.</span><span class="sxs-lookup"><span data-stu-id="4aed0-131">The identity at index 0 is the identity specific to the processor architecture.</span></span> <span data-ttu-id="4aed0-132">L’identité à l’index 1 est l’assembly indépendant de l’architecture pour le langage MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="4aed0-132">The identity at index 1 is the architecture-neutral assembly for Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="4aed0-133">L’identité à l’index 2 ne contient aucune information d’architecture.</span><span class="sxs-lookup"><span data-stu-id="4aed0-133">The identity at index 2 contains no architecture information.</span></span>  
  
 <span data-ttu-id="4aed0-134">`Get` est généralement appelée deux fois.</span><span class="sxs-lookup"><span data-stu-id="4aed0-134">`Get` is typically called twice.</span></span> <span data-ttu-id="4aed0-135">Le premier appel fournit une valeur null pour `pwzBuffer`et définit `pcchBufferSize` à la taille appropriée pour `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="4aed0-135">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="4aed0-136">Le deuxième appel fournit un `pwzBuffer`de taille appropriée et contient les données d’identité de l’assembly canoniques à l’achèvement.</span><span class="sxs-lookup"><span data-stu-id="4aed0-136">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4aed0-137">spécifications</span><span class="sxs-lookup"><span data-stu-id="4aed0-137">Requirements</span></span>  
 <span data-ttu-id="4aed0-138">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4aed0-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4aed0-139">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4aed0-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4aed0-140">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4aed0-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4aed0-141">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4aed0-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aed0-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4aed0-142">See also</span></span>

- [<span data-ttu-id="4aed0-143">ICLRProbingAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="4aed0-143">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="4aed0-144">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="4aed0-144">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
