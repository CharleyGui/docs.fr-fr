---
title: ICLRControl::SetAppDomainManagerType, méthode
ms.date: 03/30/2017
api_name:
- ICLRControl.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type:
- apiref
ms.openlocfilehash: e62f9fd6b8421ea131eff0e6b36523718589c921
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615824"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="7ac30-102">ICLRControl::SetAppDomainManagerType, méthode</span><span class="sxs-lookup"><span data-stu-id="7ac30-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="7ac30-103">Définit un type dérivé de <xref:System.AppDomainManager> comme type pour les gestionnaires de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="7ac30-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ac30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ac30-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ac30-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7ac30-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="7ac30-106">dans Nom de l’assembly dans lequel le type demandé dérivé de <xref:System.AppDomainManager> est implémenté.</span><span class="sxs-lookup"><span data-stu-id="7ac30-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="7ac30-107">dans Nom du type implémenté dans le `pwzAppDomainManagerAssembly` paramètre qui implémente les fonctionnalités de <xref:System.AppDomainManager> .</span><span class="sxs-lookup"><span data-stu-id="7ac30-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ac30-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7ac30-108">Return Value</span></span>  
  
|<span data-ttu-id="7ac30-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7ac30-109">HRESULT</span></span>|<span data-ttu-id="7ac30-110">Description</span><span class="sxs-lookup"><span data-stu-id="7ac30-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7ac30-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7ac30-111">S_OK</span></span>|<span data-ttu-id="7ac30-112">Retour réussi de la méthode.</span><span class="sxs-lookup"><span data-stu-id="7ac30-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="7ac30-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7ac30-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7ac30-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="7ac30-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7ac30-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7ac30-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7ac30-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="7ac30-116">The call timed out.</span></span>|  
|<span data-ttu-id="7ac30-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7ac30-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7ac30-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="7ac30-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7ac30-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7ac30-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7ac30-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="7ac30-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7ac30-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7ac30-121">E_FAIL</span></span>|<span data-ttu-id="7ac30-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="7ac30-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7ac30-123">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="7ac30-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7ac30-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7ac30-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7ac30-125">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="7ac30-125">Requirements</span></span>  
 <span data-ttu-id="7ac30-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ac30-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ac30-127">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7ac30-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7ac30-128">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7ac30-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ac30-129">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ac30-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ac30-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ac30-130">See also</span></span>

- [<span data-ttu-id="7ac30-131">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="7ac30-131">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="7ac30-132">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="7ac30-132">IHostControl Interface</span></span>](ihostcontrol-interface.md)
