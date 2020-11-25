---
title: ICLRHostProtectionManager::SetProtectedCategories, méthode
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetProtectedCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetProtectedCategories
helpviewer_keywords:
- SetProtectedCategories method [.NET Framework hosting]
- ICLRHostProtectionManager::SetProtectedCategories method [.NET Framework hosting]
ms.assetid: fa21dc7b-5da7-440b-b59e-9180e5181f9d
topic_type:
- apiref
ms.openlocfilehash: 0557a8f1c7c495950933a44cacd23ada8e84964e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730498"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="26130-102">ICLRHostProtectionManager::SetProtectedCategories, méthode</span><span class="sxs-lookup"><span data-stu-id="26130-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>

<span data-ttu-id="26130-103">Spécifie les catégories de types et de membres managés dont l’exécution doit être bloquée dans du code de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="26130-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26130-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26130-104">Syntax</span></span>  
  
```cpp  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26130-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="26130-105">Parameters</span></span>  

 `categories`  
 <span data-ttu-id="26130-106">dans Combinaison de valeurs [EApiCategories](eapicategories-enumeration.md) indiquant les catégories de types et de membres managés dont l’exécution doit être bloquée dans du code de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="26130-106">[in] A combination of [EApiCategories](eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26130-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="26130-107">Return Value</span></span>  
  
|<span data-ttu-id="26130-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="26130-108">HRESULT</span></span>|<span data-ttu-id="26130-109">Description</span><span class="sxs-lookup"><span data-stu-id="26130-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="26130-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="26130-110">S_OK</span></span>|<span data-ttu-id="26130-111">`SetProtectedCategories` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="26130-111">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="26130-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="26130-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="26130-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="26130-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="26130-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="26130-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="26130-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="26130-115">The call timed out.</span></span>|  
|<span data-ttu-id="26130-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="26130-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="26130-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="26130-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="26130-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="26130-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="26130-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="26130-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="26130-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="26130-120">E_FAIL</span></span>|<span data-ttu-id="26130-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="26130-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="26130-122">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="26130-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="26130-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="26130-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26130-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="26130-124">Remarks</span></span>  

 <span data-ttu-id="26130-125">Chaque `EApiCategories` valeur fait référence à une liste de types et de membres managés.</span><span class="sxs-lookup"><span data-stu-id="26130-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="26130-126">L' `EApiCategories` énumération et la `SetProtectedCategories` méthode sont directement liées à la <xref:System.Security.Permissions.HostProtectionAttribute> classe managée, qui est utilisée pour marquer les types et les membres managés qui exposent les fonctionnalités correspondant aux catégories décrites par `EApiCategories` .</span><span class="sxs-lookup"><span data-stu-id="26130-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="26130-127">Pour plus d’informations, consultez <xref:System.Security.Permissions.HostProtectionAttribute> et l' <xref:System.Security.Permissions.HostProtectionResource> énumération, qui correspond directement à `EApiCategories` .</span><span class="sxs-lookup"><span data-stu-id="26130-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26130-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="26130-128">Requirements</span></span>  

 <span data-ttu-id="26130-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26130-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26130-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="26130-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26130-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="26130-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26130-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26130-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26130-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26130-133">See also</span></span>

- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [<span data-ttu-id="26130-134">EApiCategories, énumération</span><span class="sxs-lookup"><span data-stu-id="26130-134">EApiCategories Enumeration</span></span>](eapicategories-enumeration.md)
- [<span data-ttu-id="26130-135">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="26130-135">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="26130-136">ICLRHostProtectionManager, interface</span><span class="sxs-lookup"><span data-stu-id="26130-136">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
