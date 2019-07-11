---
title: ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference, méthode
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetProbingAssembliesFromReference
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference method [.NET Framework hosting]
- GetProbingAssembliesFromReference method [.NET Framework hosting]
ms.assetid: aec05744-e8d4-44c6-b4a8-e583229ac34e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55f3bd89f0ca177bcd4edef2e17a7d2256a0042a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773489"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="e8592-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference, méthode</span><span class="sxs-lookup"><span data-stu-id="e8592-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>
<span data-ttu-id="e8592-103">Obtient un [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) énumérateur pour les identités d’assembly référencé par l’assembly avec le type d’identité spécifié.</span><span class="sxs-lookup"><span data-stu-id="e8592-103">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8592-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8592-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8592-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e8592-105">Parameters</span></span>  
 `dwMachineType`  
 <span data-ttu-id="e8592-106">[in] Une valeur valide qui spécifie l’architecture de processeur, tel que défini dans WinNT.h.</span><span class="sxs-lookup"><span data-stu-id="e8592-106">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e8592-107">[in] Fourni pour des extensibilités futures.</span><span class="sxs-lookup"><span data-stu-id="e8592-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="e8592-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT est la seule valeur de la version actuelle du common language runtime (CLR) prend en charge.</span><span class="sxs-lookup"><span data-stu-id="e8592-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="e8592-109">[in] Une identité de liaison d’assembly opaque, généralement retournée par un appel à la [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) ou [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="e8592-109">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="e8592-110">[out] Un pointeur d’interface vers un `ICLRProbingAssemblyEnum` énumérateur qui contient des références aux assemblys référencés par l’assembly identifié par `pwzReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="e8592-110">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8592-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e8592-111">Return Value</span></span>  
  
|<span data-ttu-id="e8592-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e8592-112">HRESULT</span></span>|<span data-ttu-id="e8592-113">Description</span><span class="sxs-lookup"><span data-stu-id="e8592-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e8592-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e8592-114">S_OK</span></span>|<span data-ttu-id="e8592-115">La méthode a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="e8592-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="e8592-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e8592-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e8592-117">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="e8592-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e8592-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e8592-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e8592-119">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="e8592-119">The call timed out.</span></span>|  
|<span data-ttu-id="e8592-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e8592-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e8592-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="e8592-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e8592-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e8592-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e8592-123">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="e8592-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e8592-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e8592-124">E_FAIL</span></span>|<span data-ttu-id="e8592-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e8592-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e8592-126">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="e8592-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e8592-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e8592-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e8592-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e8592-128">Requirements</span></span>  
 <span data-ttu-id="e8592-129">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8592-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8592-130">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e8592-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e8592-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8592-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8592-132">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8592-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8592-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8592-133">See also</span></span>

- [<span data-ttu-id="e8592-134">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="e8592-134">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="e8592-135">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="e8592-135">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="e8592-136">ICLRProbingAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="e8592-136">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
