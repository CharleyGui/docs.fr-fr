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
ms.openlocfilehash: 070c52258b66dcc352f2beef81b9a0694b8301ce
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703288"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="0aa7d-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="0aa7d-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="0aa7d-103">Appelle la méthode spécifiée du type spécifié dans l’assembly managé spécifié.</span><span class="sxs-lookup"><span data-stu-id="0aa7d-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aa7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0aa7d-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0aa7d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0aa7d-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="0aa7d-106">dans Chemin d’accès au <xref:System.Reflection.Assembly> qui définit l' <xref:System.Type> objet dont la méthode doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="0aa7d-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="0aa7d-107">dans Nom de l’objet <xref:System.Type> qui définit la méthode à appeler.</span><span class="sxs-lookup"><span data-stu-id="0aa7d-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="0aa7d-108">dans Nom de la méthode à appeler.</span><span class="sxs-lookup"><span data-stu-id="0aa7d-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="0aa7d-109">dans Paramètre de chaîne à passer à la méthode.</span><span class="sxs-lookup"><span data-stu-id="0aa7d-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="0aa7d-110">à Valeur entière retournée par la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="0aa7d-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0aa7d-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0aa7d-111">Return Value</span></span>  
  
|<span data-ttu-id="0aa7d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0aa7d-112">HRESULT</span></span>|<span data-ttu-id="0aa7d-113">Description</span><span class="sxs-lookup"><span data-stu-id="0aa7d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0aa7d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="0aa7d-114">S_OK</span></span>|<span data-ttu-id="0aa7d-115">`ExecuteInDefaultAppDomain`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="0aa7d-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="0aa7d-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0aa7d-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0aa7d-117">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="0aa7d-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0aa7d-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0aa7d-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0aa7d-119">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="0aa7d-119">The call timed out.</span></span>|  
|<span data-ttu-id="0aa7d-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0aa7d-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0aa7d-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="0aa7d-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0aa7d-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0aa7d-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0aa7d-123">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="0aa7d-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0aa7d-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0aa7d-124">E_FAIL</span></span>|<span data-ttu-id="0aa7d-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="0aa7d-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0aa7d-126">Si une méthode retourne E_FAIL, la liste de révocation de certificats n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="0aa7d-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="0aa7d-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0aa7d-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0aa7d-128">Notes</span><span class="sxs-lookup"><span data-stu-id="0aa7d-128">Remarks</span></span>  
 <span data-ttu-id="0aa7d-129">La méthode appelée doit avoir la signature suivante :</span><span class="sxs-lookup"><span data-stu-id="0aa7d-129">The invoked method must have the following signature:</span></span>  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="0aa7d-130">où `pwzMethodName` représente le nom de la méthode appelée et `pwzArgument` représente la valeur de chaîne transmise en tant que paramètre à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="0aa7d-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="0aa7d-131">Si la valeur HRESULT est définie sur S_OK, `pReturnValue` est défini sur la valeur entière retournée par la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="0aa7d-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="0aa7d-132">Dans le cas contraire, `pReturnValue` n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="0aa7d-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aa7d-133">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="0aa7d-133">Requirements</span></span>  
 <span data-ttu-id="0aa7d-134">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0aa7d-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aa7d-135">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0aa7d-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0aa7d-136">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0aa7d-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0aa7d-137">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0aa7d-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aa7d-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0aa7d-138">See also</span></span>

- [<span data-ttu-id="0aa7d-139">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="0aa7d-139">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
