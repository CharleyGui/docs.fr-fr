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
ms.openlocfilehash: a5e71d6ca90c8d0aa489176eb5a90bfe6896b1cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679315"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="3ce5f-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream, méthode</span><span class="sxs-lookup"><span data-stu-id="3ce5f-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>

<span data-ttu-id="3ce5f-103">Obtient un pointeur vers un objet [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) qui contient les données d’identité d’assembly pour les assemblys référencés par l’assembly dans le flux spécifié.</span><span class="sxs-lookup"><span data-stu-id="3ce5f-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ce5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ce5f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ce5f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3ce5f-105">Parameters</span></span>  

 `pStream`  
 <span data-ttu-id="3ce5f-106">dans Pointeur d’interface vers un `IStream` contenant l’assembly à évaluer.</span><span class="sxs-lookup"><span data-stu-id="3ce5f-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3ce5f-107">dans Fourni pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="3ce5f-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="3ce5f-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT est la seule valeur prise en charge par la version actuelle du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="3ce5f-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="3ce5f-109">dans Pointeur vers un objet [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) qui contient les données d’identité d’assembly pour les assemblys à exclure `ppReferenceEnum` .</span><span class="sxs-lookup"><span data-stu-id="3ce5f-109">[in] A pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="3ce5f-110">à Pointeur vers l’adresse d’un `ICLRReferenceAssemblyEnum` objet qui contient les données d’identité de l’assembly pour les assemblys référencés par l’assembly dans, à l' `pStream` exclusion des assemblys dans `pExcludeAssembliesList` .</span><span class="sxs-lookup"><span data-stu-id="3ce5f-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ce5f-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="3ce5f-111">Return Value</span></span>  
  
|<span data-ttu-id="3ce5f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3ce5f-112">HRESULT</span></span>|<span data-ttu-id="3ce5f-113">Description</span><span class="sxs-lookup"><span data-stu-id="3ce5f-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3ce5f-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="3ce5f-114">S_OK</span></span>|<span data-ttu-id="3ce5f-115">Retour réussi de la méthode.</span><span class="sxs-lookup"><span data-stu-id="3ce5f-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="3ce5f-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3ce5f-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3ce5f-117">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="3ce5f-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3ce5f-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3ce5f-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3ce5f-119">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="3ce5f-119">The call timed out.</span></span>|  
|<span data-ttu-id="3ce5f-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3ce5f-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3ce5f-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="3ce5f-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3ce5f-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3ce5f-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3ce5f-123">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="3ce5f-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3ce5f-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3ce5f-124">E_FAIL</span></span>|<span data-ttu-id="3ce5f-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="3ce5f-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3ce5f-126">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="3ce5f-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3ce5f-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3ce5f-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ce5f-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="3ce5f-128">Remarks</span></span>  

 <span data-ttu-id="3ce5f-129">L’appelant peut choisir d’exclure un ensemble de références d’assembly connues de la liste retournée.</span><span class="sxs-lookup"><span data-stu-id="3ce5f-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="3ce5f-130">Cet ensemble est défini par `pExcludeAssembliesList` .</span><span class="sxs-lookup"><span data-stu-id="3ce5f-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ce5f-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3ce5f-131">Requirements</span></span>  

 <span data-ttu-id="3ce5f-132">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ce5f-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ce5f-133">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3ce5f-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3ce5f-134">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3ce5f-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3ce5f-135">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ce5f-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ce5f-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ce5f-136">See also</span></span>

- [<span data-ttu-id="3ce5f-137">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="3ce5f-137">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="3ce5f-138">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="3ce5f-138">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="3ce5f-139">ICLRReferenceAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="3ce5f-139">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)
