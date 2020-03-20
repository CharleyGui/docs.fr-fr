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
ms.openlocfilehash: 11d042ea9eecc8d428761da6eaa15f7c2907ebd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176264"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="0f99c-102">IHostSecurityManager::OpenThreadToken, méthode</span><span class="sxs-lookup"><span data-stu-id="0f99c-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="0f99c-103">Ouvre le jeton d’accès discrétionnaire associé au fil d’exécution actuel.</span><span class="sxs-lookup"><span data-stu-id="0f99c-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f99c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f99c-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,
    [in]  BOOL     bOpenAsSelf,
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f99c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0f99c-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="0f99c-106">[dans] Masque de valeurs d’accès qui spécifient les types d’accès demandés au jeton de thread.</span><span class="sxs-lookup"><span data-stu-id="0f99c-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="0f99c-107">Ces valeurs sont définies `OpenThreadToken` dans la fonction Win32.</span><span class="sxs-lookup"><span data-stu-id="0f99c-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="0f99c-108">Les types d’accès demandés sont conciliés avec la liste discrétionnaire de contrôle d’accès (DACL) du jeton afin de déterminer quels types d’accès à l’octroi ou au refus.</span><span class="sxs-lookup"><span data-stu-id="0f99c-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="0f99c-109">[dans] `true` spécifier que la vérification d’accès doit être effectuée en utilisant le contexte de sécurité du processus pour le thread d’appel; `false` spécifier que la vérification d’accès doit être effectuée en utilisant le contexte de sécurité du fil d’appel lui-même.</span><span class="sxs-lookup"><span data-stu-id="0f99c-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="0f99c-110">Si le thread se fait passer pour un client, le contexte de sécurité peut être celui d’un processus client.</span><span class="sxs-lookup"><span data-stu-id="0f99c-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="0f99c-111">[out] Un pointeur sur le jeton d’accès nouvellement ouvert.</span><span class="sxs-lookup"><span data-stu-id="0f99c-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f99c-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0f99c-112">Return Value</span></span>  
  
|<span data-ttu-id="0f99c-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f99c-113">HRESULT</span></span>|<span data-ttu-id="0f99c-114">Description</span><span class="sxs-lookup"><span data-stu-id="0f99c-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0f99c-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="0f99c-115">S_OK</span></span>|<span data-ttu-id="0f99c-116">`OpenThreadToken`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="0f99c-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="0f99c-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0f99c-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0f99c-118">L’heure courante de l’exécution de la langue (CLR) n’a pas été chargée dans un processus, ou le CLR est dans un état où il ne peut pas exécuter le code géré ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="0f99c-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0f99c-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0f99c-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0f99c-120">L’appel s’est fait chronométrer.</span><span class="sxs-lookup"><span data-stu-id="0f99c-120">The call timed out.</span></span>|  
|<span data-ttu-id="0f99c-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0f99c-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0f99c-122">L’appelant n’est pas propriétaire de la serrure.</span><span class="sxs-lookup"><span data-stu-id="0f99c-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0f99c-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0f99c-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0f99c-124">Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="0f99c-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0f99c-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0f99c-125">E_FAIL</span></span>|<span data-ttu-id="0f99c-126">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="0f99c-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0f99c-127">Lorsqu’une méthode revient E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="0f99c-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0f99c-128">Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0f99c-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f99c-129">Notes </span><span class="sxs-lookup"><span data-stu-id="0f99c-129">Remarks</span></span>  
 <span data-ttu-id="0f99c-130">`IHostSecurityManager::OpenThreadToken`se comporte de la même manière que la fonction Win32 correspondante du même nom, sauf que la fonction `IHostSecurityManager::OpenThreadToken` Win32 permet à l’appelant de passer dans une poignée à un thread arbitraire, tout en n’ouvrant que le jeton associé au fil d’appel.</span><span class="sxs-lookup"><span data-stu-id="0f99c-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="0f99c-131">Le `HANDLE` type n’est pas conforme à com, c’est-à-dire que sa taille est spécifique au système d’exploitation, et il nécessite un marshaling personnalisé.</span><span class="sxs-lookup"><span data-stu-id="0f99c-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="0f99c-132">Ainsi, ce jeton n’est utilisé que dans le processus, entre le CLR et l’hôte.</span><span class="sxs-lookup"><span data-stu-id="0f99c-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f99c-133">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0f99c-133">Requirements</span></span>  
 <span data-ttu-id="0f99c-134">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f99c-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f99c-135">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="0f99c-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f99c-136">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0f99c-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f99c-137">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f99c-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f99c-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f99c-138">See also</span></span>

- [<span data-ttu-id="0f99c-139">IHostSecurityContext, interface</span><span class="sxs-lookup"><span data-stu-id="0f99c-139">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="0f99c-140">IHostSecurityManager, interface</span><span class="sxs-lookup"><span data-stu-id="0f99c-140">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
