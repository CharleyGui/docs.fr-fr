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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b116a1f422daa20a2b51f0a5fc12d6065c2a01e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779813"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="2319c-102">ICLRMetaHost::EnumerateInstalledRuntimes, méthode</span><span class="sxs-lookup"><span data-stu-id="2319c-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>
<span data-ttu-id="2319c-103">Retourne une énumération qui contient un élément valide [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pour chaque version du common language runtime (CLR) est installé sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2319c-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2319c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2319c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2319c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2319c-105">Parameters</span></span>  
 `ppEnumerator`  
 <span data-ttu-id="2319c-106">[out] Une énumération de [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces correspondant à chaque version du CLR qui est installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2319c-106">[out] An enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2319c-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2319c-107">Return Value</span></span>  
 <span data-ttu-id="2319c-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="2319c-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2319c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2319c-109">HRESULT</span></span>|<span data-ttu-id="2319c-110">Description</span><span class="sxs-lookup"><span data-stu-id="2319c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2319c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2319c-111">S_OK</span></span>|<span data-ttu-id="2319c-112">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="2319c-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="2319c-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="2319c-113">E_POINTER</span></span>|<span data-ttu-id="2319c-114">`ppEnumerator` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="2319c-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2319c-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2319c-115">Requirements</span></span>  
 <span data-ttu-id="2319c-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2319c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2319c-117">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2319c-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2319c-118">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2319c-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2319c-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2319c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2319c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2319c-120">See also</span></span>

- [<span data-ttu-id="2319c-121">ICLRMetaHost, interface</span><span class="sxs-lookup"><span data-stu-id="2319c-121">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="2319c-122">Hébergement</span><span class="sxs-lookup"><span data-stu-id="2319c-122">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
