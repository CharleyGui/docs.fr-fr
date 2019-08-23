---
title: ICLRAppDomainResourceMonitor::GetCurrentCpuTime, méthode
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10245541718fd5e5f30ef6bba4ab289bcef767fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950212"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="d59d0-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime, méthode</span><span class="sxs-lookup"><span data-stu-id="d59d0-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>
<span data-ttu-id="d59d0-103">Obtient le temps processeur total utilisé par tous les threads lors de l’exécution dans le domaine d’application actuel, depuis la création du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="d59d0-103">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d59d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d59d0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d59d0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d59d0-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="d59d0-106">dans ID du domaine d’application demandé.</span><span class="sxs-lookup"><span data-stu-id="d59d0-106">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="d59d0-107">à Pointeur vers le temps processeur total qui a été utilisé par tous les threads lors de l’exécution dans le domaine d’application actuel depuis la création du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="d59d0-107">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="d59d0-108">Ce paramètre peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="d59d0-108">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d59d0-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d59d0-109">Return Value</span></span>  
  
|<span data-ttu-id="d59d0-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d59d0-110">HRESULT</span></span>|<span data-ttu-id="d59d0-111">Description</span><span class="sxs-lookup"><span data-stu-id="d59d0-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d59d0-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d59d0-112">S_OK</span></span>|<span data-ttu-id="d59d0-113">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="d59d0-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="d59d0-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="d59d0-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="d59d0-115">Le domaine d’application a été déchargé ou n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="d59d0-115">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="d59d0-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d59d0-116">E_FAIL</span></span>|<span data-ttu-id="d59d0-117">L’analyse des ressources du domaine d’application n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="d59d0-117">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="d59d0-118">ou</span><span class="sxs-lookup"><span data-stu-id="d59d0-118">-or-</span></span><br /><br /> <span data-ttu-id="d59d0-119">Tous les autres échecs.</span><span class="sxs-lookup"><span data-stu-id="d59d0-119">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d59d0-120">Notes</span><span class="sxs-lookup"><span data-stu-id="d59d0-120">Remarks</span></span>  
 <span data-ttu-id="d59d0-121">Cette méthode est l’équivalent non managé de la propriété managée <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d59d0-121">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d59d0-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d59d0-122">Requirements</span></span>  
 <span data-ttu-id="d59d0-123">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d59d0-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d59d0-124">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d59d0-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d59d0-125">**Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d59d0-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d59d0-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d59d0-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d59d0-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d59d0-127">See also</span></span>

- [<span data-ttu-id="d59d0-128">ICLRAppDomainResourceMonitor, interface</span><span class="sxs-lookup"><span data-stu-id="d59d0-128">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="d59d0-129">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="d59d0-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="d59d0-130">Analyse de ressource de domaine d'application</span><span class="sxs-lookup"><span data-stu-id="d59d0-130">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="d59d0-131">Hébergement</span><span class="sxs-lookup"><span data-stu-id="d59d0-131">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
