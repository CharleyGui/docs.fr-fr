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
ms.openlocfilehash: 8d88222215eb31e1c63f3b26079517c4b088e81b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728834"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="6ec4a-102">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="6ec4a-102">ICLRRuntimeHost Interface</span></span>

<span data-ttu-id="6ec4a-103">Fournit des fonctionnalités similaires à celles de l’interface [ICorRuntimeHost](icorruntimehost-interface.md) fournie dans la .NET Framework version 1, avec les modifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="6ec4a-103">Provides functionality similar to that of the [ICorRuntimeHost](icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="6ec4a-104">Ajout de la méthode [SetHostControl](iclrruntimehost-sethostcontrol-method.md) pour définir l’interface de contrôle hôte.</span><span class="sxs-lookup"><span data-stu-id="6ec4a-104">The addition of the [SetHostControl](iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="6ec4a-105">Omission de certaines méthodes fournies par `ICorRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="6ec4a-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6ec4a-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6ec4a-106">Methods</span></span>  
  
|<span data-ttu-id="6ec4a-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="6ec4a-107">Method</span></span>|<span data-ttu-id="6ec4a-108">Description</span><span class="sxs-lookup"><span data-stu-id="6ec4a-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6ec4a-109">ExecuteApplication, méthode</span><span class="sxs-lookup"><span data-stu-id="6ec4a-109">ExecuteApplication Method</span></span>](iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="6ec4a-110">Utilisé dans les scénarios de déploiement ClickOnce basés sur un manifeste pour spécifier l’application à activer dans un nouveau domaine.</span><span class="sxs-lookup"><span data-stu-id="6ec4a-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="6ec4a-111">ExecuteInAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="6ec4a-111">ExecuteInAppDomain Method</span></span>](iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="6ec4a-112">Spécifie le <xref:System.AppDomain> dans lequel exécuter le code managé spécifié.</span><span class="sxs-lookup"><span data-stu-id="6ec4a-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="6ec4a-113">ExecuteInDefaultAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="6ec4a-113">ExecuteInDefaultAppDomain Method</span></span>](iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="6ec4a-114">Appelle la méthode spécifiée du type spécifié dans l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="6ec4a-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="6ec4a-115">GetCLRControl, méthode</span><span class="sxs-lookup"><span data-stu-id="6ec4a-115">GetCLRControl Method</span></span>](iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="6ec4a-116">Obtient un pointeur d’interface de type [ICLRControl](iclrcontrol-interface.md) que les hôtes peuvent utiliser pour personnaliser les aspects du Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="6ec4a-116">Gets an interface pointer of type [ICLRControl](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="6ec4a-117">GetCurrentAppDomainId, méthode</span><span class="sxs-lookup"><span data-stu-id="6ec4a-117">GetCurrentAppDomainId Method</span></span>](iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="6ec4a-118">Obtient l’identificateur numérique du en <xref:System.AppDomain> cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6ec4a-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="6ec4a-119">SetHostControl, méthode</span><span class="sxs-lookup"><span data-stu-id="6ec4a-119">SetHostControl Method</span></span>](iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="6ec4a-120">Définit l’interface de contrôle hôte.</span><span class="sxs-lookup"><span data-stu-id="6ec4a-120">Sets the host control interface.</span></span> <span data-ttu-id="6ec4a-121">Vous devez appeler `SetHostControl` avant d’appeler `Start` .</span><span class="sxs-lookup"><span data-stu-id="6ec4a-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="6ec4a-122">Start, méthode</span><span class="sxs-lookup"><span data-stu-id="6ec4a-122">Start Method</span></span>](iclrruntimehost-start-method.md)|<span data-ttu-id="6ec4a-123">Initialise le CLR dans un processus.</span><span class="sxs-lookup"><span data-stu-id="6ec4a-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="6ec4a-124">Stop (méthode)</span><span class="sxs-lookup"><span data-stu-id="6ec4a-124">Stop Method</span></span>](iclrruntimehost-stop-method.md)|<span data-ttu-id="6ec4a-125">Arrête l’exécution du code par le Runtime.</span><span class="sxs-lookup"><span data-stu-id="6ec4a-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="6ec4a-126">UnloadAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="6ec4a-126">UnloadAppDomain Method</span></span>](iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="6ec4a-127">Décharge le <xref:System.AppDomain> qui correspond à l’identificateur numérique spécifié.</span><span class="sxs-lookup"><span data-stu-id="6ec4a-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ec4a-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="6ec4a-128">Remarks</span></span>  

 <span data-ttu-id="6ec4a-129">À partir du .NET Framework 4, utilisez l’interface [ICLRMetaHost](iclrmetahost-interface.md) pour obtenir un pointeur vers l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , puis appelez la méthode [ICLRRuntimeInfo :: GetInterface](iclrruntimeinfo-getinterface-method.md) pour obtenir un pointeur vers `ICLRRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="6ec4a-129">Starting with the .NET Framework 4, use the [ICLRMetaHost](iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="6ec4a-130">Dans les versions antérieures du .NET Framework, l’hôte obtient un pointeur vers une `ICLRRuntimeHost` instance en appelant [CorBindToRuntimeEx](corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime,](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="6ec4a-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="6ec4a-131">Pour fournir des implémentations de l’une des technologies fournies dans le .NET Framework version 2,0, vous devez utiliser `ICLRRuntimeHost` au lieu de `ICorRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="6ec4a-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6ec4a-132">N’appelez pas la méthode [Start](iclrruntimehost-start-method.md) avant d’appeler la méthode [ExecuteApplication](iclrruntimehost-executeapplication-method.md) pour activer une application basée sur un manifeste.</span><span class="sxs-lookup"><span data-stu-id="6ec4a-132">Do not call the [Start](iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="6ec4a-133">Si la `Start` méthode est appelée en premier, l’appel de la `ExecuteApplication` méthode échoue.</span><span class="sxs-lookup"><span data-stu-id="6ec4a-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ec4a-134">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6ec4a-134">Requirements</span></span>  

 <span data-ttu-id="6ec4a-135">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ec4a-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ec4a-136">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6ec4a-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ec4a-137">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6ec4a-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ec4a-138">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ec4a-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ec4a-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ec4a-139">See also</span></span>

- [<span data-ttu-id="6ec4a-140">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="6ec4a-140">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="6ec4a-141">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="6ec4a-141">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="6ec4a-142">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="6ec4a-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="6ec4a-143">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="6ec4a-143">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="6ec4a-144">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="6ec4a-144">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="6ec4a-145">Coclasse CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="6ec4a-145">CLRRuntimeHost Coclass</span></span>](clrruntimehost-coclass.md)
