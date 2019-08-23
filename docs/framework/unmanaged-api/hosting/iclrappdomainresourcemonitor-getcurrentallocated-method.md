---
title: ICLRAppDomainResourceMonitor::GetCurrentAllocated, méthode
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentAllocated
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentAllocated
helpviewer_keywords:
- GetCurrentAllocated method [.NET Framework hosting]
- ICLRAppDomainResourceMonitor::GetCurrentAllocated method [.NET Framework hosting]
ms.assetid: 7bab209c-efd4-44c2-af30-61abab0ae2fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d02478c2421823ce2acb533d2abea2ea8b13c74
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950288"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="975c2-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated, méthode</span><span class="sxs-lookup"><span data-stu-id="975c2-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="975c2-103">Obtient la taille totale, en octets, de toutes les allocations de mémoire effectuées par le domaine d’application depuis sa création, sans soustraire la mémoire qui a été récupérée par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="975c2-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="975c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="975c2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
## <a name="parameters"></a><span data-ttu-id="975c2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="975c2-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="975c2-106">dans ID du domaine d’application demandé.</span><span class="sxs-lookup"><span data-stu-id="975c2-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="975c2-107">à Pointeur vers la taille totale de toutes les allocations de mémoire.</span><span class="sxs-lookup"><span data-stu-id="975c2-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="975c2-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="975c2-108">Return Value</span></span>  
 <span data-ttu-id="975c2-109">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="975c2-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="975c2-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="975c2-110">HRESULT</span></span>|<span data-ttu-id="975c2-111">Description</span><span class="sxs-lookup"><span data-stu-id="975c2-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="975c2-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="975c2-112">S_OK</span></span>|<span data-ttu-id="975c2-113">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="975c2-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="975c2-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="975c2-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="975c2-115">Le domaine d’application a été déchargé ou n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="975c2-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="975c2-116">Notes</span><span class="sxs-lookup"><span data-stu-id="975c2-116">Remarks</span></span>  
 <span data-ttu-id="975c2-117">Cette méthode est l’équivalent non managé de la propriété managée <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="975c2-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="975c2-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="975c2-118">Requirements</span></span>  
 <span data-ttu-id="975c2-119">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="975c2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="975c2-120">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="975c2-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="975c2-121">**Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="975c2-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="975c2-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="975c2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="975c2-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="975c2-123">See also</span></span>

- [<span data-ttu-id="975c2-124">ICLRAppDomainResourceMonitor, interface</span><span class="sxs-lookup"><span data-stu-id="975c2-124">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="975c2-125">Analyse de ressource de domaine d'application</span><span class="sxs-lookup"><span data-stu-id="975c2-125">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="975c2-126">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="975c2-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="975c2-127">Hébergement</span><span class="sxs-lookup"><span data-stu-id="975c2-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
