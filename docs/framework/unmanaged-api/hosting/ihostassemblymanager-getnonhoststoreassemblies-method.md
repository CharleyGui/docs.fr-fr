---
title: IHostAssemblyManager::GetNonHostStoreAssemblies, méthode
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetNonHostStoreAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type:
- apiref
ms.openlocfilehash: 0dc2f625da7f4e37583f198c8d6dba86f6dcdb10
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805065"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="3275d-102">IHostAssemblyManager::GetNonHostStoreAssemblies, méthode</span><span class="sxs-lookup"><span data-stu-id="3275d-102">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>
<span data-ttu-id="3275d-103">Obtient un pointeur d’interface vers un [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) qui représente la liste des assemblys que l’hôte attend que le Common Language Runtime (CLR) se charge.</span><span class="sxs-lookup"><span data-stu-id="3275d-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3275d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3275d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3275d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3275d-105">Parameters</span></span>  
 `ppReferenceList`  
 <span data-ttu-id="3275d-106">à Pointeur vers l’adresse d’un `ICLRAssemblyReferenceList` qui contient une liste de références aux assemblys que l’hôte attend que le CLR se charge.</span><span class="sxs-lookup"><span data-stu-id="3275d-106">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3275d-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3275d-107">Return Value</span></span>  
  
|<span data-ttu-id="3275d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3275d-108">HRESULT</span></span>|<span data-ttu-id="3275d-109">Description</span><span class="sxs-lookup"><span data-stu-id="3275d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3275d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3275d-110">S_OK</span></span>|<span data-ttu-id="3275d-111">`GetNonHostStoreAssemblies`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="3275d-111">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="3275d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3275d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3275d-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="3275d-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3275d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3275d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3275d-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="3275d-115">The call timed out.</span></span>|  
|<span data-ttu-id="3275d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3275d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3275d-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="3275d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3275d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3275d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3275d-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="3275d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3275d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3275d-120">E_FAIL</span></span>|<span data-ttu-id="3275d-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="3275d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3275d-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="3275d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3275d-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3275d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3275d-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3275d-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="3275d-125">Mémoire disponible insuffisante pour créer la liste des références pour le demandé `ICLRAssemblyReferenceList` .</span><span class="sxs-lookup"><span data-stu-id="3275d-125">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3275d-126">Notes</span><span class="sxs-lookup"><span data-stu-id="3275d-126">Remarks</span></span>  
 <span data-ttu-id="3275d-127">Le CLR résout les références à l’aide de l’ensemble d’instructions suivant :</span><span class="sxs-lookup"><span data-stu-id="3275d-127">The CLR resolves references using the following set of guidelines:</span></span>  
  
- <span data-ttu-id="3275d-128">Tout d’abord, il consulte la liste des références d’assembly retournées par `GetNonHostStoreAssemblies` .</span><span class="sxs-lookup"><span data-stu-id="3275d-128">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
- <span data-ttu-id="3275d-129">Si l’assembly apparaît dans la liste, le CLR s’y lie normalement.</span><span class="sxs-lookup"><span data-stu-id="3275d-129">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
- <span data-ttu-id="3275d-130">Si l’assembly n’apparaît pas dans la liste et que l’hôte a fourni une implémentation de [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), le CLR appelle [IHostAssemblyStore ::P rovideassembly](ihostassemblystore-provideassembly-method.md) pour permettre à l’hôte de fournir l’assembly auquel effectuer la liaison.</span><span class="sxs-lookup"><span data-stu-id="3275d-130">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
- <span data-ttu-id="3275d-131">Dans le cas contraire, le CLR ne peut pas être lié à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="3275d-131">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="3275d-132">Si l’hôte définit `ppReferenceList` sur la valeur null, le CLR commence par sonder le global assembly cache, appelle `ProvideAssembly` , puis sonde la base de l’application pour résoudre une référence d’assembly.</span><span class="sxs-lookup"><span data-stu-id="3275d-132">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3275d-133">Lors de l’initialisation, le CLR `GetNonHostStoreAssemblies` n’appelle qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="3275d-133">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="3275d-134">La méthode n’est pas appelée à nouveau.</span><span class="sxs-lookup"><span data-stu-id="3275d-134">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3275d-135">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3275d-135">Requirements</span></span>  
 <span data-ttu-id="3275d-136">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3275d-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3275d-137">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3275d-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3275d-138">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3275d-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3275d-139">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3275d-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3275d-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3275d-140">See also</span></span>

- [<span data-ttu-id="3275d-141">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="3275d-141">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="3275d-142">IHostAssemblyManager, interface</span><span class="sxs-lookup"><span data-stu-id="3275d-142">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="3275d-143">IHostAssemblyStore, interface</span><span class="sxs-lookup"><span data-stu-id="3275d-143">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
