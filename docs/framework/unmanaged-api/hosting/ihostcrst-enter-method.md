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
ms.openlocfilehash: 79afaac4dce1c4baa9802d81af90c425f5de7a08
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804917"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="048a8-102">IHostCrst::Enter, méthode</span><span class="sxs-lookup"><span data-stu-id="048a8-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="048a8-103">Entre dans la section critique qui est représentée par l’instance [IHostCrst](ihostcrst-interface.md) actuelle.</span><span class="sxs-lookup"><span data-stu-id="048a8-103">Enters the critical section that is represented by the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="048a8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="048a8-104">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="048a8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="048a8-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="048a8-106">dans L’une des valeurs [WAIT_OPTION](wait-option-enumeration.md) , indiquant l’action que l’hôte doit effectuer si l’opération bloque.</span><span class="sxs-lookup"><span data-stu-id="048a8-106">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="048a8-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="048a8-107">Return Value</span></span>  
  
|<span data-ttu-id="048a8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="048a8-108">HRESULT</span></span>|<span data-ttu-id="048a8-109">Description</span><span class="sxs-lookup"><span data-stu-id="048a8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="048a8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="048a8-110">S_OK</span></span>|<span data-ttu-id="048a8-111">`Enter`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="048a8-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="048a8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="048a8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="048a8-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="048a8-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="048a8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="048a8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="048a8-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="048a8-115">The call timed out.</span></span>|  
|<span data-ttu-id="048a8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="048a8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="048a8-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="048a8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="048a8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="048a8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="048a8-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="048a8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="048a8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="048a8-120">E_FAIL</span></span>|<span data-ttu-id="048a8-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="048a8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="048a8-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="048a8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="048a8-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="048a8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="048a8-124">Notes</span><span class="sxs-lookup"><span data-stu-id="048a8-124">Remarks</span></span>  
 <span data-ttu-id="048a8-125">`Enter`reflète la `EnterCriticalSection` fonction Win32.</span><span class="sxs-lookup"><span data-stu-id="048a8-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="048a8-126">Cette méthode n’est pas retournée tant que la section critique n’est pas entrée.</span><span class="sxs-lookup"><span data-stu-id="048a8-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="048a8-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="048a8-127">Requirements</span></span>  
 <span data-ttu-id="048a8-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="048a8-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="048a8-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="048a8-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="048a8-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="048a8-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="048a8-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="048a8-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="048a8-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="048a8-132">See also</span></span>

- [<span data-ttu-id="048a8-133">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="048a8-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="048a8-134">IHostCrst, interface</span><span class="sxs-lookup"><span data-stu-id="048a8-134">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="048a8-135">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="048a8-135">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
