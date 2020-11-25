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
ms.openlocfilehash: 9ce4a5e042e838da8e9eba614f26e35b38af56c5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714131"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="cc7ca-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets, méthode</span><span class="sxs-lookup"><span data-stu-id="cc7ca-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>

<span data-ttu-id="cc7ca-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="cc7ca-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc7ca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc7ca-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="cc7ca-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="cc7ca-105">Return Value</span></span>  
  
|<span data-ttu-id="cc7ca-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cc7ca-106">HRESULT</span></span>|<span data-ttu-id="cc7ca-107">Description</span><span class="sxs-lookup"><span data-stu-id="cc7ca-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cc7ca-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="cc7ca-108">S_OK</span></span>|<span data-ttu-id="cc7ca-109">`SetEagerSerializeGrantSets` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="cc7ca-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="cc7ca-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cc7ca-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cc7ca-111">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="cc7ca-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cc7ca-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cc7ca-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cc7ca-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="cc7ca-113">The call timed out.</span></span>|  
|<span data-ttu-id="cc7ca-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cc7ca-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cc7ca-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="cc7ca-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cc7ca-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cc7ca-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cc7ca-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="cc7ca-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cc7ca-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cc7ca-118">E_FAIL</span></span>|<span data-ttu-id="cc7ca-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="cc7ca-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cc7ca-120">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="cc7ca-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cc7ca-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cc7ca-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cc7ca-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cc7ca-122">Requirements</span></span>  

 <span data-ttu-id="cc7ca-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc7ca-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc7ca-124">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cc7ca-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc7ca-125">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cc7ca-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc7ca-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc7ca-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc7ca-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc7ca-127">See also</span></span>

- [<span data-ttu-id="cc7ca-128">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="cc7ca-128">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="cc7ca-129">ICLRHostProtectionManager, interface</span><span class="sxs-lookup"><span data-stu-id="cc7ca-129">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
