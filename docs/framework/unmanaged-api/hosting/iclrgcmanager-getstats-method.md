---
title: ICLRGCManager::GetStats, méthode
ms.date: 03/30/2017
api_name:
- ICLRGCManager.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type:
- apiref
ms.openlocfilehash: 8622920a81f4b469361ffa879f7a4eeda697cab9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504223"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="57a7d-102">ICLRGCManager::GetStats, méthode</span><span class="sxs-lookup"><span data-stu-id="57a7d-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="57a7d-103">Obtient un jeu de statistiques actuelles sur le système de garbage collection du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="57a7d-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57a7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57a7d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57a7d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="57a7d-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="57a7d-106">[in, out] Instance [COR_GC_STATS](cor-gc-stats-structure.md) qui contient les statistiques demandées.</span><span class="sxs-lookup"><span data-stu-id="57a7d-106">[in, out] A [COR_GC_STATS](cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57a7d-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="57a7d-107">Return Value</span></span>  
  
|<span data-ttu-id="57a7d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57a7d-108">HRESULT</span></span>|<span data-ttu-id="57a7d-109">Description</span><span class="sxs-lookup"><span data-stu-id="57a7d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57a7d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="57a7d-110">S_OK</span></span>|<span data-ttu-id="57a7d-111">`GetStats`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="57a7d-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="57a7d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57a7d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57a7d-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="57a7d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="57a7d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="57a7d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="57a7d-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="57a7d-115">The call timed out.</span></span>|  
|<span data-ttu-id="57a7d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="57a7d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="57a7d-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="57a7d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="57a7d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="57a7d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="57a7d-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="57a7d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="57a7d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57a7d-120">E_FAIL</span></span>|<span data-ttu-id="57a7d-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="57a7d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="57a7d-122">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="57a7d-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="57a7d-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="57a7d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57a7d-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="57a7d-124">Remarks</span></span>  
 <span data-ttu-id="57a7d-125">Le CLR calcule et retourne uniquement les statistiques qui sont spécifiées par le `Flags` champ de `pStats` .</span><span class="sxs-lookup"><span data-stu-id="57a7d-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="57a7d-126">Définissez le `Flags` champ sur une ou plusieurs valeurs de l’énumération [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) pour spécifier les statistiques de la structure [COR_GC_STATS](cor-gc-stats-structure.md) à définir.</span><span class="sxs-lookup"><span data-stu-id="57a7d-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="57a7d-127">Voici un exemple d’utilisation :</span><span class="sxs-lookup"><span data-stu-id="57a7d-127">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="57a7d-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="57a7d-128">Requirements</span></span>  
 <span data-ttu-id="57a7d-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57a7d-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57a7d-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="57a7d-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57a7d-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="57a7d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57a7d-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57a7d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57a7d-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57a7d-133">See also</span></span>

- [<span data-ttu-id="57a7d-134">Gestion automatique de la mémoire</span><span class="sxs-lookup"><span data-stu-id="57a7d-134">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="57a7d-135">COR_GC_STATS, structure</span><span class="sxs-lookup"><span data-stu-id="57a7d-135">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="57a7d-136">COR_GC_STAT_TYPES (énumération)</span><span class="sxs-lookup"><span data-stu-id="57a7d-136">COR_GC_STAT_TYPES Enumeration</span></span>](cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="57a7d-137">Garbage collection</span><span class="sxs-lookup"><span data-stu-id="57a7d-137">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="57a7d-138">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="57a7d-138">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="57a7d-139">ICLRGCManager, interface</span><span class="sxs-lookup"><span data-stu-id="57a7d-139">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="57a7d-140">Interfaces d'hébergement du CLR</span><span class="sxs-lookup"><span data-stu-id="57a7d-140">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="57a7d-141">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="57a7d-141">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="57a7d-142">Hosting</span><span class="sxs-lookup"><span data-stu-id="57a7d-142">Hosting</span></span>](index.md)
