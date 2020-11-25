---
title: ICLRRuntimeHost::GetCLRControl, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCLRControl
helpviewer_keywords:
- ICLRRuntimeHost::GetCLRControl method [.NET Framework hosting]
- GetCLRControl method [.NET Framework hosting]
ms.assetid: e47e3655-efd5-4572-a1dc-50c69bf2a468
topic_type:
- apiref
ms.openlocfilehash: 928ac05fbd3a19a17e7f37674b2a75f8bc799fc6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728868"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="493f6-102">ICLRRuntimeHost::GetCLRControl, méthode</span><span class="sxs-lookup"><span data-stu-id="493f6-102">ICLRRuntimeHost::GetCLRControl Method</span></span>

<span data-ttu-id="493f6-103">Obtient un pointeur d’interface de type [interface ICLRControl](iclrcontrol-interface.md) que les hôtes peuvent utiliser pour personnaliser les aspects du Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="493f6-103">Gets an interface pointer of type [ICLRControl Interface](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="493f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="493f6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="493f6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="493f6-105">Parameters</span></span>  

 `pCLRControl`  
 <span data-ttu-id="493f6-106">à Pointeur d’interface de type [ICLRControl interface](iclrcontrol-interface.md) qui permet aux hôtes de configurer des aspects supplémentaires du CLR.</span><span class="sxs-lookup"><span data-stu-id="493f6-106">[out] An interface pointer of type [ICLRControl Interface](iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="493f6-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="493f6-107">Return Value</span></span>  
  
|<span data-ttu-id="493f6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="493f6-108">HRESULT</span></span>|<span data-ttu-id="493f6-109">Description</span><span class="sxs-lookup"><span data-stu-id="493f6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="493f6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="493f6-110">S_OK</span></span>|<span data-ttu-id="493f6-111">`GetCLRControl` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="493f6-111">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="493f6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="493f6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="493f6-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="493f6-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="493f6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="493f6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="493f6-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="493f6-115">The call timed out.</span></span>|  
|<span data-ttu-id="493f6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="493f6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="493f6-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="493f6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="493f6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="493f6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="493f6-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="493f6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="493f6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="493f6-120">E_FAIL</span></span>|<span data-ttu-id="493f6-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="493f6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="493f6-122">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="493f6-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="493f6-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="493f6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="493f6-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="493f6-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="493f6-125">Le CLR a déjà démarré.</span><span class="sxs-lookup"><span data-stu-id="493f6-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="493f6-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="493f6-126">Remarks</span></span>  

 <span data-ttu-id="493f6-127">`ICLRControl` fournit la méthode [GetCLRManager](iclrcontrol-getclrmanager-method.md) , qui permet à l’hôte d’afficher un pointeur d’interface vers l’un des types de gestionnaires.</span><span class="sxs-lookup"><span data-stu-id="493f6-127">`ICLRControl` provides the [GetCLRManager Method](iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="493f6-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="493f6-128">Requirements</span></span>  

 <span data-ttu-id="493f6-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="493f6-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="493f6-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="493f6-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="493f6-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="493f6-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="493f6-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="493f6-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="493f6-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="493f6-133">See also</span></span>

- [<span data-ttu-id="493f6-134">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="493f6-134">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="493f6-135">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="493f6-135">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
