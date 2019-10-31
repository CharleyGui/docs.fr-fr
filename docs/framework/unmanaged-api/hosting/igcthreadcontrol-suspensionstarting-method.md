---
title: IGCThreadControl::SuspensionStarting, méthode
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionStarting
helpviewer_keywords:
- IGCThreadControl::SuspensionStarting method [.NET Framework hosting]
- SuspensionStarting method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 0af312af-98e9-415e-b182-42e80a1aee51
topic_type:
- apiref
ms.openlocfilehash: 1e1d63ab28276f69e5b3a762520db8f8300d05bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134764"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="c0812-102">IGCThreadControl::SuspensionStarting, méthode</span><span class="sxs-lookup"><span data-stu-id="c0812-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="c0812-103">Indique à l’hôte que le runtime commence une suspension de thread pour une garbage collection ou une autre suspension.</span><span class="sxs-lookup"><span data-stu-id="c0812-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0812-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0812-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="c0812-105">Notes</span><span class="sxs-lookup"><span data-stu-id="c0812-105">Remarks</span></span>  
 <span data-ttu-id="c0812-106">Ne replanifiez pas de threads pendant le rappel `SuspensionStarting`.</span><span class="sxs-lookup"><span data-stu-id="c0812-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0812-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="c0812-107">Requirements</span></span>  
 <span data-ttu-id="c0812-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0812-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0812-109">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c0812-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c0812-110">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c0812-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c0812-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0812-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0812-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0812-112">See also</span></span>

- [<span data-ttu-id="c0812-113">IGCThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="c0812-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
