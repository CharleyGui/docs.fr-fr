---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromStream, méthode
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
helpviewer_keywords:
- GetBindingIdentityFromStream method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream method [.NET Framework hosting]
ms.assetid: 40123b30-a589-46b3-95d3-af7b2b0baa05
topic_type:
- apiref
ms.openlocfilehash: b30f6f5ce22290dc3750cef0171349ec5ff2f76a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126734"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="52700-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream, méthode</span><span class="sxs-lookup"><span data-stu-id="52700-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="52700-103">Obtient les données d’identité d’assembly canoniques pour l’assembly dans le flux spécifié.</span><span class="sxs-lookup"><span data-stu-id="52700-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52700-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52700-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52700-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="52700-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="52700-106">dans Flux d’assembly à évaluer.</span><span class="sxs-lookup"><span data-stu-id="52700-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="52700-107">dans Fourni pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="52700-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="52700-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT est la seule valeur prise en charge par la version actuelle du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="52700-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="52700-109">à Mémoire tampon contenant les données d’identité de l’assembly opaque.</span><span class="sxs-lookup"><span data-stu-id="52700-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="52700-110">[in, out] Taille de `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="52700-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52700-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="52700-111">Return Value</span></span>  
  
|<span data-ttu-id="52700-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="52700-112">HRESULT</span></span>|<span data-ttu-id="52700-113">Description</span><span class="sxs-lookup"><span data-stu-id="52700-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="52700-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="52700-114">S_OK</span></span>|<span data-ttu-id="52700-115">La méthode a été retournée avec succès.</span><span class="sxs-lookup"><span data-stu-id="52700-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="52700-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="52700-116">E_INVALIDARG</span></span>|<span data-ttu-id="52700-117">Le `pStream` fourni a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="52700-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="52700-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="52700-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="52700-119">La taille de `pwzBuffer` est trop petite.</span><span class="sxs-lookup"><span data-stu-id="52700-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="52700-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="52700-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="52700-121">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="52700-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="52700-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="52700-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="52700-123">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="52700-123">The call timed out.</span></span>|  
|<span data-ttu-id="52700-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="52700-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="52700-125">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="52700-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="52700-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="52700-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="52700-127">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="52700-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="52700-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="52700-128">E_FAIL</span></span>|<span data-ttu-id="52700-129">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="52700-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="52700-130">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="52700-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="52700-131">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="52700-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="52700-132">spécifications</span><span class="sxs-lookup"><span data-stu-id="52700-132">Requirements</span></span>  
 <span data-ttu-id="52700-133">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52700-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52700-134">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="52700-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="52700-135">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="52700-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52700-136">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52700-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52700-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52700-137">See also</span></span>

- [<span data-ttu-id="52700-138">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="52700-138">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="52700-139">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="52700-139">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
