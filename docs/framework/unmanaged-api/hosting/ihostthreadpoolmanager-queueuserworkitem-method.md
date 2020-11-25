---
title: IHostThreadPoolManager::QueueUserWorkItem, méthode
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.QueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::QueueUserWorkItem
helpviewer_keywords:
- IHostThreadPoolManager::QueueUserWorkItem method [.NET Framework hosting]
- QueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 41602053-8670-4827-9d61-cbfcba509b9c
topic_type:
- apiref
ms.openlocfilehash: 4537d367518dd80b2559f8ca058684e234ff7a91
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730745"
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a><span data-ttu-id="545d5-102">IHostThreadPoolManager::QueueUserWorkItem, méthode</span><span class="sxs-lookup"><span data-stu-id="545d5-102">IHostThreadPoolManager::QueueUserWorkItem Method</span></span>

<span data-ttu-id="545d5-103">Met en file d’attente une fonction pour l’exécution et spécifie un objet contenant les données à utiliser par cette fonction.</span><span class="sxs-lookup"><span data-stu-id="545d5-103">Queues a function for execution, and specifies an object containing data to be used by that function.</span></span> <span data-ttu-id="545d5-104">La fonction s’exécute lorsqu’un thread devient disponible.</span><span class="sxs-lookup"><span data-stu-id="545d5-104">The function executes when a thread becomes available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="545d5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="545d5-105">Syntax</span></span>  
  
```cpp  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="545d5-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="545d5-106">Parameters</span></span>  

 `Function`  
 <span data-ttu-id="545d5-107">dans Pointeur de fonction qui représente la fonction à exécuter.</span><span class="sxs-lookup"><span data-stu-id="545d5-107">[in] A function pointer that represents the function to execute.</span></span>  
  
 `Context`  
 <span data-ttu-id="545d5-108">dans Objet qui contient les données à utiliser par `Function` .</span><span class="sxs-lookup"><span data-stu-id="545d5-108">[in] An object that contains data to be used by `Function`.</span></span>  
  
 `Flags`  
 <span data-ttu-id="545d5-109">dans L’une des valeurs d’indicateurs, telle que définie pour la `QueueUserWorkItem` méthode Win32, qui contrôle l’exécution.</span><span class="sxs-lookup"><span data-stu-id="545d5-109">[in] One of the flags values, as defined for the Win32 `QueueUserWorkItem` method, that control execution.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="545d5-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="545d5-110">Return Value</span></span>  
  
|<span data-ttu-id="545d5-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="545d5-111">HRESULT</span></span>|<span data-ttu-id="545d5-112">Description</span><span class="sxs-lookup"><span data-stu-id="545d5-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="545d5-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="545d5-113">S_OK</span></span>|<span data-ttu-id="545d5-114">`QueueUserWorkItem` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="545d5-114">`QueueUserWorkItem` returned successfully.</span></span>|  
|<span data-ttu-id="545d5-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="545d5-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="545d5-116">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="545d5-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="545d5-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="545d5-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="545d5-118">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="545d5-118">The call timed out.</span></span>|  
|<span data-ttu-id="545d5-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="545d5-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="545d5-120">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="545d5-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="545d5-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="545d5-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="545d5-122">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="545d5-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="545d5-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="545d5-123">E_FAIL</span></span>|<span data-ttu-id="545d5-124">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="545d5-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="545d5-125">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="545d5-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="545d5-126">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="545d5-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="545d5-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="545d5-127">Remarks</span></span>  

 <span data-ttu-id="545d5-128">`QueueUserWorkItem` met en file d’attente un élément de travail vers un thread de travail dans le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="545d5-128">`QueueUserWorkItem` queues a work item to a worker thread in the thread pool.</span></span> <span data-ttu-id="545d5-129">Sa signature et ses types de paramètres sont identiques à ceux de la fonction Win32 correspondante, qui porte le même nom.</span><span class="sxs-lookup"><span data-stu-id="545d5-129">Its signature and parameter types are identical to those of the corresponding Win32 function, which has the same name.</span></span> <span data-ttu-id="545d5-130">Pour plus d’informations, consultez la documentation de la plateforme Windows.</span><span class="sxs-lookup"><span data-stu-id="545d5-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="545d5-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="545d5-131">Requirements</span></span>  

 <span data-ttu-id="545d5-132">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="545d5-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="545d5-133">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="545d5-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="545d5-134">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="545d5-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="545d5-135">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="545d5-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="545d5-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="545d5-136">See also</span></span>

- <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="545d5-137">IHostThreadPoolManager, interface</span><span class="sxs-lookup"><span data-stu-id="545d5-137">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
