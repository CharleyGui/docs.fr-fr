---
title: ICLRMetaHost::EnumerateInstalledRuntimes, méthode
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateInstalledRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes
helpviewer_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes method [.NET Framework hosting]
- EnumerateInstalledRuntimes method [.NET Framework hosting]
ms.assetid: 9e359384-0d3d-451c-807e-5d7fcebf2be7
topic_type:
- apiref
ms.openlocfilehash: 9415d5189edb901822abad9269e0150e7601a963
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140956"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="d289d-102">ICLRMetaHost::EnumerateInstalledRuntimes, méthode</span><span class="sxs-lookup"><span data-stu-id="d289d-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>
<span data-ttu-id="d289d-103">Retourne une énumération qui contient une interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) valide pour chaque version du Common Language Runtime (CLR) installé sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d289d-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d289d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d289d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d289d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d289d-105">Parameters</span></span>  
 `ppEnumerator`  
 <span data-ttu-id="d289d-106">à Énumération des interfaces [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) correspondant à chaque version du CLR installée sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d289d-106">[out] An enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d289d-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d289d-107">Return Value</span></span>  
 <span data-ttu-id="d289d-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d289d-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d289d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d289d-109">HRESULT</span></span>|<span data-ttu-id="d289d-110">Description</span><span class="sxs-lookup"><span data-stu-id="d289d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d289d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d289d-111">S_OK</span></span>|<span data-ttu-id="d289d-112">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="d289d-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="d289d-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="d289d-113">E_POINTER</span></span>|<span data-ttu-id="d289d-114">`ppEnumerator` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="d289d-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d289d-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="d289d-115">Requirements</span></span>  
 <span data-ttu-id="d289d-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d289d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d289d-117">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="d289d-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d289d-118">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d289d-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d289d-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d289d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d289d-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d289d-120">See also</span></span>

- [<span data-ttu-id="d289d-121">ICLRMetaHost, interface</span><span class="sxs-lookup"><span data-stu-id="d289d-121">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="d289d-122">Hébergement</span><span class="sxs-lookup"><span data-stu-id="d289d-122">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
