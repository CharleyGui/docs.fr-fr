---
title: ICLRMetaHost::EnumerateLoadedRuntimes, méthode
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
ms.openlocfilehash: f89307ad7ed41f872ad66a99be03663ac1f30f13
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140974"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="ea863-102">ICLRMetaHost::EnumerateLoadedRuntimes, méthode</span><span class="sxs-lookup"><span data-stu-id="ea863-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="ea863-103">Retourne une énumération qui comprend un pointeur d’interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) valide pour chaque version du Common Language Runtime (CLR) qui est chargé dans un processus donné.</span><span class="sxs-lookup"><span data-stu-id="ea863-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="ea863-104">Cette méthode remplace la fonction [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) .</span><span class="sxs-lookup"><span data-stu-id="ea863-104">This method supersedes the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea863-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea863-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea863-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ea863-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="ea863-107">dans Handle du processus à examiner pour les runtimes chargés.</span><span class="sxs-lookup"><span data-stu-id="ea863-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="ea863-108">à Une <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> énumération d’interfaces [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) correspondant à chaque CLR chargé par le processus.</span><span class="sxs-lookup"><span data-stu-id="ea863-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea863-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ea863-109">Return Value</span></span>  
 <span data-ttu-id="ea863-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="ea863-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ea863-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ea863-111">HRESULT</span></span>|<span data-ttu-id="ea863-112">Description</span><span class="sxs-lookup"><span data-stu-id="ea863-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ea863-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ea863-113">S_OK</span></span>|<span data-ttu-id="ea863-114">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="ea863-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="ea863-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="ea863-115">E_POINTER</span></span>|<span data-ttu-id="ea863-116">`ppEnumerator` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="ea863-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea863-117">Notes</span><span class="sxs-lookup"><span data-stu-id="ea863-117">Remarks</span></span>  
 <span data-ttu-id="ea863-118">Cette méthode répertorie tous les runtimes chargés, même s’ils ont été chargés avec des fonctions déconseillées telles que [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="ea863-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea863-119">spécifications</span><span class="sxs-lookup"><span data-stu-id="ea863-119">Requirements</span></span>  
 <span data-ttu-id="ea863-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea863-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea863-121">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="ea863-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ea863-122">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ea863-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea863-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea863-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea863-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea863-124">See also</span></span>

- [<span data-ttu-id="ea863-125">ICLRMetaHost, interface</span><span class="sxs-lookup"><span data-stu-id="ea863-125">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="ea863-126">Hébergement</span><span class="sxs-lookup"><span data-stu-id="ea863-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
