---
title: ICLRHostProtectionManager::SetEagerSerializeGrantSets, méthode
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetEagerSerializeGrantSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetEagerSerializeGrantSets
helpviewer_keywords:
- SetEagerSerializeGrantSets method [.NET Framework hosting]
- ICLRHostProtectionManager::SetEagerSerializeGrantSets method [.NET Framework hosting]
ms.assetid: d6158360-22b1-4ace-ad85-d830b9964783
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f14368956ee2ffd3ae875710e1e73e2bdbee8dd7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779654"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="2a67f-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets, méthode</span><span class="sxs-lookup"><span data-stu-id="2a67f-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="2a67f-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="2a67f-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a67f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a67f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2a67f-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2a67f-105">Return Value</span></span>  
  
|<span data-ttu-id="2a67f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2a67f-106">HRESULT</span></span>|<span data-ttu-id="2a67f-107">Description</span><span class="sxs-lookup"><span data-stu-id="2a67f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2a67f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2a67f-108">S_OK</span></span>|<span data-ttu-id="2a67f-109">`SetEagerSerializeGrantSets` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="2a67f-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="2a67f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2a67f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2a67f-111">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="2a67f-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2a67f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2a67f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2a67f-113">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="2a67f-113">The call timed out.</span></span>|  
|<span data-ttu-id="2a67f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2a67f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2a67f-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="2a67f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2a67f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2a67f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2a67f-117">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="2a67f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2a67f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2a67f-118">E_FAIL</span></span>|<span data-ttu-id="2a67f-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="2a67f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2a67f-120">Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="2a67f-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2a67f-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2a67f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2a67f-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2a67f-122">Requirements</span></span>  
 <span data-ttu-id="2a67f-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a67f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a67f-124">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2a67f-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2a67f-125">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2a67f-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a67f-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a67f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a67f-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a67f-127">See also</span></span>

- [<span data-ttu-id="2a67f-128">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="2a67f-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="2a67f-129">ICLRHostProtectionManager, interface</span><span class="sxs-lookup"><span data-stu-id="2a67f-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
