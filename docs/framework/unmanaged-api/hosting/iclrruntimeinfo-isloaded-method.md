---
title: ICLRRuntimeInfo::IsLoaded, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoaded
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type:
- apiref
ms.openlocfilehash: 3275a69683a312340f35841815685066def10b23
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762524"
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="6528c-102">ICLRRuntimeInfo::IsLoaded, méthode</span><span class="sxs-lookup"><span data-stu-id="6528c-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="6528c-103">Indique si le common language runtime (CLR) associé à l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) est chargé dans un processus.</span><span class="sxs-lookup"><span data-stu-id="6528c-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="6528c-104">Un Runtime peut être chargé sans également être démarré.</span><span class="sxs-lookup"><span data-stu-id="6528c-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6528c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6528c-105">Syntax</span></span>  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6528c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6528c-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="6528c-107">dans Handle du processus.</span><span class="sxs-lookup"><span data-stu-id="6528c-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="6528c-108">[out] `true` Si le CLR est chargé dans le processus ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="6528c-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6528c-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6528c-109">Return Value</span></span>  
 <span data-ttu-id="6528c-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="6528c-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6528c-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6528c-111">HRESULT</span></span>|<span data-ttu-id="6528c-112">Description</span><span class="sxs-lookup"><span data-stu-id="6528c-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6528c-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="6528c-113">S_OK</span></span>|<span data-ttu-id="6528c-114">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="6528c-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="6528c-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="6528c-115">E_POINTER</span></span>|<span data-ttu-id="6528c-116">`pbLoaded` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="6528c-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6528c-117">Notes</span><span class="sxs-lookup"><span data-stu-id="6528c-117">Remarks</span></span>  
 <span data-ttu-id="6528c-118">Cette méthode est à compatibilité descendante avec les fonctions et interfaces suivantes :</span><span class="sxs-lookup"><span data-stu-id="6528c-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
- <span data-ttu-id="6528c-119">[ICorRuntimeHost](icorruntimehost-interface.md) , interface (dans l’API d’hébergement .NET Framework version 1).</span><span class="sxs-lookup"><span data-stu-id="6528c-119">[ICorRuntimeHost](icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
- <span data-ttu-id="6528c-120">[ICLRRuntimeHost](iclrruntimehost-interface.md) , interface (dans l’API d’hébergement .NET Framework 2,0).</span><span class="sxs-lookup"><span data-stu-id="6528c-120">[ICLRRuntimeHost](iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
- <span data-ttu-id="6528c-121">Fonctions déconseillées `CorBindTo*` (consultez [fonctions d’hébergement CLR dépréciées](deprecated-clr-hosting-functions.md) dans l’API d’hébergement .NET Framework 2,0).</span><span class="sxs-lookup"><span data-stu-id="6528c-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="6528c-122">Un hôte peut appeler l’une des fonctions dépréciées `CorBindTo*` , telles que la fonction [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) , pour instancier une version spécifique du CLR.</span><span class="sxs-lookup"><span data-stu-id="6528c-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="6528c-123">L’hôte peut ensuite appeler la méthode [ICLRMetaHost :: GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) et spécifier le même numéro de version pour obtenir une interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="6528c-123">The host could then call the [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="6528c-124">Si l’hôte appelle ensuite la `IsLoaded` méthode sur l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) retournée, `pbLoaded` retourne `true` ; sinon, il retourne `false` .</span><span class="sxs-lookup"><span data-stu-id="6528c-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6528c-125">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="6528c-125">Requirements</span></span>  
 <span data-ttu-id="6528c-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6528c-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6528c-127">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="6528c-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6528c-128">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6528c-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6528c-129">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6528c-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6528c-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6528c-130">See also</span></span>

- [<span data-ttu-id="6528c-131">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="6528c-131">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="6528c-132">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="6528c-132">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="6528c-133">Hébergement</span><span class="sxs-lookup"><span data-stu-id="6528c-133">Hosting</span></span>](index.md)
