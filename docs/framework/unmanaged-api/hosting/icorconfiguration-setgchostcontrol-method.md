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
ms.openlocfilehash: 4824fcfc53bae6c81760a23f76e83fb8ae7efd79
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715808"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="a4e89-102">ICorConfiguration::SetGCHostControl, méthode</span><span class="sxs-lookup"><span data-stu-id="a4e89-102">ICorConfiguration::SetGCHostControl Method</span></span>

<span data-ttu-id="a4e89-103">Définit l’interface de rappel que le garbage collector doit utiliser pour demander à l’hôte de modifier les limites de la mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="a4e89-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4e89-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4e89-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4e89-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a4e89-105">Parameters</span></span>  

 `pGCHostControl`  
 <span data-ttu-id="a4e89-106">dans Pointeur vers un objet [IGCHostControl](igchostcontrol-interface.md) qui autorise le garbage collector à demander à l’hôte de modifier les limites de la mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="a4e89-106">[in] A pointer to an [IGCHostControl](igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4e89-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a4e89-107">Requirements</span></span>  

 <span data-ttu-id="a4e89-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4e89-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4e89-109">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a4e89-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a4e89-110">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a4e89-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4e89-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4e89-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4e89-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4e89-112">See also</span></span>

- [<span data-ttu-id="a4e89-113">ICorConfiguration, interface</span><span class="sxs-lookup"><span data-stu-id="a4e89-113">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
