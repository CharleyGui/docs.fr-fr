---
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream, méthode
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream method [.NET Framework hosting]
- GetReferencedAssembliesFromStream method [.NET Framework hosting]
ms.assetid: fe9849c1-c3fc-477b-a31f-e8619f5516f5
topic_type:
- apiref
ms.openlocfilehash: f4c200ad23ff7a71298e84fda857912da53978a5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126685"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="9d918-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream, méthode</span><span class="sxs-lookup"><span data-stu-id="9d918-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>
<span data-ttu-id="9d918-103">Obtient un pointeur vers un objet [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) qui contient les données d’identité d’assembly pour les assemblys référencés par l’assembly dans le flux spécifié.</span><span class="sxs-lookup"><span data-stu-id="9d918-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d918-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d918-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d918-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9d918-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="9d918-106">dans Pointeur d’interface vers un `IStream` contenant l’assembly à évaluer.</span><span class="sxs-lookup"><span data-stu-id="9d918-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9d918-107">dans Fourni pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="9d918-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="9d918-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT est la seule valeur prise en charge par la version actuelle du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="9d918-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="9d918-109">dans Pointeur vers un objet [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) qui contient les données d’identité d’assembly pour les assemblys à exclure de `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="9d918-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="9d918-110">à Pointeur vers l’adresse d’un objet `ICLRReferenceAssemblyEnum` qui contient les données d’identité de l’assembly pour les assemblys référencés par l’assembly dans `pStream`, à l’exclusion des assemblys dans `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="9d918-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d918-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9d918-111">Return Value</span></span>  
  
|<span data-ttu-id="9d918-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d918-112">HRESULT</span></span>|<span data-ttu-id="9d918-113">Description</span><span class="sxs-lookup"><span data-stu-id="9d918-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d918-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d918-114">S_OK</span></span>|<span data-ttu-id="9d918-115">La méthode a été retournée avec succès.</span><span class="sxs-lookup"><span data-stu-id="9d918-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="9d918-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9d918-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9d918-117">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="9d918-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9d918-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9d918-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9d918-119">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="9d918-119">The call timed out.</span></span>|  
|<span data-ttu-id="9d918-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9d918-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9d918-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="9d918-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9d918-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9d918-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9d918-123">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="9d918-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9d918-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9d918-124">E_FAIL</span></span>|<span data-ttu-id="9d918-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="9d918-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9d918-126">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9d918-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9d918-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9d918-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d918-128">Notes</span><span class="sxs-lookup"><span data-stu-id="9d918-128">Remarks</span></span>  
 <span data-ttu-id="9d918-129">L’appelant peut choisir d’exclure un ensemble de références d’assembly connues de la liste retournée.</span><span class="sxs-lookup"><span data-stu-id="9d918-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="9d918-130">Cet ensemble est défini par `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="9d918-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d918-131">spécifications</span><span class="sxs-lookup"><span data-stu-id="9d918-131">Requirements</span></span>  
 <span data-ttu-id="9d918-132">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d918-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d918-133">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9d918-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d918-134">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9d918-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d918-135">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d918-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d918-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d918-136">See also</span></span>

- [<span data-ttu-id="9d918-137">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="9d918-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="9d918-138">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="9d918-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="9d918-139">ICLRReferenceAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="9d918-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
