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
ms.openlocfilehash: 685d303b31b8f8c20cbbdb8aec6fc127650aa32a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616045"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="3dff1-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated, méthode</span><span class="sxs-lookup"><span data-stu-id="3dff1-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="3dff1-103">Obtient la taille totale, en octets, de toutes les allocations de mémoire effectuées par le domaine d’application depuis sa création, sans soustraire la mémoire qui a été récupérée par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="3dff1-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dff1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3dff1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dff1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3dff1-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="3dff1-106">dans ID du domaine d’application demandé.</span><span class="sxs-lookup"><span data-stu-id="3dff1-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="3dff1-107">à Pointeur vers la taille totale de toutes les allocations de mémoire.</span><span class="sxs-lookup"><span data-stu-id="3dff1-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3dff1-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3dff1-108">Return Value</span></span>  
 <span data-ttu-id="3dff1-109">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="3dff1-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3dff1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3dff1-110">HRESULT</span></span>|<span data-ttu-id="3dff1-111">Description</span><span class="sxs-lookup"><span data-stu-id="3dff1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3dff1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3dff1-112">S_OK</span></span>|<span data-ttu-id="3dff1-113">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="3dff1-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="3dff1-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="3dff1-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="3dff1-115">Le domaine d’application a été déchargé ou n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="3dff1-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3dff1-116">Notes</span><span class="sxs-lookup"><span data-stu-id="3dff1-116">Remarks</span></span>  
 <span data-ttu-id="3dff1-117">Cette méthode est l’équivalent non managé de la propriété managée <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3dff1-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dff1-118">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="3dff1-118">Requirements</span></span>  
 <span data-ttu-id="3dff1-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dff1-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dff1-120">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="3dff1-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3dff1-121">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3dff1-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3dff1-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dff1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dff1-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3dff1-123">See also</span></span>

- [<span data-ttu-id="3dff1-124">ICLRAppDomainResourceMonitor, interface</span><span class="sxs-lookup"><span data-stu-id="3dff1-124">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="3dff1-125">Analyse des ressources du domaine d’application</span><span class="sxs-lookup"><span data-stu-id="3dff1-125">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="3dff1-126">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="3dff1-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="3dff1-127">Hébergement</span><span class="sxs-lookup"><span data-stu-id="3dff1-127">Hosting</span></span>](index.md)
