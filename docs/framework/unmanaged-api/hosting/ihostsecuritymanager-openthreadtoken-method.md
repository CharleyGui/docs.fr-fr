---
title: IHostSecurityManager::OpenThreadToken, méthode
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1beeb0ff6b2e3493f0814fc3371f189bd4d485d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778021"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="6760f-102">IHostSecurityManager::OpenThreadToken, méthode</span><span class="sxs-lookup"><span data-stu-id="6760f-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="6760f-103">Ouvre le jeton d’accès discrétionnaire associé au thread en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6760f-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6760f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6760f-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6760f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6760f-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="6760f-106">[in] Masque des valeurs d’accès qui spécifient les types demandés d’accès au jeton de thread.</span><span class="sxs-lookup"><span data-stu-id="6760f-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="6760f-107">Ces valeurs sont définies dans Win32 `OpenThreadToken` (fonction).</span><span class="sxs-lookup"><span data-stu-id="6760f-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="6760f-108">Les types d’accès demandés sont rapprochées par rapport à la liste de contrôle d’accès discrétionnaire (DACL) pour déterminer quels types d’accès à accorder ou refuser du jeton.</span><span class="sxs-lookup"><span data-stu-id="6760f-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="6760f-109">[in] `true` pour spécifier que la vérification d’accès doit être effectuée à l’aide du contexte de sécurité du processus pour le thread appelant ; `false` pour spécifier que la vérification d’accès doit être effectuée à l’aide du contexte de sécurité pour le thread appelant lui-même.</span><span class="sxs-lookup"><span data-stu-id="6760f-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="6760f-110">Si le thread emprunte un client, le contexte de sécurité peut être celui d’un processus client.</span><span class="sxs-lookup"><span data-stu-id="6760f-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="6760f-111">[out] Pointeur vers le jeton d’accès qui vient d’être ouvert.</span><span class="sxs-lookup"><span data-stu-id="6760f-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6760f-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6760f-112">Return Value</span></span>  
  
|<span data-ttu-id="6760f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6760f-113">HRESULT</span></span>|<span data-ttu-id="6760f-114">Description</span><span class="sxs-lookup"><span data-stu-id="6760f-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6760f-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="6760f-115">S_OK</span></span>|<span data-ttu-id="6760f-116">`OpenThreadToken` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="6760f-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="6760f-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6760f-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6760f-118">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="6760f-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6760f-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6760f-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6760f-120">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="6760f-120">The call timed out.</span></span>|  
|<span data-ttu-id="6760f-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6760f-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6760f-122">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="6760f-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6760f-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6760f-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6760f-124">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="6760f-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6760f-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6760f-125">E_FAIL</span></span>|<span data-ttu-id="6760f-126">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="6760f-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6760f-127">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="6760f-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6760f-128">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6760f-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6760f-129">Notes</span><span class="sxs-lookup"><span data-stu-id="6760f-129">Remarks</span></span>  
 <span data-ttu-id="6760f-130">`IHostSecurityManager::OpenThreadToken` se comporte de la même façon pour la fonction Win32 correspondante du même nom, sauf que la fonction Win32 permet à l’appelant de passer un handle à un thread arbitraire, alors que `IHostSecurityManager::OpenThreadToken` s’ouvre uniquement le jeton associé au thread appelant.</span><span class="sxs-lookup"><span data-stu-id="6760f-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="6760f-131">Le `HANDLE` type n’est pas conforme à COM, autrement dit, sa taille est spécifique au système d’exploitation et il requiert le marshaling personnalisé.</span><span class="sxs-lookup"><span data-stu-id="6760f-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="6760f-132">Par conséquent, ce jeton est utilisé que dans le processus, entre le CLR et l’hôte.</span><span class="sxs-lookup"><span data-stu-id="6760f-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6760f-133">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6760f-133">Requirements</span></span>  
 <span data-ttu-id="6760f-134">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6760f-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6760f-135">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6760f-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6760f-136">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6760f-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6760f-137">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6760f-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6760f-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6760f-138">See also</span></span>

- [<span data-ttu-id="6760f-139">IHostSecurityContext, interface</span><span class="sxs-lookup"><span data-stu-id="6760f-139">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="6760f-140">IHostSecurityManager, interface</span><span class="sxs-lookup"><span data-stu-id="6760f-140">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
