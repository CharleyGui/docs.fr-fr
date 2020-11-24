---
title: IHostTaskManager::SetCLRTaskManager, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
ms.openlocfilehash: 23d0679599c681468caa2507518d0ae3144ac26a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669794"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="c855a-102">IHostTaskManager::SetCLRTaskManager, méthode</span><span class="sxs-lookup"><span data-stu-id="c855a-102">IHostTaskManager::SetCLRTaskManager Method</span></span>

<span data-ttu-id="c855a-103">Fournit à l’hôte un pointeur d’interface vers une instance [ICLRTaskManager](iclrtaskmanager-interface.md) implémentée par le Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="c855a-103">Provides the host with an interface pointer to an [ICLRTaskManager](iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c855a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c855a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c855a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c855a-105">Parameters</span></span>  

 `pManager`  
 <span data-ttu-id="c855a-106">dans Pointeur vers une `ICLRTaskManager` instance implémentée par le Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="c855a-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c855a-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="c855a-107">Return Value</span></span>  
  
|<span data-ttu-id="c855a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c855a-108">HRESULT</span></span>|<span data-ttu-id="c855a-109">Description</span><span class="sxs-lookup"><span data-stu-id="c855a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c855a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c855a-110">S_OK</span></span>|<span data-ttu-id="c855a-111">`SetCLRTaskManager` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="c855a-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="c855a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c855a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c855a-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="c855a-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c855a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c855a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c855a-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="c855a-115">The call timed out.</span></span>|  
|<span data-ttu-id="c855a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c855a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c855a-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="c855a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c855a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c855a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c855a-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="c855a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c855a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c855a-120">E_FAIL</span></span>|<span data-ttu-id="c855a-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="c855a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c855a-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="c855a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c855a-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c855a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c855a-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="c855a-124">Remarks</span></span>  

 <span data-ttu-id="c855a-125">Le runtime appelle `SetCLRTaskManager` pour fournir à l’hôte un pointeur d’interface vers une `ICLRTaskManager` instance.</span><span class="sxs-lookup"><span data-stu-id="c855a-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c855a-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c855a-126">Requirements</span></span>  

 <span data-ttu-id="c855a-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c855a-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c855a-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c855a-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c855a-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c855a-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c855a-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c855a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c855a-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c855a-131">See also</span></span>

- [<span data-ttu-id="c855a-132">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="c855a-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="c855a-133">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="c855a-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="c855a-134">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="c855a-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="c855a-135">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="c855a-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
