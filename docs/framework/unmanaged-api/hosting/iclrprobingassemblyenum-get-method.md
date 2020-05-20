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
ms.openlocfilehash: ea66c142afc097d1003df4e7f5f5b960a91e2ab0
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703385"
---
# <a name="iclrprobingassemblyenumget-method"></a><span data-ttu-id="a0063-102">ICLRProbingAssemblyEnum::Get, méthode</span><span class="sxs-lookup"><span data-stu-id="a0063-102">ICLRProbingAssemblyEnum::Get Method</span></span>
<span data-ttu-id="a0063-103">Obtient l’identité de l’assembly au niveau de l’index spécifié.</span><span class="sxs-lookup"><span data-stu-id="a0063-103">Gets the assembly identity at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0063-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0063-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0063-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a0063-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="a0063-106">dans Index de base zéro de l’identité de l’assembly à retourner.</span><span class="sxs-lookup"><span data-stu-id="a0063-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="a0063-107">à Mémoire tampon contenant les données d’identité de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a0063-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="a0063-108">[in, out] Taille de la `pwzBuffer` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="a0063-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0063-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a0063-109">Return Value</span></span>  
  
|<span data-ttu-id="a0063-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0063-110">HRESULT</span></span>|<span data-ttu-id="a0063-111">Description</span><span class="sxs-lookup"><span data-stu-id="a0063-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0063-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a0063-112">S_OK</span></span>|<span data-ttu-id="a0063-113">`Get`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="a0063-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="a0063-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="a0063-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="a0063-115">`pwzBuffer` est trop petite.</span><span class="sxs-lookup"><span data-stu-id="a0063-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="a0063-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="a0063-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="a0063-117">L’énumération ne contient plus d’éléments.</span><span class="sxs-lookup"><span data-stu-id="a0063-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="a0063-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a0063-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a0063-119">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="a0063-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a0063-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a0063-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a0063-121">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="a0063-121">The call timed out.</span></span>|  
|<span data-ttu-id="a0063-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a0063-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a0063-123">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="a0063-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a0063-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a0063-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a0063-125">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="a0063-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a0063-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a0063-126">E_FAIL</span></span>|<span data-ttu-id="a0063-127">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="a0063-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a0063-128">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="a0063-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a0063-129">Les appels suivants à toutes les méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a0063-129">Subsequent calls to any hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0063-130">Notes</span><span class="sxs-lookup"><span data-stu-id="a0063-130">Remarks</span></span>  
 <span data-ttu-id="a0063-131">L’identité à l’index 0 est l’identité propre à l’architecture du processeur.</span><span class="sxs-lookup"><span data-stu-id="a0063-131">The identity at index 0 is the identity specific to the processor architecture.</span></span> <span data-ttu-id="a0063-132">L’identité à l’index 1 est l’assembly indépendant de l’architecture pour le langage MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="a0063-132">The identity at index 1 is the architecture-neutral assembly for Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="a0063-133">L’identité à l’index 2 ne contient aucune information d’architecture.</span><span class="sxs-lookup"><span data-stu-id="a0063-133">The identity at index 2 contains no architecture information.</span></span>  
  
 <span data-ttu-id="a0063-134">`Get`est généralement appelée deux fois.</span><span class="sxs-lookup"><span data-stu-id="a0063-134">`Get` is typically called twice.</span></span> <span data-ttu-id="a0063-135">Le premier appel fournit une valeur null pour `pwzBuffer` et définit `pcchBufferSize` la taille appropriée pour `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="a0063-135">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="a0063-136">Le deuxième appel fournit une taille appropriée `pwzBuffer` et contient les données d’identité de l’assembly canonique à l’achèvement.</span><span class="sxs-lookup"><span data-stu-id="a0063-136">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0063-137">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="a0063-137">Requirements</span></span>  
 <span data-ttu-id="a0063-138">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0063-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0063-139">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a0063-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a0063-140">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a0063-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0063-141">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0063-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0063-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0063-142">See also</span></span>

- [<span data-ttu-id="a0063-143">ICLRProbingAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="a0063-143">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="a0063-144">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0063-144">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
