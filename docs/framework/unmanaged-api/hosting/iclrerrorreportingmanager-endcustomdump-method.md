---
title: ICLRErrorReportingManager::EndCustomDump, méthode
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.EndCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::EndCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::EndCustomDump method [.NET Framework hosting]
- EndCustomDump method [.NET Framework hosting]
ms.assetid: 88a5da04-8729-4108-82c4-af206a7d483e
topic_type:
- apiref
ms.openlocfilehash: feaeba15fcc4e8264f7fde57d3b268a6b583ad83
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677828"
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="e07be-102">ICLRErrorReportingManager::EndCustomDump, méthode</span><span class="sxs-lookup"><span data-stu-id="e07be-102">ICLRErrorReportingManager::EndCustomDump Method</span></span>

<span data-ttu-id="e07be-103">Supprime la configuration de vidage de la pile personnalisée spécifiée dans un appel antérieur à la méthode [ICLRErrorReportingManager :: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e07be-103">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e07be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e07be-104">Syntax</span></span>  
  
```cpp  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e07be-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e07be-105">Return Value</span></span>  
  
|<span data-ttu-id="e07be-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e07be-106">HRESULT</span></span>|<span data-ttu-id="e07be-107">Description</span><span class="sxs-lookup"><span data-stu-id="e07be-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e07be-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e07be-108">S_OK</span></span>|<span data-ttu-id="e07be-109">`EndCustomDump` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="e07be-109">`EndCustomDump` returned successfully.</span></span>|  
|<span data-ttu-id="e07be-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e07be-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e07be-111">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="e07be-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e07be-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e07be-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e07be-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="e07be-113">The call timed out.</span></span>|  
|<span data-ttu-id="e07be-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e07be-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e07be-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="e07be-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e07be-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e07be-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e07be-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="e07be-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e07be-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e07be-118">E_FAIL</span></span>|<span data-ttu-id="e07be-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e07be-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e07be-120">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e07be-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e07be-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e07be-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e07be-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="e07be-122">Remarks</span></span>  

 <span data-ttu-id="e07be-123">La `EndCustomDump` méthode efface la configuration de vidage de pile personnalisée définie par un appel antérieur à la `BeginCustomDump` méthode et libère tout état associé.</span><span class="sxs-lookup"><span data-stu-id="e07be-123">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="e07be-124">Elle doit être appelée une fois que le vidage de pile personnalisé est terminé.</span><span class="sxs-lookup"><span data-stu-id="e07be-124">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e07be-125">L’échec de l’appel `EndCustomDump` entraîne une fuite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="e07be-125">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e07be-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e07be-126">Requirements</span></span>  

 <span data-ttu-id="e07be-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e07be-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e07be-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e07be-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e07be-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e07be-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e07be-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e07be-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e07be-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e07be-131">See also</span></span>

- [<span data-ttu-id="e07be-132">CustomDumpItem, structure</span><span class="sxs-lookup"><span data-stu-id="e07be-132">CustomDumpItem Structure</span></span>](customdumpitem-structure.md)
- [<span data-ttu-id="e07be-133">ECustomDumpFlavor, énumération</span><span class="sxs-lookup"><span data-stu-id="e07be-133">ECustomDumpFlavor Enumeration</span></span>](ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="e07be-134">ICLRErrorReportingManager, interface</span><span class="sxs-lookup"><span data-stu-id="e07be-134">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
