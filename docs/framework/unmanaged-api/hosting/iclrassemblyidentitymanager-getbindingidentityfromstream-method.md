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
ms.openlocfilehash: f1e6a47c0838782ae0610d49ca7fce3eb8554458
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716705"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="ac10c-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream, méthode</span><span class="sxs-lookup"><span data-stu-id="ac10c-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>

<span data-ttu-id="ac10c-103">Obtient les données d’identité d’assembly canoniques pour l’assembly dans le flux spécifié.</span><span class="sxs-lookup"><span data-stu-id="ac10c-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac10c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac10c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac10c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ac10c-105">Parameters</span></span>  

 `pStream`  
 <span data-ttu-id="ac10c-106">dans Flux d’assembly à évaluer.</span><span class="sxs-lookup"><span data-stu-id="ac10c-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ac10c-107">dans Fourni pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="ac10c-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="ac10c-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT est la seule valeur prise en charge par la version actuelle du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ac10c-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="ac10c-109">à Mémoire tampon contenant les données d’identité de l’assembly opaque.</span><span class="sxs-lookup"><span data-stu-id="ac10c-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="ac10c-110">[in, out] Taille de `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="ac10c-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac10c-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="ac10c-111">Return Value</span></span>  
  
|<span data-ttu-id="ac10c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac10c-112">HRESULT</span></span>|<span data-ttu-id="ac10c-113">Description</span><span class="sxs-lookup"><span data-stu-id="ac10c-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac10c-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac10c-114">S_OK</span></span>|<span data-ttu-id="ac10c-115">Retour réussi de la méthode.</span><span class="sxs-lookup"><span data-stu-id="ac10c-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="ac10c-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ac10c-116">E_INVALIDARG</span></span>|<span data-ttu-id="ac10c-117">Le fourni `pStream` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="ac10c-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="ac10c-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="ac10c-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="ac10c-119">La taille de `pwzBuffer` est trop petite.</span><span class="sxs-lookup"><span data-stu-id="ac10c-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="ac10c-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ac10c-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ac10c-121">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="ac10c-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ac10c-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ac10c-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ac10c-123">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="ac10c-123">The call timed out.</span></span>|  
|<span data-ttu-id="ac10c-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ac10c-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ac10c-125">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="ac10c-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ac10c-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ac10c-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ac10c-127">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="ac10c-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ac10c-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ac10c-128">E_FAIL</span></span>|<span data-ttu-id="ac10c-129">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="ac10c-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ac10c-130">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="ac10c-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ac10c-131">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ac10c-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac10c-132">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ac10c-132">Requirements</span></span>  

 <span data-ttu-id="ac10c-133">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac10c-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac10c-134">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ac10c-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac10c-135">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac10c-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac10c-136">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac10c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac10c-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac10c-137">See also</span></span>

- [<span data-ttu-id="ac10c-138">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="ac10c-138">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="ac10c-139">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="ac10c-139">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
