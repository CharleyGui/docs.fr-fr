---
title: ICLRErrorReportingManager::BeginCustomDump, méthode
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.BeginCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type:
- apiref
ms.openlocfilehash: 4c83ffaf920abe005ba987e0a744e13aa0d3c016
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615668"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="f99c9-102">ICLRErrorReportingManager::BeginCustomDump, méthode</span><span class="sxs-lookup"><span data-stu-id="f99c9-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="f99c9-103">Spécifie la configuration des dumps de tas personnalisés pour le rapport d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="f99c9-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f99c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f99c9-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f99c9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f99c9-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="f99c9-106">dans Valeur [ECustomDumpFlavor,](ecustomdumpflavor-enumeration.md) qui indique le type de dump du tas sur lequel générer le dump du tas personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f99c9-106">[in] A [ECustomDumpFlavor](ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="f99c9-107">dans Longueur du `items` tableau.</span><span class="sxs-lookup"><span data-stu-id="f99c9-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="f99c9-108">Si `dwFlavor` n’est pas DUMP_FLAVOR_Mini, `dwNumItems` doit être égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="f99c9-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="f99c9-109">dans Tableau d’instances [CustomDumpItem](customdumpitem-structure.md) , spécifiant les éléments à ajouter au mini-vidage.</span><span class="sxs-lookup"><span data-stu-id="f99c9-109">[in] An array of [CustomDumpItem](customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="f99c9-110">Si `dwFlavor` n’est pas DUMP_FLAVOR_Mini, `items` doit avoir la valeur null.</span><span class="sxs-lookup"><span data-stu-id="f99c9-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="f99c9-111">[in] Réservé pour une future utilisation.</span><span class="sxs-lookup"><span data-stu-id="f99c9-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f99c9-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f99c9-112">Return Value</span></span>  
  
|<span data-ttu-id="f99c9-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f99c9-113">HRESULT</span></span>|<span data-ttu-id="f99c9-114">Description</span><span class="sxs-lookup"><span data-stu-id="f99c9-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f99c9-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="f99c9-115">S_OK</span></span>|<span data-ttu-id="f99c9-116">Retour réussi de la méthode.</span><span class="sxs-lookup"><span data-stu-id="f99c9-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="f99c9-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f99c9-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f99c9-118">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="f99c9-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f99c9-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f99c9-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f99c9-120">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="f99c9-120">The call timed out.</span></span>|  
|<span data-ttu-id="f99c9-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f99c9-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f99c9-122">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="f99c9-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f99c9-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f99c9-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f99c9-124">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="f99c9-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f99c9-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f99c9-125">E_FAIL</span></span>|<span data-ttu-id="f99c9-126">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="f99c9-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f99c9-127">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="f99c9-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f99c9-128">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f99c9-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f99c9-129">Notes</span><span class="sxs-lookup"><span data-stu-id="f99c9-129">Remarks</span></span>  
 <span data-ttu-id="f99c9-130">La `BeginCustomDump` méthode définit une configuration de vidage de tas personnalisée.</span><span class="sxs-lookup"><span data-stu-id="f99c9-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="f99c9-131">La méthode [EndCustomDump](iclrerrorreportingmanager-endcustomdump-method.md) efface la configuration du dump du tas personnalisé et libère tous les États associés.</span><span class="sxs-lookup"><span data-stu-id="f99c9-131">The [EndCustomDump](iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="f99c9-132">Elle doit être appelée une fois que le dump du tas personnalisé est terminé.</span><span class="sxs-lookup"><span data-stu-id="f99c9-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f99c9-133">L’échec de l’appel `EndCustomDump` entraîne une fuite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="f99c9-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f99c9-134">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="f99c9-134">Requirements</span></span>  
 <span data-ttu-id="f99c9-135">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f99c9-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f99c9-136">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f99c9-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f99c9-137">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f99c9-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f99c9-138">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f99c9-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f99c9-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f99c9-139">See also</span></span>

- [<span data-ttu-id="f99c9-140">CustomDumpItem, structure</span><span class="sxs-lookup"><span data-stu-id="f99c9-140">CustomDumpItem Structure</span></span>](customdumpitem-structure.md)
- [<span data-ttu-id="f99c9-141">ECustomDumpFlavor, énumération</span><span class="sxs-lookup"><span data-stu-id="f99c9-141">ECustomDumpFlavor Enumeration</span></span>](ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="f99c9-142">ICLRErrorReportingManager, interface</span><span class="sxs-lookup"><span data-stu-id="f99c9-142">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
