---
title: IHostIoCompletionManager::GetHostOverlappedSize, méthode
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetHostOverlappedSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type:
- apiref
ms.openlocfilehash: 612a5f08982b1db5c940a7cca93166480b21e612
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724856"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="41d72-102">IHostIoCompletionManager::GetHostOverlappedSize, méthode</span><span class="sxs-lookup"><span data-stu-id="41d72-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>

<span data-ttu-id="41d72-103">Obtient la taille des données personnalisées que l’hôte envisage d’ajouter aux demandes d’e/s.</span><span class="sxs-lookup"><span data-stu-id="41d72-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41d72-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41d72-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41d72-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="41d72-105">Parameters</span></span>  

 `pcbSize`  
 <span data-ttu-id="41d72-106">à Pointeur vers le nombre d’octets que le common language runtime (CLR) doit allouer en plus de la taille de l' `OVERLAPPED` objet Win32.</span><span class="sxs-lookup"><span data-stu-id="41d72-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41d72-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="41d72-107">Return Value</span></span>  
  
|<span data-ttu-id="41d72-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="41d72-108">HRESULT</span></span>|<span data-ttu-id="41d72-109">Description</span><span class="sxs-lookup"><span data-stu-id="41d72-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41d72-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="41d72-110">S_OK</span></span>|<span data-ttu-id="41d72-111">`GetHostOverlappedSize` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="41d72-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="41d72-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="41d72-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="41d72-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="41d72-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="41d72-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="41d72-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="41d72-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="41d72-115">The call timed out.</span></span>|  
|<span data-ttu-id="41d72-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="41d72-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="41d72-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="41d72-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="41d72-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="41d72-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="41d72-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="41d72-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="41d72-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="41d72-120">E_FAIL</span></span>|<span data-ttu-id="41d72-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="41d72-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="41d72-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="41d72-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="41d72-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="41d72-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41d72-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="41d72-124">Remarks</span></span>  

 <span data-ttu-id="41d72-125">Tous les appels d’e/s asynchrones aux API de la plateforme Windows acceptent un `OVERLAPPED` objet Win32, qui fournit des informations telles que la position du pointeur de fichier.</span><span class="sxs-lookup"><span data-stu-id="41d72-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="41d72-126">Pour conserver l’État, les applications qui effectuent des appels d’e/s asynchrones ajoutent généralement des données personnalisées à la structure.</span><span class="sxs-lookup"><span data-stu-id="41d72-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="41d72-127">`GetHostOverlappedSize` et [IHostIoCompletionManager :: InitializeHostOverlapped,](ihostiocompletionmanager-initializehostoverlapped-method.md) offrent une opportunité pour l’hôte d’inclure ces données personnalisées.</span><span class="sxs-lookup"><span data-stu-id="41d72-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="41d72-128">Le CLR appelle la `GetHostOverlappedSize` méthode pour déterminer la taille des données personnalisées que l’hôte envisage d’ajouter à l' `OVERLAPPED` objet.</span><span class="sxs-lookup"><span data-stu-id="41d72-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41d72-129">`GetHostOverlappedSize` est appelée une seule fois.</span><span class="sxs-lookup"><span data-stu-id="41d72-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="41d72-130">Les données personnalisées de l’hôte doivent avoir la même taille pour chaque demande d’e/s.</span><span class="sxs-lookup"><span data-stu-id="41d72-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="41d72-131">La taille de l' `OVERLAPPED` objet lui-même n’est pas incluse dans la valeur de `pcbSize` .</span><span class="sxs-lookup"><span data-stu-id="41d72-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="41d72-132">Pour plus d’informations sur la `OVERLAPPED` structure, consultez la documentation de la plateforme Windows.</span><span class="sxs-lookup"><span data-stu-id="41d72-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41d72-133">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="41d72-133">Requirements</span></span>  

 <span data-ttu-id="41d72-134">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41d72-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41d72-135">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="41d72-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41d72-136">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="41d72-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41d72-137">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41d72-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41d72-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41d72-138">See also</span></span>

- <xref:System.Threading.NativeOverlapped>
- [<span data-ttu-id="41d72-139">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="41d72-139">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="41d72-140">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="41d72-140">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
