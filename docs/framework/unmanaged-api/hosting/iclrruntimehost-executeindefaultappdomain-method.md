---
title: ICLRRuntimeHost::ExecuteInDefaultAppDomain, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type:
- apiref
ms.openlocfilehash: 1a1bc7609042422de876fe167a9e61655aaf62b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176407"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="c9db3-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="c9db3-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="c9db3-103">Appelle la méthode spécifiée du type spécifié dans l’assemblage géré spécifié.</span><span class="sxs-lookup"><span data-stu-id="c9db3-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9db3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9db3-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9db3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c9db3-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="c9db3-106">[dans] Le chemin <xref:System.Reflection.Assembly> vers celui <xref:System.Type> qui définit la méthode à invoquer.</span><span class="sxs-lookup"><span data-stu-id="c9db3-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="c9db3-107">[dans] Le nom <xref:System.Type> de celui qui définit la méthode à invoquer.</span><span class="sxs-lookup"><span data-stu-id="c9db3-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="c9db3-108">[dans] Le nom de la méthode à invoquer.</span><span class="sxs-lookup"><span data-stu-id="c9db3-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="c9db3-109">[dans] Le paramètre de chaîne pour passer à la méthode.</span><span class="sxs-lookup"><span data-stu-id="c9db3-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="c9db3-110">[out] La valeur de l’intégriste retournée par la méthode invoquée.</span><span class="sxs-lookup"><span data-stu-id="c9db3-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9db3-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c9db3-111">Return Value</span></span>  
  
|<span data-ttu-id="c9db3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9db3-112">HRESULT</span></span>|<span data-ttu-id="c9db3-113">Description</span><span class="sxs-lookup"><span data-stu-id="c9db3-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9db3-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9db3-114">S_OK</span></span>|<span data-ttu-id="c9db3-115">`ExecuteInDefaultAppDomain`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="c9db3-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="c9db3-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c9db3-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c9db3-117">L’heure courante de l’exécution de la langue (CLR) n’a pas été chargée dans un processus, ou le CLR est dans un état où il ne peut pas exécuter le code géré ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="c9db3-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c9db3-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c9db3-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c9db3-119">L’appel s’est fait chronométrer.</span><span class="sxs-lookup"><span data-stu-id="c9db3-119">The call timed out.</span></span>|  
|<span data-ttu-id="c9db3-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c9db3-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c9db3-121">L’appelant n’est pas propriétaire de la serrure.</span><span class="sxs-lookup"><span data-stu-id="c9db3-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c9db3-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c9db3-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c9db3-123">Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="c9db3-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c9db3-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c9db3-124">E_FAIL</span></span>|<span data-ttu-id="c9db3-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="c9db3-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c9db3-126">Si une méthode revient E_FAIL, la LCR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="c9db3-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="c9db3-127">Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c9db3-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9db3-128">Notes </span><span class="sxs-lookup"><span data-stu-id="c9db3-128">Remarks</span></span>  
 <span data-ttu-id="c9db3-129">La méthode invoquée doit avoir la signature suivante :</span><span class="sxs-lookup"><span data-stu-id="c9db3-129">The invoked method must have the following signature:</span></span>  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="c9db3-130">où `pwzMethodName` représente le nom de `pwzArgument` la méthode invoquée, et représente la valeur de la chaîne transmise comme paramètre à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="c9db3-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="c9db3-131">Si la valeur HRESULT est réglée `pReturnValue` pour S_OK, est réglée à la valeur integer retournée par la méthode invoquée.</span><span class="sxs-lookup"><span data-stu-id="c9db3-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="c9db3-132">Sinon, `pReturnValue` n’est pas fixé.</span><span class="sxs-lookup"><span data-stu-id="c9db3-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9db3-133">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c9db3-133">Requirements</span></span>  
 <span data-ttu-id="c9db3-134">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9db3-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9db3-135">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="c9db3-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9db3-136">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9db3-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9db3-137">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9db3-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9db3-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9db3-138">See also</span></span>

- [<span data-ttu-id="c9db3-139">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="c9db3-139">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
