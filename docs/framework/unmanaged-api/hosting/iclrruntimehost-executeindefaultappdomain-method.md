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
ms.openlocfilehash: ed841d1b2ff346ebef668cbd96a58ddfe466b3b8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120445"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="014df-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="014df-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="014df-103">Appelle la méthode spécifiée du type spécifié dans l’assembly managé spécifié.</span><span class="sxs-lookup"><span data-stu-id="014df-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="014df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="014df-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,   
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="014df-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="014df-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="014df-106">dans Chemin d’accès à la <xref:System.Reflection.Assembly> qui définit le <xref:System.Type> dont la méthode doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="014df-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="014df-107">dans Nom de l' <xref:System.Type> qui définit la méthode à appeler.</span><span class="sxs-lookup"><span data-stu-id="014df-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="014df-108">dans Nom de la méthode à appeler.</span><span class="sxs-lookup"><span data-stu-id="014df-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="014df-109">dans Paramètre de chaîne à passer à la méthode.</span><span class="sxs-lookup"><span data-stu-id="014df-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="014df-110">à Valeur entière retournée par la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="014df-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="014df-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="014df-111">Return Value</span></span>  
  
|<span data-ttu-id="014df-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="014df-112">HRESULT</span></span>|<span data-ttu-id="014df-113">Description</span><span class="sxs-lookup"><span data-stu-id="014df-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="014df-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="014df-114">S_OK</span></span>|<span data-ttu-id="014df-115">`ExecuteInDefaultAppDomain` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="014df-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="014df-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="014df-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="014df-117">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="014df-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="014df-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="014df-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="014df-119">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="014df-119">The call timed out.</span></span>|  
|<span data-ttu-id="014df-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="014df-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="014df-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="014df-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="014df-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="014df-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="014df-123">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="014df-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="014df-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="014df-124">E_FAIL</span></span>|<span data-ttu-id="014df-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="014df-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="014df-126">Si une méthode retourne E_FAIL, la liste de révocation de certificats n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="014df-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="014df-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="014df-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="014df-128">Notes</span><span class="sxs-lookup"><span data-stu-id="014df-128">Remarks</span></span>  
 <span data-ttu-id="014df-129">La méthode appelée doit avoir la signature suivante :</span><span class="sxs-lookup"><span data-stu-id="014df-129">The invoked method must have the following signature:</span></span>  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="014df-130">où `pwzMethodName` représente le nom de la méthode appelée, et `pwzArgument` représente la valeur de chaîne transmise en tant que paramètre à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="014df-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="014df-131">Si la valeur HRESULT est définie sur S_OK, `pReturnValue` est défini sur la valeur entière retournée par la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="014df-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="014df-132">Dans le cas contraire, `pReturnValue` n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="014df-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="014df-133">spécifications</span><span class="sxs-lookup"><span data-stu-id="014df-133">Requirements</span></span>  
 <span data-ttu-id="014df-134">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="014df-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="014df-135">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="014df-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="014df-136">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="014df-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="014df-137">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="014df-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="014df-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="014df-138">See also</span></span>

- [<span data-ttu-id="014df-139">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="014df-139">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
