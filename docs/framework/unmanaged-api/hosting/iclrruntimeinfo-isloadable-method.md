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
ms.openlocfilehash: 2236e815211168d8e7105375b75f30128f7f209a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714965"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="08929-102">ICLRRuntimeInfo::IsLoadable, méthode</span><span class="sxs-lookup"><span data-stu-id="08929-102">ICLRRuntimeInfo::IsLoadable Method</span></span>

<span data-ttu-id="08929-103">Indique si le runtime associé à cette interface peut être chargé dans le processus en cours, en tenant compte d’autres runtimes qui peuvent déjà être chargés dans le processus.</span><span class="sxs-lookup"><span data-stu-id="08929-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08929-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08929-104">Syntax</span></span>  
  
```cpp  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08929-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="08929-105">Parameters</span></span>  

 `pbLoadable`  
 <span data-ttu-id="08929-106">[out] `true` Si ce runtime a pu être chargé dans le processus en cours ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="08929-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08929-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="08929-107">Return Value</span></span>  

 <span data-ttu-id="08929-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="08929-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="08929-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08929-109">HRESULT</span></span>|<span data-ttu-id="08929-110">Description</span><span class="sxs-lookup"><span data-stu-id="08929-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08929-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="08929-111">S_OK</span></span>|<span data-ttu-id="08929-112">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="08929-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="08929-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="08929-113">E_POINTER</span></span>|<span data-ttu-id="08929-114">`pbLoadable` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="08929-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08929-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="08929-115">Remarks</span></span>  

 <span data-ttu-id="08929-116">Si un autre Runtime est déjà chargé dans le processus et que le runtime associé à cette interface peut être chargé pour l’exécution côte à côte in-process, `pbLoadable` retourne `true` .</span><span class="sxs-lookup"><span data-stu-id="08929-116">If another runtime is already loaded into the process, and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="08929-117">Si les deux runtimes ne peuvent pas s’exécuter côte à côte in-process, `pbLoadable` retourne `false` .</span><span class="sxs-lookup"><span data-stu-id="08929-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="08929-118">Par exemple, le common language runtime (CLR) version 4 peut s’exécuter côte à côte dans le même processus avec CLR version 2,0 ou CLR version 1,1.</span><span class="sxs-lookup"><span data-stu-id="08929-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="08929-119">Toutefois, CLR version 1,1 et CLR version 2,0 ne peuvent pas s’exécuter côte à côte in-process.</span><span class="sxs-lookup"><span data-stu-id="08929-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="08929-120">Si aucun Runtime n’est chargé dans le processus, cette méthode retourne toujours `true` .</span><span class="sxs-lookup"><span data-stu-id="08929-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08929-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="08929-121">Requirements</span></span>  

 <span data-ttu-id="08929-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08929-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08929-123">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="08929-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="08929-124">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="08929-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08929-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08929-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08929-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08929-126">See also</span></span>

- [<span data-ttu-id="08929-127">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="08929-127">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="08929-128">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="08929-128">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="08929-129">Hébergement</span><span class="sxs-lookup"><span data-stu-id="08929-129">Hosting</span></span>](index.md)
