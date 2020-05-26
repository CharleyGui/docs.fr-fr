---
title: IHostSecurityManager::ImpersonateLoggedOnUser, méthode
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.ImpersonateLoggedOnUser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::ImpersonateLoggedOnUser
helpviewer_keywords:
- ImpersonateLoggedOnUser method [.NET Framework hosting]
- IHostSecurityManager::ImpersonateLoggedOnUser method [.NET Framework hosting]
ms.assetid: acc49ba0-f1d9-45ad-871f-9d053a89dcbe
topic_type:
- apiref
ms.openlocfilehash: ada12a35691e0897a44f4f00e2e439fc08ef18af
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803907"
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="c3673-102">IHostSecurityManager::ImpersonateLoggedOnUser, méthode</span><span class="sxs-lookup"><span data-stu-id="c3673-102">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>
<span data-ttu-id="c3673-103">Demande que le code soit exécuté à l’aide des informations d’identification de l’identité de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="c3673-103">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3673-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3673-104">Syntax</span></span>  
  
```cpp  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3673-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c3673-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="c3673-106">dans Jeton représentant les informations d’identification de l’utilisateur dont l’identité doit être empruntée.</span><span class="sxs-lookup"><span data-stu-id="c3673-106">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3673-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c3673-107">Return Value</span></span>  
  
|<span data-ttu-id="c3673-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c3673-108">HRESULT</span></span>|<span data-ttu-id="c3673-109">Description</span><span class="sxs-lookup"><span data-stu-id="c3673-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c3673-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c3673-110">S_OK</span></span>|<span data-ttu-id="c3673-111">`ImpersonateLoggedOnUser`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="c3673-111">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="c3673-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c3673-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c3673-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="c3673-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c3673-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c3673-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c3673-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="c3673-115">The call timed out.</span></span>|  
|<span data-ttu-id="c3673-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c3673-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c3673-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="c3673-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c3673-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c3673-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c3673-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="c3673-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c3673-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c3673-120">E_FAIL</span></span>|<span data-ttu-id="c3673-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="c3673-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c3673-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="c3673-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c3673-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c3673-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3673-124">Notes</span><span class="sxs-lookup"><span data-stu-id="c3673-124">Remarks</span></span>  
 <span data-ttu-id="c3673-125">Appelez `LogonUser` ou une fonction Win32 associée pour obtenir un handle des informations d’identification de l’identité de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="c3673-125">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="c3673-126">Le `HANDLE` type n’est pas conforme à com, autrement dit, sa taille est spécifique à un système d’exploitation et il nécessite un marshaling personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c3673-126">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="c3673-127">Ainsi, ce jeton est destiné à être utilisé uniquement dans le processus, entre le CLR et l’hôte.</span><span class="sxs-lookup"><span data-stu-id="c3673-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3673-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c3673-128">Requirements</span></span>  
 <span data-ttu-id="c3673-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3673-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3673-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c3673-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c3673-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c3673-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3673-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3673-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3673-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3673-133">See also</span></span>

- [<span data-ttu-id="c3673-134">IHostSecurityContext, interface</span><span class="sxs-lookup"><span data-stu-id="c3673-134">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="c3673-135">IHostSecurityManager, interface</span><span class="sxs-lookup"><span data-stu-id="c3673-135">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="c3673-136">RevertToSelf, méthode</span><span class="sxs-lookup"><span data-stu-id="c3673-136">RevertToSelf Method</span></span>](ihostsecuritymanager-reverttoself-method.md)
