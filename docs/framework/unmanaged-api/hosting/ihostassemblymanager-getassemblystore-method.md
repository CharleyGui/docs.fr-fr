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
ms.openlocfilehash: 936ea068f3cc5567a00af5f2bdd5f3d9cd52bc81
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681182"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="e1eaf-102">IHostAssemblyManager::GetAssemblyStore, méthode</span><span class="sxs-lookup"><span data-stu-id="e1eaf-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>

<span data-ttu-id="e1eaf-103">Obtient un pointeur d’interface vers un [IHostAssemblyStore](ihostassemblystore-interface.md) qui représente la liste des assemblys chargés par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="e1eaf-103">Gets an interface pointer to an [IHostAssemblyStore](ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1eaf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1eaf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1eaf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e1eaf-105">Parameters</span></span>  

 `ppAssemblyStore`  
 <span data-ttu-id="e1eaf-106">à Pointeur de fonction vers une `IHostAssemblyStore` instance, ou null, si l’hôte n’implémente pas `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="e1eaf-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1eaf-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="e1eaf-107">Return Value</span></span>  
  
|<span data-ttu-id="e1eaf-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e1eaf-108">HRESULT</span></span>|<span data-ttu-id="e1eaf-109">Description</span><span class="sxs-lookup"><span data-stu-id="e1eaf-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e1eaf-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e1eaf-110">S_OK</span></span>|<span data-ttu-id="e1eaf-111">`GetAssemblyStore` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="e1eaf-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="e1eaf-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e1eaf-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e1eaf-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="e1eaf-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e1eaf-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e1eaf-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e1eaf-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="e1eaf-115">The call timed out.</span></span>|  
|<span data-ttu-id="e1eaf-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e1eaf-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e1eaf-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="e1eaf-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e1eaf-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e1eaf-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e1eaf-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="e1eaf-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e1eaf-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e1eaf-120">E_FAIL</span></span>|<span data-ttu-id="e1eaf-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e1eaf-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e1eaf-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e1eaf-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e1eaf-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e1eaf-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e1eaf-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="e1eaf-124">E_NOINTERFACE</span></span>|<span data-ttu-id="e1eaf-125">L’hôte ne fournit pas d’implémentation de `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="e1eaf-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1eaf-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="e1eaf-126">Remarks</span></span>  

 <span data-ttu-id="e1eaf-127">`IHostAssemblyStore` fournit des méthodes qui permettent à un hôte de se lier à des assemblys et des modules indépendamment du CLR.</span><span class="sxs-lookup"><span data-stu-id="e1eaf-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="e1eaf-128">Les hôtes fournissent généralement des magasins d’assemblys pour permettre le chargement d’assemblys à partir de formats autres que le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="e1eaf-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1eaf-129">Si l’hôte n’implémente pas `IHostAssemblyStore` , `GetAssemblyStore` doit retourner une valeur HRESULT de E_NOINTERFACE et doit avoir la valeur `ppAssemblyStore` null.</span><span class="sxs-lookup"><span data-stu-id="e1eaf-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1eaf-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e1eaf-130">Requirements</span></span>  

 <span data-ttu-id="e1eaf-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1eaf-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1eaf-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e1eaf-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e1eaf-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e1eaf-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1eaf-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1eaf-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1eaf-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1eaf-135">See also</span></span>

- [<span data-ttu-id="e1eaf-136">IHostAssemblyManager, interface</span><span class="sxs-lookup"><span data-stu-id="e1eaf-136">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="e1eaf-137">IHostAssemblyStore, interface</span><span class="sxs-lookup"><span data-stu-id="e1eaf-137">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
