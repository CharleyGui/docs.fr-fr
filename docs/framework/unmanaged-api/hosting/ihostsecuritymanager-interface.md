---
title: IHostSecurityManager, interface
ms.date: 03/30/2017
api_name:
- IHostSecurityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager
helpviewer_keywords:
- IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type:
- apiref
ms.openlocfilehash: 237fe23493460df77a79ba3aed9f0a809cd8aa23
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501467"
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="bc3e8-102">IHostSecurityManager, interface</span><span class="sxs-lookup"><span data-stu-id="bc3e8-102">IHostSecurityManager Interface</span></span>
<span data-ttu-id="bc3e8-103">Fournit des méthodes qui autorisent l’accès et le contrôle sur le contexte de sécurité du thread en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="bc3e8-103">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bc3e8-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="bc3e8-104">Methods</span></span>  
  
|<span data-ttu-id="bc3e8-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="bc3e8-105">Method</span></span>|<span data-ttu-id="bc3e8-106">Description</span><span class="sxs-lookup"><span data-stu-id="bc3e8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bc3e8-107">GetSecurityContext, méthode</span><span class="sxs-lookup"><span data-stu-id="bc3e8-107">GetSecurityContext Method</span></span>](ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="bc3e8-108">Obtient le [IHostSecurityContext](ihostsecuritycontext-interface.md) demandé à partir de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="bc3e8-108">Gets the requested [IHostSecurityContext](ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="bc3e8-109">ImpersonateLoggedOnUser, méthode</span><span class="sxs-lookup"><span data-stu-id="bc3e8-109">ImpersonateLoggedOnUser Method</span></span>](ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="bc3e8-110">Demande que le code soit exécuté à l’aide des informations d’identification de l’identité de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="bc3e8-110">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="bc3e8-111">OpenThreadToken, méthode</span><span class="sxs-lookup"><span data-stu-id="bc3e8-111">OpenThreadToken Method</span></span>](ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="bc3e8-112">Ouvre le jeton d’accès discrétionnaire associé au thread actuel.</span><span class="sxs-lookup"><span data-stu-id="bc3e8-112">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="bc3e8-113">RevertToSelf, méthode</span><span class="sxs-lookup"><span data-stu-id="bc3e8-113">RevertToSelf Method</span></span>](ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="bc3e8-114">Termine l’emprunt d’identité de l’identité de l’utilisateur actuel et retourne le jeton de thread d’origine.</span><span class="sxs-lookup"><span data-stu-id="bc3e8-114">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="bc3e8-115">SetSecurityContext, méthode</span><span class="sxs-lookup"><span data-stu-id="bc3e8-115">SetSecurityContext Method</span></span>](ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="bc3e8-116">Définit le contexte de sécurité pour le thread en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="bc3e8-116">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="bc3e8-117">SetThreadToken, méthode</span><span class="sxs-lookup"><span data-stu-id="bc3e8-117">SetThreadToken Method</span></span>](ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="bc3e8-118">Définit un handle pour le thread en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="bc3e8-118">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc3e8-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="bc3e8-119">Remarks</span></span>  
 <span data-ttu-id="bc3e8-120">Un hôte peut contrôler tout l’accès du code aux jetons de thread à la fois par le common language runtime (CLR) et le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bc3e8-120">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="bc3e8-121">Il peut également s’assurer que les informations de contexte de sécurité complètes sont transmises sur des opérations asynchrones ou des points de code avec accès restreint au code.</span><span class="sxs-lookup"><span data-stu-id="bc3e8-121">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="bc3e8-122">`IHostSecurityContext`encapsule ces informations de contexte de sécurité, qui sont opaques pour le CLR.</span><span class="sxs-lookup"><span data-stu-id="bc3e8-122">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="bc3e8-123">Le CLR gère le contexte de thread managé en interne.</span><span class="sxs-lookup"><span data-stu-id="bc3e8-123">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="bc3e8-124">Il interroge la spécifique au processus `IHostSecurityManager` dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="bc3e8-124">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
- <span data-ttu-id="bc3e8-125">Sur le thread finaliseur, pendant l’exécution du finaliseur.</span><span class="sxs-lookup"><span data-stu-id="bc3e8-125">On the finalizer thread, during finalizer execution.</span></span>  
  
- <span data-ttu-id="bc3e8-126">Pendant l’exécution du constructeur de module et de classe.</span><span class="sxs-lookup"><span data-stu-id="bc3e8-126">During class and module constructor execution.</span></span>  
  
- <span data-ttu-id="bc3e8-127">À des points asynchrones sur le thread de travail, dans les appels à la méthode [IHostThreadPoolManager :: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bc3e8-127">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
- <span data-ttu-id="bc3e8-128">Dans la maintenance des ports de terminaison d’e/s.</span><span class="sxs-lookup"><span data-stu-id="bc3e8-128">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc3e8-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bc3e8-129">Requirements</span></span>  
 <span data-ttu-id="bc3e8-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc3e8-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc3e8-131">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bc3e8-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bc3e8-132">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bc3e8-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc3e8-133">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc3e8-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc3e8-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc3e8-134">See also</span></span>

- [<span data-ttu-id="bc3e8-135">IHostSecurityContext, interface</span><span class="sxs-lookup"><span data-stu-id="bc3e8-135">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="bc3e8-136">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="bc3e8-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
