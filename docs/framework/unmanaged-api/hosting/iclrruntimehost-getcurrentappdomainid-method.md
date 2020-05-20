---
title: ICLRRuntimeHost::GetCurrentAppDomainId, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCurrentAppDomainId
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId
helpviewer_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId method [.NET Framework hosting]
- GetCurrentAppDomainId method [.NET Framework hosting]
ms.assetid: 33800475-7815-4976-8aca-a1038761a2ef
topic_type:
- apiref
ms.openlocfilehash: 1c667b19ac4bfa0bea95b85cf099906e351e5b71
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703669"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="b3767-102">ICLRRuntimeHost::GetCurrentAppDomainId, méthode</span><span class="sxs-lookup"><span data-stu-id="b3767-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="b3767-103">Obtient l’identificateur numérique du en <xref:System.AppDomain> cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="b3767-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3767-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3767-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3767-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b3767-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="b3767-106">à Identificateur numérique du en cours d' <xref:System.AppDomain> exécution.</span><span class="sxs-lookup"><span data-stu-id="b3767-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3767-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b3767-107">Return Value</span></span>  
  
|<span data-ttu-id="b3767-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b3767-108">HRESULT</span></span>|<span data-ttu-id="b3767-109">Description</span><span class="sxs-lookup"><span data-stu-id="b3767-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b3767-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b3767-110">S_OK</span></span>|<span data-ttu-id="b3767-111">`GetCurrentAppDomainId`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="b3767-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="b3767-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b3767-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b3767-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="b3767-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b3767-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b3767-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b3767-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="b3767-115">The call timed out.</span></span>|  
|<span data-ttu-id="b3767-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b3767-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b3767-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="b3767-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b3767-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b3767-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b3767-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="b3767-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b3767-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b3767-120">E_FAIL</span></span>|<span data-ttu-id="b3767-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b3767-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b3767-122">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="b3767-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b3767-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b3767-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3767-124">Notes</span><span class="sxs-lookup"><span data-stu-id="b3767-124">Remarks</span></span>  
 <span data-ttu-id="b3767-125">Le `pdwAppDomainId` paramètre est défini sur la valeur de la <xref:System.AppDomain.Id%2A> propriété du <xref:System.AppDomain> dans lequel le thread actuel s’exécute.</span><span class="sxs-lookup"><span data-stu-id="b3767-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3767-126">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="b3767-126">Requirements</span></span>  
 <span data-ttu-id="b3767-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3767-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3767-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b3767-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3767-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b3767-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3767-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3767-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3767-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3767-131">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="b3767-132">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="b3767-132">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
