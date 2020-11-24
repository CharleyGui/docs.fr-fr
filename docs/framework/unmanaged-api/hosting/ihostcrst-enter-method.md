---
title: IHostCrst::Enter, méthode
ms.date: 03/30/2017
api_name:
- IHostCrst.Enter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Enter
helpviewer_keywords:
- Enter method [.NET Framework hosting]
- IHostCrst::Enter method [.NET Framework hosting]
ms.assetid: 100dd7eb-7053-4295-9bb3-32ba47f6ec79
topic_type:
- apiref
ms.openlocfilehash: a5c2646d7c9dbf8a7aea4a7fb9bd0a6b8c1d5d66
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680545"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="6d796-102">IHostCrst::Enter, méthode</span><span class="sxs-lookup"><span data-stu-id="6d796-102">IHostCrst::Enter Method</span></span>

<span data-ttu-id="6d796-103">Entre dans la section critique qui est représentée par l’instance [IHostCrst](ihostcrst-interface.md) actuelle.</span><span class="sxs-lookup"><span data-stu-id="6d796-103">Enters the critical section that is represented by the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d796-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d796-104">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d796-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6d796-105">Parameters</span></span>  

 `option`  
 <span data-ttu-id="6d796-106">dans L’une des valeurs [WAIT_OPTION](wait-option-enumeration.md) , indiquant l’action que l’hôte doit effectuer si l’opération bloque.</span><span class="sxs-lookup"><span data-stu-id="6d796-106">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d796-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="6d796-107">Return Value</span></span>  
  
|<span data-ttu-id="6d796-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6d796-108">HRESULT</span></span>|<span data-ttu-id="6d796-109">Description</span><span class="sxs-lookup"><span data-stu-id="6d796-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6d796-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6d796-110">S_OK</span></span>|<span data-ttu-id="6d796-111">`Enter` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="6d796-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="6d796-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6d796-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6d796-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="6d796-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6d796-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6d796-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6d796-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="6d796-115">The call timed out.</span></span>|  
|<span data-ttu-id="6d796-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6d796-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6d796-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="6d796-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6d796-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6d796-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6d796-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="6d796-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6d796-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6d796-120">E_FAIL</span></span>|<span data-ttu-id="6d796-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="6d796-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6d796-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="6d796-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6d796-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6d796-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d796-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="6d796-124">Remarks</span></span>  

 <span data-ttu-id="6d796-125">`Enter` reflète la `EnterCriticalSection` fonction Win32.</span><span class="sxs-lookup"><span data-stu-id="6d796-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d796-126">Cette méthode n’est pas retournée tant que la section critique n’est pas entrée.</span><span class="sxs-lookup"><span data-stu-id="6d796-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d796-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6d796-127">Requirements</span></span>  

 <span data-ttu-id="6d796-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d796-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d796-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6d796-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6d796-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6d796-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6d796-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d796-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d796-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d796-132">See also</span></span>

- [<span data-ttu-id="6d796-133">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="6d796-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="6d796-134">IHostCrst, interface</span><span class="sxs-lookup"><span data-stu-id="6d796-134">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="6d796-135">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="6d796-135">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
