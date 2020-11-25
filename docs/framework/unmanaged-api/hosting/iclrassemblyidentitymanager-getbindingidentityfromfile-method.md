---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromFile, méthode
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
helpviewer_keywords:
- GetBindingIdentityFromFile method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentifyFromFile method [.NET Framework hosting]
ms.assetid: 7797562d-7b4c-4bd9-8b93-f35e0e2869e4
topic_type:
- apiref
ms.openlocfilehash: 443acfa77dc8103008263f19bed116d02e7ea676
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716732"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="9c98b-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile, méthode</span><span class="sxs-lookup"><span data-stu-id="9c98b-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>

<span data-ttu-id="9c98b-103">Obtient les données de liaison de l’identité de l’assembly pour l’assembly dans le chemin d’accès au fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="9c98b-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c98b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c98b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c98b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9c98b-105">Parameters</span></span>  

 `pwzFilePath`  
 <span data-ttu-id="9c98b-106">dans Chemin d’accès au fichier à évaluer.</span><span class="sxs-lookup"><span data-stu-id="9c98b-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9c98b-107">dans Valeur de l’énumération [ECLRAssemblyIdentityFlags,](eclrassemblyidentityflags-enumeration.md) qui indique le type d’identité d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="9c98b-107">[in] A value of the [ECLRAssemblyIdentityFlags](eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="9c98b-108">Fourni pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="9c98b-108">Provided for future extensibility.</span></span> <span data-ttu-id="9c98b-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT est la seule valeur prise en charge par la version 2,0 du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="9c98b-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="9c98b-110">à Mémoire tampon contenant les données d’identité de l’assembly opaque.</span><span class="sxs-lookup"><span data-stu-id="9c98b-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="9c98b-111">[in, out] Pointeur vers la taille de `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="9c98b-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c98b-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="9c98b-112">Return Value</span></span>  
  
|<span data-ttu-id="9c98b-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9c98b-113">HRESULT</span></span>|<span data-ttu-id="9c98b-114">Description</span><span class="sxs-lookup"><span data-stu-id="9c98b-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9c98b-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="9c98b-115">S_OK</span></span>|<span data-ttu-id="9c98b-116">Retour réussi de la méthode.</span><span class="sxs-lookup"><span data-stu-id="9c98b-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="9c98b-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9c98b-117">E_INVALIDARG</span></span>|<span data-ttu-id="9c98b-118">Le fourni `pwzFilePath` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="9c98b-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="9c98b-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="9c98b-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="9c98b-120">La taille de `pwzBuffer` est trop petite.</span><span class="sxs-lookup"><span data-stu-id="9c98b-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="9c98b-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9c98b-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9c98b-122">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="9c98b-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9c98b-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9c98b-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9c98b-124">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="9c98b-124">The call timed out.</span></span>|  
|<span data-ttu-id="9c98b-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9c98b-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9c98b-126">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="9c98b-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9c98b-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9c98b-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9c98b-128">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="9c98b-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9c98b-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9c98b-129">E_FAIL</span></span>|<span data-ttu-id="9c98b-130">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="9c98b-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9c98b-131">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9c98b-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9c98b-132">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9c98b-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c98b-133">Remarques</span><span class="sxs-lookup"><span data-stu-id="9c98b-133">Remarks</span></span>  

 <span data-ttu-id="9c98b-134">`GetBindingIdentityFromFile` est généralement appelée deux fois.</span><span class="sxs-lookup"><span data-stu-id="9c98b-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="9c98b-135">Le premier appel fournit une valeur null pour `pwzBuffer` , et la méthode retourne la taille appropriée dans `pcchBufferSize` .</span><span class="sxs-lookup"><span data-stu-id="9c98b-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="9c98b-136">Le deuxième appel fournit une mémoire tampon allouée de manière appropriée, et la méthode retourne avec les données de mémoire tampon en cours à l’achèvement.</span><span class="sxs-lookup"><span data-stu-id="9c98b-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c98b-137">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9c98b-137">Requirements</span></span>  

 <span data-ttu-id="9c98b-138">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c98b-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c98b-139">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9c98b-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9c98b-140">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9c98b-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c98b-141">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c98b-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c98b-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c98b-142">See also</span></span>

- [<span data-ttu-id="9c98b-143">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="9c98b-143">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="9c98b-144">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="9c98b-144">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="9c98b-145">ICLRHostBindingPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="9c98b-145">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
