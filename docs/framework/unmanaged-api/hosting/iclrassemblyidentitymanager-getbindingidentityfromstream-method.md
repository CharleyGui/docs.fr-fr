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
ms.openlocfilehash: abba19600616cad8ba3377ae2ebb23459449d2a0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615980"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="728e3-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream, méthode</span><span class="sxs-lookup"><span data-stu-id="728e3-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="728e3-103">Obtient les données d’identité d’assembly canoniques pour l’assembly dans le flux spécifié.</span><span class="sxs-lookup"><span data-stu-id="728e3-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="728e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="728e3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="728e3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="728e3-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="728e3-106">dans Flux d’assembly à évaluer.</span><span class="sxs-lookup"><span data-stu-id="728e3-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="728e3-107">dans Fourni pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="728e3-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="728e3-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT est la seule valeur prise en charge par la version actuelle du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="728e3-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="728e3-109">à Mémoire tampon contenant les données d’identité de l’assembly opaque.</span><span class="sxs-lookup"><span data-stu-id="728e3-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="728e3-110">[in, out] Taille de `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="728e3-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="728e3-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="728e3-111">Return Value</span></span>  
  
|<span data-ttu-id="728e3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="728e3-112">HRESULT</span></span>|<span data-ttu-id="728e3-113">Description</span><span class="sxs-lookup"><span data-stu-id="728e3-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="728e3-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="728e3-114">S_OK</span></span>|<span data-ttu-id="728e3-115">Retour réussi de la méthode.</span><span class="sxs-lookup"><span data-stu-id="728e3-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="728e3-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="728e3-116">E_INVALIDARG</span></span>|<span data-ttu-id="728e3-117">Le fourni `pStream` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="728e3-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="728e3-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="728e3-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="728e3-119">La taille de `pwzBuffer` est trop petite.</span><span class="sxs-lookup"><span data-stu-id="728e3-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="728e3-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="728e3-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="728e3-121">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="728e3-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="728e3-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="728e3-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="728e3-123">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="728e3-123">The call timed out.</span></span>|  
|<span data-ttu-id="728e3-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="728e3-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="728e3-125">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="728e3-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="728e3-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="728e3-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="728e3-127">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="728e3-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="728e3-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="728e3-128">E_FAIL</span></span>|<span data-ttu-id="728e3-129">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="728e3-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="728e3-130">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="728e3-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="728e3-131">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="728e3-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="728e3-132">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="728e3-132">Requirements</span></span>  
 <span data-ttu-id="728e3-133">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="728e3-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="728e3-134">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="728e3-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="728e3-135">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="728e3-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="728e3-136">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="728e3-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="728e3-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="728e3-137">See also</span></span>

- [<span data-ttu-id="728e3-138">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="728e3-138">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="728e3-139">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="728e3-139">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
