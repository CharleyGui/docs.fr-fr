---
title: ICLRRuntimeInfo::IsLoadable, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4937c86be434ef5e97ec72763b7c53d5435bcaf4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774020"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="3421c-102">ICLRRuntimeInfo::IsLoadable, méthode</span><span class="sxs-lookup"><span data-stu-id="3421c-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="3421c-103">Indique si le runtime associé à cette interface peut être chargé dans le processus actuel, en tenant compte autres runtimes qui peuvent déjà être chargées dans le processus.</span><span class="sxs-lookup"><span data-stu-id="3421c-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3421c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3421c-104">Syntax</span></span>  
  
```cpp  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3421c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3421c-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="3421c-106">[out] `true` si ce runtime a pu être chargé dans le processus en cours ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="3421c-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3421c-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3421c-107">Return Value</span></span>  
 <span data-ttu-id="3421c-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="3421c-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3421c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3421c-109">HRESULT</span></span>|<span data-ttu-id="3421c-110">Description</span><span class="sxs-lookup"><span data-stu-id="3421c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3421c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3421c-111">S_OK</span></span>|<span data-ttu-id="3421c-112">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="3421c-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="3421c-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="3421c-113">E_POINTER</span></span>|<span data-ttu-id="3421c-114">`pbLoadable` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="3421c-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3421c-115">Notes</span><span class="sxs-lookup"><span data-stu-id="3421c-115">Remarks</span></span>  
 <span data-ttu-id="3421c-116">Si un autre runtime est déjà chargé dans le processus et le runtime associé à cette interface peut être chargé pour l’exécution de côte à côte in-process, `pbLoadable` retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="3421c-116">If another runtime is already loaded into the process and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="3421c-117">Si les deux runtimes ne peut pas exécuter côte à côte in-process, `pbLoadable` retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="3421c-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="3421c-118">Par exemple, le common language runtime (CLR) version 4 peut s’exécuter côte à côte dans le même processus avec le CLR version 2.0 ou version 1.1 du CLR.</span><span class="sxs-lookup"><span data-stu-id="3421c-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="3421c-119">Toutefois, les version 1.1 et CLR version 2.0 ne peut pas exécuter côte à côte in-process.</span><span class="sxs-lookup"><span data-stu-id="3421c-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="3421c-120">Si aucun runtime n’est chargées dans le processus, cette méthode retourne toujours `true`.</span><span class="sxs-lookup"><span data-stu-id="3421c-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3421c-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3421c-121">Requirements</span></span>  
 <span data-ttu-id="3421c-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3421c-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3421c-123">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="3421c-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3421c-124">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3421c-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3421c-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3421c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3421c-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3421c-126">See also</span></span>

- [<span data-ttu-id="3421c-127">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="3421c-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="3421c-128">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="3421c-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="3421c-129">Hébergement</span><span class="sxs-lookup"><span data-stu-id="3421c-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
