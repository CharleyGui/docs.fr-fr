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
ms.openlocfilehash: 72caac0aafe7f9c5919057a6ad2565258aec6a50
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504072"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="41c7e-102">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="41c7e-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="41c7e-103">Fournit des fonctionnalités similaires à celles de l’interface [ICorRuntimeHost](icorruntimehost-interface.md) fournie dans la .NET Framework version 1, avec les modifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="41c7e-103">Provides functionality similar to that of the [ICorRuntimeHost](icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="41c7e-104">Ajout de la méthode [SetHostControl](iclrruntimehost-sethostcontrol-method.md) pour définir l’interface de contrôle hôte.</span><span class="sxs-lookup"><span data-stu-id="41c7e-104">The addition of the [SetHostControl](iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="41c7e-105">Omission de certaines méthodes fournies par `ICorRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="41c7e-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="41c7e-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="41c7e-106">Methods</span></span>  
  
|<span data-ttu-id="41c7e-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="41c7e-107">Method</span></span>|<span data-ttu-id="41c7e-108">Description</span><span class="sxs-lookup"><span data-stu-id="41c7e-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="41c7e-109">ExecuteApplication, méthode</span><span class="sxs-lookup"><span data-stu-id="41c7e-109">ExecuteApplication Method</span></span>](iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="41c7e-110">Utilisé dans les scénarios de déploiement ClickOnce basés sur un manifeste pour spécifier l’application à activer dans un nouveau domaine.</span><span class="sxs-lookup"><span data-stu-id="41c7e-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="41c7e-111">ExecuteInAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="41c7e-111">ExecuteInAppDomain Method</span></span>](iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="41c7e-112">Spécifie le <xref:System.AppDomain> dans lequel exécuter le code managé spécifié.</span><span class="sxs-lookup"><span data-stu-id="41c7e-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="41c7e-113">ExecuteInDefaultAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="41c7e-113">ExecuteInDefaultAppDomain Method</span></span>](iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="41c7e-114">Appelle la méthode spécifiée du type spécifié dans l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="41c7e-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="41c7e-115">GetCLRControl, méthode</span><span class="sxs-lookup"><span data-stu-id="41c7e-115">GetCLRControl Method</span></span>](iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="41c7e-116">Obtient un pointeur d’interface de type [ICLRControl](iclrcontrol-interface.md) que les hôtes peuvent utiliser pour personnaliser les aspects du Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="41c7e-116">Gets an interface pointer of type [ICLRControl](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="41c7e-117">GetCurrentAppDomainId, méthode</span><span class="sxs-lookup"><span data-stu-id="41c7e-117">GetCurrentAppDomainId Method</span></span>](iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="41c7e-118">Obtient l’identificateur numérique du en <xref:System.AppDomain> cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="41c7e-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="41c7e-119">SetHostControl, méthode</span><span class="sxs-lookup"><span data-stu-id="41c7e-119">SetHostControl Method</span></span>](iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="41c7e-120">Définit l’interface de contrôle hôte.</span><span class="sxs-lookup"><span data-stu-id="41c7e-120">Sets the host control interface.</span></span> <span data-ttu-id="41c7e-121">Vous devez appeler `SetHostControl` avant d’appeler `Start` .</span><span class="sxs-lookup"><span data-stu-id="41c7e-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="41c7e-122">Start, méthode</span><span class="sxs-lookup"><span data-stu-id="41c7e-122">Start Method</span></span>](iclrruntimehost-start-method.md)|<span data-ttu-id="41c7e-123">Initialise le CLR dans un processus.</span><span class="sxs-lookup"><span data-stu-id="41c7e-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="41c7e-124">Stop, méthode</span><span class="sxs-lookup"><span data-stu-id="41c7e-124">Stop Method</span></span>](iclrruntimehost-stop-method.md)|<span data-ttu-id="41c7e-125">Arrête l’exécution du code par le Runtime.</span><span class="sxs-lookup"><span data-stu-id="41c7e-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="41c7e-126">UnloadAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="41c7e-126">UnloadAppDomain Method</span></span>](iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="41c7e-127">Décharge le <xref:System.AppDomain> qui correspond à l’identificateur numérique spécifié.</span><span class="sxs-lookup"><span data-stu-id="41c7e-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41c7e-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="41c7e-128">Remarks</span></span>  
 <span data-ttu-id="41c7e-129">À partir du .NET Framework 4, utilisez l’interface [ICLRMetaHost](iclrmetahost-interface.md) pour obtenir un pointeur vers l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , puis appelez la méthode [ICLRRuntimeInfo :: GetInterface](iclrruntimeinfo-getinterface-method.md) pour obtenir un pointeur vers `ICLRRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="41c7e-129">Starting with the .NET Framework 4, use the [ICLRMetaHost](iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="41c7e-130">Dans les versions antérieures du .NET Framework, l’hôte obtient un pointeur vers une `ICLRRuntimeHost` instance en appelant [CorBindToRuntimeEx](corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime,](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="41c7e-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="41c7e-131">Pour fournir des implémentations de l’une des technologies fournies dans le .NET Framework version 2,0, vous devez utiliser `ICLRRuntimeHost` au lieu de `ICorRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="41c7e-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="41c7e-132">N’appelez pas la méthode [Start](iclrruntimehost-start-method.md) avant d’appeler la méthode [ExecuteApplication](iclrruntimehost-executeapplication-method.md) pour activer une application basée sur un manifeste.</span><span class="sxs-lookup"><span data-stu-id="41c7e-132">Do not call the [Start](iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="41c7e-133">Si la `Start` méthode est appelée en premier, l’appel de la `ExecuteApplication` méthode échoue.</span><span class="sxs-lookup"><span data-stu-id="41c7e-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41c7e-134">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="41c7e-134">Requirements</span></span>  
 <span data-ttu-id="41c7e-135">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41c7e-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41c7e-136">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="41c7e-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41c7e-137">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="41c7e-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41c7e-138">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41c7e-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c7e-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41c7e-139">See also</span></span>

- [<span data-ttu-id="41c7e-140">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="41c7e-140">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="41c7e-141">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="41c7e-141">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="41c7e-142">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="41c7e-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="41c7e-143">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="41c7e-143">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="41c7e-144">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="41c7e-144">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="41c7e-145">Coclasse CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="41c7e-145">CLRRuntimeHost Coclass</span></span>](clrruntimehost-coclass.md)
