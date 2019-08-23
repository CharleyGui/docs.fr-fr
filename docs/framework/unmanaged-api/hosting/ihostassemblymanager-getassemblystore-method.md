---
title: IHostAssemblyManager::GetAssemblyStore, méthode
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62965fa928522052b6885769e02c0211ca8d3fe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937932"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="65652-102">IHostAssemblyManager::GetAssemblyStore, méthode</span><span class="sxs-lookup"><span data-stu-id="65652-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="65652-103">Obtient un pointeur d’interface vers un [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) qui représente la liste des assemblys chargés par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="65652-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65652-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65652-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65652-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="65652-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="65652-106">à Pointeur de fonction vers une `IHostAssemblyStore` instance, ou null, si l’hôte n’implémente `IHostAssemblyStore`pas.</span><span class="sxs-lookup"><span data-stu-id="65652-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65652-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="65652-107">Return Value</span></span>  
  
|<span data-ttu-id="65652-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="65652-108">HRESULT</span></span>|<span data-ttu-id="65652-109">Description</span><span class="sxs-lookup"><span data-stu-id="65652-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="65652-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="65652-110">S_OK</span></span>|<span data-ttu-id="65652-111">`GetAssemblyStore`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="65652-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="65652-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="65652-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="65652-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="65652-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="65652-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="65652-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="65652-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="65652-115">The call timed out.</span></span>|  
|<span data-ttu-id="65652-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="65652-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="65652-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="65652-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="65652-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="65652-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="65652-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="65652-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="65652-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="65652-120">E_FAIL</span></span>|<span data-ttu-id="65652-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="65652-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="65652-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="65652-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="65652-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="65652-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="65652-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="65652-124">E_NOINTERFACE</span></span>|<span data-ttu-id="65652-125">L’hôte ne fournit pas d’implémentation de `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="65652-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65652-126">Notes</span><span class="sxs-lookup"><span data-stu-id="65652-126">Remarks</span></span>  
 <span data-ttu-id="65652-127">`IHostAssemblyStore`fournit des méthodes qui permettent à un hôte de se lier à des assemblys et des modules indépendamment du CLR.</span><span class="sxs-lookup"><span data-stu-id="65652-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="65652-128">Les hôtes fournissent généralement des magasins d’assemblys pour permettre le chargement d’assemblys à partir de formats autres que le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="65652-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="65652-129">Si l’hôte n’implémente `IHostAssemblyStore`pas `GetAssemblyStore` , doit retourner une valeur HRESULT d' `ppAssemblyStore` E_NOINTERFACE et doit avoir la valeur null.</span><span class="sxs-lookup"><span data-stu-id="65652-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65652-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="65652-130">Requirements</span></span>  
 <span data-ttu-id="65652-131">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65652-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65652-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="65652-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65652-133">**Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="65652-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65652-134">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65652-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65652-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65652-135">See also</span></span>

- [<span data-ttu-id="65652-136">IHostAssemblyManager, interface</span><span class="sxs-lookup"><span data-stu-id="65652-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="65652-137">IHostAssemblyStore, interface</span><span class="sxs-lookup"><span data-stu-id="65652-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
