---
title: ICorConfiguration::SetGCHostControl, méthode
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCHostControl
helpviewer_keywords:
- ICorConfiguration::SetGCHostControl method [.NET Framework hosting]
- SetGCHostControl method [.NET Framework hosting]
ms.assetid: bca6bd79-e288-475a-aa46-6bf81541d966
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a23c2793dce5be459b3aa0f183179c584592c115
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779875"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="ba725-102">ICorConfiguration::SetGCHostControl, méthode</span><span class="sxs-lookup"><span data-stu-id="ba725-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="ba725-103">Définit l’interface de rappel à utiliser par le garbage collector de demander à l’hôte de modifier les limites de mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="ba725-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba725-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba725-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba725-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ba725-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="ba725-106">[in] Un pointeur vers un [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) objet qui permet au garbage collector de demander à l’hôte de modifier les limites de mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="ba725-106">[in] A pointer to an [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba725-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ba725-107">Requirements</span></span>  
 <span data-ttu-id="ba725-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba725-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba725-109">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ba725-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ba725-110">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ba725-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba725-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba725-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba725-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba725-112">See also</span></span>

- [<span data-ttu-id="ba725-113">ICorConfiguration, interface</span><span class="sxs-lookup"><span data-stu-id="ba725-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
