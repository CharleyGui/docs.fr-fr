---
title: ICLRRuntimeHost, interface
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba02373aae33baf77b72323fabf1f6ca1fe4eecf
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490240"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="d2207-102">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="d2207-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="d2207-103">Fournit des fonctionnalités similaires à celles de la [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface fournie dans le .NET Framework version 1, avec les modifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="d2207-103">Provides functionality similar to that of the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="d2207-104">L’ajout de la [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) méthode pour définir l’interface de contrôle hôte.</span><span class="sxs-lookup"><span data-stu-id="d2207-104">The addition of the [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="d2207-105">L’omission de certaines méthodes fournies par `ICorRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="d2207-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2207-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d2207-106">Methods</span></span>  
  
|<span data-ttu-id="d2207-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="d2207-107">Method</span></span>|<span data-ttu-id="d2207-108">Description</span><span class="sxs-lookup"><span data-stu-id="d2207-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d2207-109">ExecuteApplication, méthode</span><span class="sxs-lookup"><span data-stu-id="d2207-109">ExecuteApplication Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="d2207-110">Utilisé dans les scénarios de déploiement ClickOnce basée sur un manifeste pour spécifier l’application à activer dans un nouveau domaine.</span><span class="sxs-lookup"><span data-stu-id="d2207-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="d2207-111">ExecuteInAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="d2207-111">ExecuteInAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="d2207-112">Spécifie le <xref:System.AppDomain> dans lequel exécuter le code managé spécifié.</span><span class="sxs-lookup"><span data-stu-id="d2207-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="d2207-113">ExecuteInDefaultAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="d2207-113">ExecuteInDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="d2207-114">Appelle la méthode spécifiée du type spécifié dans l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="d2207-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="d2207-115">GetCLRControl, méthode</span><span class="sxs-lookup"><span data-stu-id="d2207-115">GetCLRControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="d2207-116">Obtient un pointeur d’interface de type [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) que les hôtes peuvent utiliser pour personnaliser les aspects du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="d2207-116">Gets an interface pointer of type [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="d2207-117">GetCurrentAppDomainId, méthode</span><span class="sxs-lookup"><span data-stu-id="d2207-117">GetCurrentAppDomainId Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="d2207-118">Obtient l’identificateur numérique de la <xref:System.AppDomain> qui est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d2207-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="d2207-119">SetHostControl, méthode</span><span class="sxs-lookup"><span data-stu-id="d2207-119">SetHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="d2207-120">Définit l’interface de contrôle hôte.</span><span class="sxs-lookup"><span data-stu-id="d2207-120">Sets the host control interface.</span></span> <span data-ttu-id="d2207-121">Vous devez appeler `SetHostControl` avant d’appeler `Start`.</span><span class="sxs-lookup"><span data-stu-id="d2207-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="d2207-122">Start, méthode</span><span class="sxs-lookup"><span data-stu-id="d2207-122">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|<span data-ttu-id="d2207-123">Initialise le CLR dans un processus.</span><span class="sxs-lookup"><span data-stu-id="d2207-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="d2207-124">Stop, méthode</span><span class="sxs-lookup"><span data-stu-id="d2207-124">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|<span data-ttu-id="d2207-125">Arrête l’exécution du code par le runtime.</span><span class="sxs-lookup"><span data-stu-id="d2207-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="d2207-126">UnloadAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="d2207-126">UnloadAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="d2207-127">Décharge le <xref:System.AppDomain> qui correspond à l’identificateur numérique spécifié.</span><span class="sxs-lookup"><span data-stu-id="d2207-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2207-128">Notes</span><span class="sxs-lookup"><span data-stu-id="d2207-128">Remarks</span></span>  
 <span data-ttu-id="d2207-129">À compter de .NET Framework 4, utilisez le [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface permettant d’obtenir un pointeur vers le [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, puis appelez le [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)méthode pour obtenir un pointeur vers `ICLRRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="d2207-129">Starting with the .NET Framework 4, use the [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="d2207-130">Dans les versions antérieures du .NET Framework, l’hôte obtient un pointeur vers un `ICLRRuntimeHost` instance en appelant [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="d2207-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="d2207-131">Pour fournir des implémentations de chacune des technologies fournies dans le .NET Framework version 2.0, vous devez utiliser `ICLRRuntimeHost` au lieu de `ICorRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="d2207-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d2207-132">N’appelez pas la [Démarrer](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) méthode avant d’appeler le [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) méthode permettant d’activer une application basée sur un manifeste.</span><span class="sxs-lookup"><span data-stu-id="d2207-132">Do not call the [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="d2207-133">Si le `Start` méthode est appelée en premier, le `ExecuteApplication` appel de méthode échoue.</span><span class="sxs-lookup"><span data-stu-id="d2207-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2207-134">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d2207-134">Requirements</span></span>  
 <span data-ttu-id="d2207-135">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2207-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2207-136">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d2207-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d2207-137">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d2207-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2207-138">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2207-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2207-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2207-139">See also</span></span>

- [<span data-ttu-id="d2207-140">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="d2207-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="d2207-141">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="d2207-141">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="d2207-142">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="d2207-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="d2207-143">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="d2207-143">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="d2207-144">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="d2207-144">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="d2207-145">CLRRuntimeHost, coclasse</span><span class="sxs-lookup"><span data-stu-id="d2207-145">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
