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
ms.openlocfilehash: 263058131e63205aa37f81847ed647944fef7540
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731387"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="34f14-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference, méthode</span><span class="sxs-lookup"><span data-stu-id="34f14-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>

<span data-ttu-id="34f14-103">Obtient un énumérateur [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) pour les identités d’assembly référencées par l’assembly avec le type d’identité spécifié.</span><span class="sxs-lookup"><span data-stu-id="34f14-103">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34f14-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34f14-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34f14-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="34f14-105">Parameters</span></span>  

 `dwMachineType`  
 <span data-ttu-id="34f14-106">dans Valeur valide qui spécifie l’architecture du processeur, comme défini dans Winnt. h.</span><span class="sxs-lookup"><span data-stu-id="34f14-106">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="34f14-107">dans Fourni pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="34f14-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="34f14-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT est la seule valeur prise en charge par la version actuelle du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="34f14-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="34f14-109">dans Identité de liaison d’assembly opaque, généralement retournée par un appel à la méthode [ICLRAssemblyIdentityManager :: GetBindingIdentityFromFile,](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) ou [ICLRAssemblyIdentityManager :: GetBindingIdentityFromStream,](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) .</span><span class="sxs-lookup"><span data-stu-id="34f14-109">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="34f14-110">à Pointeur d’interface vers un `ICLRProbingAssemblyEnum` énumérateur qui contient des références aux assemblys référencés par l’assembly identifié par `pwzReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="34f14-110">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34f14-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="34f14-111">Return Value</span></span>  
  
|<span data-ttu-id="34f14-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34f14-112">HRESULT</span></span>|<span data-ttu-id="34f14-113">Description</span><span class="sxs-lookup"><span data-stu-id="34f14-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34f14-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="34f14-114">S_OK</span></span>|<span data-ttu-id="34f14-115">Retour réussi de la méthode.</span><span class="sxs-lookup"><span data-stu-id="34f14-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="34f14-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="34f14-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="34f14-117">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="34f14-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="34f14-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="34f14-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="34f14-119">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="34f14-119">The call timed out.</span></span>|  
|<span data-ttu-id="34f14-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="34f14-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="34f14-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="34f14-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="34f14-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="34f14-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="34f14-123">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="34f14-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="34f14-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="34f14-124">E_FAIL</span></span>|<span data-ttu-id="34f14-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="34f14-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="34f14-126">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="34f14-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="34f14-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="34f14-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="34f14-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="34f14-128">Requirements</span></span>  

 <span data-ttu-id="34f14-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34f14-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34f14-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="34f14-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34f14-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="34f14-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34f14-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34f14-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34f14-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34f14-133">See also</span></span>

- [<span data-ttu-id="34f14-134">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="34f14-134">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="34f14-135">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="34f14-135">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="34f14-136">ICLRProbingAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="34f14-136">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
