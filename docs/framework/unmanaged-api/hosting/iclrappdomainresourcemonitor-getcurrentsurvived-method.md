---
title: ICLRAppDomainResourceMonitor::GetCurrentSurvived, méthode
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf285b6e1f703c8776937fa33c7ab5801f04f80f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950161"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a><span data-ttu-id="e5431-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived, méthode</span><span class="sxs-lookup"><span data-stu-id="e5431-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Method</span></span>
<span data-ttu-id="e5431-103">Obtient le nombre d’octets qui ont survécu au dernier garbage collection de blocage complet et qui sont référencés par le domaine d’application actuel.</span><span class="sxs-lookup"><span data-stu-id="e5431-103">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5431-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5431-104">Syntax</span></span>  
  
```cpp  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5431-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e5431-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="e5431-106">dans ID du domaine d’application demandé.</span><span class="sxs-lookup"><span data-stu-id="e5431-106">[in] The ID of the requested application domain.</span></span>  
  
 `pAppDomainBytesSurvived`  
 <span data-ttu-id="e5431-107">à Pointeur vers le nombre d’octets qui ont survécu après le dernier garbage collection détenu par ce domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="e5431-107">[out] A pointer to the number of bytes that survived after the last garbage collection that are held by this application domain.</span></span> <span data-ttu-id="e5431-108">Après une collection complète, ce nombre est exact et complet.</span><span class="sxs-lookup"><span data-stu-id="e5431-108">After a full collection, this number is accurate and complete.</span></span> <span data-ttu-id="e5431-109">Après une collection éphémère, ce nombre est potentiellement incomplet.</span><span class="sxs-lookup"><span data-stu-id="e5431-109">After an ephemeral collection, this number is potentially incomplete.</span></span> <span data-ttu-id="e5431-110">Ce paramètre peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="e5431-110">This parameter can be `null`.</span></span>  
  
 `pRuntimeBytesSurvived`  
 <span data-ttu-id="e5431-111">à Pointeur vers le nombre total d’octets qui ont survécu à partir du dernier garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e5431-111">[out] A pointer to the total number of bytes that survived from the last garbage collection.</span></span> <span data-ttu-id="e5431-112">Après une collection complète, ce nombre représente le nombre d’octets conservés dans les tas managés.</span><span class="sxs-lookup"><span data-stu-id="e5431-112">After a full collection, this number represents the number of the bytes that are held in managed heaps.</span></span> <span data-ttu-id="e5431-113">Après une collection éphémère, ce nombre représente le nombre d’octets maintenus actifs dans les générations éphémères.</span><span class="sxs-lookup"><span data-stu-id="e5431-113">After an ephemeral collection, this number represents the number of bytes that are held live in ephemeral generations.</span></span> <span data-ttu-id="e5431-114">Ce paramètre peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="e5431-114">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5431-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e5431-115">Return Value</span></span>  
 <span data-ttu-id="e5431-116">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="e5431-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e5431-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e5431-117">HRESULT</span></span>|<span data-ttu-id="e5431-118">Description</span><span class="sxs-lookup"><span data-stu-id="e5431-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e5431-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="e5431-119">S_OK</span></span>|<span data-ttu-id="e5431-120">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="e5431-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="e5431-121">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="e5431-121">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="e5431-122">Le domaine d’application a été déchargé ou n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="e5431-122">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5431-123">Notes</span><span class="sxs-lookup"><span data-stu-id="e5431-123">Remarks</span></span>  
 <span data-ttu-id="e5431-124">Les statistiques sont mises à jour uniquement après un garbage collection de blocage complet; autrement dit, une collection qui comprend toutes les générations et qui arrête l’application pendant que la collection se produit.</span><span class="sxs-lookup"><span data-stu-id="e5431-124">Statistics are updated only after a full, blocking garbage collection; that is, a collection that includes all generations and that stops the application while collection occurs.</span></span> <span data-ttu-id="e5431-125">Par exemple, la <xref:System.GC.Collect?displayProperty=nameWithType> surcharge de méthode effectue une collection bloquante complète.</span><span class="sxs-lookup"><span data-stu-id="e5431-125">For example, the <xref:System.GC.Collect?displayProperty=nameWithType> method overload performs a full, blocking collection.</span></span> <span data-ttu-id="e5431-126">Garbage collection simultanée se produit en arrière-plan et ne bloque pas l’application.</span><span class="sxs-lookup"><span data-stu-id="e5431-126">Concurrent garbage collection occurs in the background and does not block the application.</span></span>  
  
 <span data-ttu-id="e5431-127">La `GetCurrentSurvived` méthode est l’équivalent non managé de la propriété managée <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e5431-127">The `GetCurrentSurvived` method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5431-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e5431-128">Requirements</span></span>  
 <span data-ttu-id="e5431-129">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5431-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5431-130">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e5431-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e5431-131">**Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e5431-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e5431-132">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5431-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5431-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5431-133">See also</span></span>

- [<span data-ttu-id="e5431-134">ICLRAppDomainResourceMonitor, interface</span><span class="sxs-lookup"><span data-stu-id="e5431-134">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="e5431-135">Analyse de ressource de domaine d'application</span><span class="sxs-lookup"><span data-stu-id="e5431-135">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="e5431-136">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="e5431-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="e5431-137">Hébergement</span><span class="sxs-lookup"><span data-stu-id="e5431-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
