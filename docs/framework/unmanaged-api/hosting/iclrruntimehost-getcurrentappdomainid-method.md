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
ms.openlocfilehash: 1b7d321eec2bbc2beb47c5de034bb4ef5d534c9d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120466"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="581d1-102">ICLRRuntimeHost::GetCurrentAppDomainId, méthode</span><span class="sxs-lookup"><span data-stu-id="581d1-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="581d1-103">Obtient l’identificateur numérique du <xref:System.AppDomain> en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="581d1-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="581d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="581d1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="581d1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="581d1-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="581d1-106">à Identificateur numérique de l' <xref:System.AppDomain> en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="581d1-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="581d1-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="581d1-107">Return Value</span></span>  
  
|<span data-ttu-id="581d1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="581d1-108">HRESULT</span></span>|<span data-ttu-id="581d1-109">Description</span><span class="sxs-lookup"><span data-stu-id="581d1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="581d1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="581d1-110">S_OK</span></span>|<span data-ttu-id="581d1-111">`GetCurrentAppDomainId` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="581d1-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="581d1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="581d1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="581d1-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="581d1-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="581d1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="581d1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="581d1-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="581d1-115">The call timed out.</span></span>|  
|<span data-ttu-id="581d1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="581d1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="581d1-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="581d1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="581d1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="581d1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="581d1-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="581d1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="581d1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="581d1-120">E_FAIL</span></span>|<span data-ttu-id="581d1-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="581d1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="581d1-122">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="581d1-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="581d1-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="581d1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="581d1-124">Notes</span><span class="sxs-lookup"><span data-stu-id="581d1-124">Remarks</span></span>  
 <span data-ttu-id="581d1-125">Le paramètre `pdwAppDomainId` est défini sur la valeur de la propriété <xref:System.AppDomain.Id%2A> du <xref:System.AppDomain> dans lequel le thread actuel s’exécute.</span><span class="sxs-lookup"><span data-stu-id="581d1-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="581d1-126">spécifications</span><span class="sxs-lookup"><span data-stu-id="581d1-126">Requirements</span></span>  
 <span data-ttu-id="581d1-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="581d1-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="581d1-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="581d1-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="581d1-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="581d1-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="581d1-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="581d1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="581d1-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="581d1-131">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="581d1-132">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="581d1-132">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
