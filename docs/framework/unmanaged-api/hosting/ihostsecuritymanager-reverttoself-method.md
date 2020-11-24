---
title: IHostSecurityManager::RevertToSelf, méthode
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.RevertToSelf
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::RevertToSelf
helpviewer_keywords:
- RevertToSelf method [.NET Framework hosting]
- IHostSecurityManager::RevertToSelf method [.NET Framework hosting]
ms.assetid: 189f28f8-f9a1-4192-aedc-91084e4f8b99
topic_type:
- apiref
ms.openlocfilehash: a54c25cb0cae906dc2d030900b9a1e1dbbbb2f1e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680519"
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="b91f1-102">IHostSecurityManager::RevertToSelf, méthode</span><span class="sxs-lookup"><span data-stu-id="b91f1-102">IHostSecurityManager::RevertToSelf Method</span></span>

<span data-ttu-id="b91f1-103">Termine l’emprunt d’identité de l’identité de l’utilisateur actuel et retourne le jeton de thread d’origine.</span><span class="sxs-lookup"><span data-stu-id="b91f1-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b91f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b91f1-104">Syntax</span></span>  
  
```cpp  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b91f1-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b91f1-105">Return Value</span></span>  
  
|<span data-ttu-id="b91f1-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b91f1-106">HRESULT</span></span>|<span data-ttu-id="b91f1-107">Description</span><span class="sxs-lookup"><span data-stu-id="b91f1-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b91f1-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="b91f1-108">S_OK</span></span>|<span data-ttu-id="b91f1-109">`RevertToSelf` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="b91f1-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="b91f1-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b91f1-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b91f1-111">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="b91f1-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b91f1-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b91f1-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b91f1-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="b91f1-113">The call timed out.</span></span>|  
|<span data-ttu-id="b91f1-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b91f1-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b91f1-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="b91f1-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b91f1-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b91f1-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b91f1-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="b91f1-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b91f1-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b91f1-118">E_FAIL</span></span>|<span data-ttu-id="b91f1-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b91f1-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b91f1-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="b91f1-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b91f1-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b91f1-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b91f1-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="b91f1-122">Remarks</span></span>  

 <span data-ttu-id="b91f1-123">`RevertToSelf` est appelé pour retourner au jeton de thread d’origine, après un appel antérieur à la méthode [ImpersonateLoggedOnUser](ihostsecuritymanager-impersonateloggedonuser-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b91f1-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b91f1-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b91f1-124">Requirements</span></span>  

 <span data-ttu-id="b91f1-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b91f1-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b91f1-126">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b91f1-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b91f1-127">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b91f1-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b91f1-128">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b91f1-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b91f1-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b91f1-129">See also</span></span>

- [<span data-ttu-id="b91f1-130">IHostSecurityContext, interface</span><span class="sxs-lookup"><span data-stu-id="b91f1-130">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="b91f1-131">IHostSecurityManager, interface</span><span class="sxs-lookup"><span data-stu-id="b91f1-131">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="b91f1-132">ImpersonateLoggedOnUser, méthode</span><span class="sxs-lookup"><span data-stu-id="b91f1-132">ImpersonateLoggedOnUser Method</span></span>](ihostsecuritymanager-impersonateloggedonuser-method.md)
