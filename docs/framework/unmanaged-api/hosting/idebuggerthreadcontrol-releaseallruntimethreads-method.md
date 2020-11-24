---
title: IDebuggerThreadControl::ReleaseAllRuntimeThreads, méthode
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type:
- apiref
ms.openlocfilehash: 490648ab8883b1dba257b82c0d0fa3c8e4783814
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684159"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="22895-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="22895-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>

<span data-ttu-id="22895-103">Avertit l’hôte que les services de débogage sont sur le paragraphe de libérer tous les threads qui sont bloqués.</span><span class="sxs-lookup"><span data-stu-id="22895-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22895-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22895-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="22895-105">Notes</span><span class="sxs-lookup"><span data-stu-id="22895-105">Remarks</span></span>  

 <span data-ttu-id="22895-106">La `ReleaseAllRuntimeThreads` méthode ne sera jamais appelée sur un thread d’exécution.</span><span class="sxs-lookup"><span data-stu-id="22895-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="22895-107">Si un thread d’exécution est bloqué sur l’hôte, il doit le libérer maintenant.</span><span class="sxs-lookup"><span data-stu-id="22895-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22895-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="22895-108">Requirements</span></span>  

 <span data-ttu-id="22895-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22895-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22895-110">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="22895-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="22895-111">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="22895-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22895-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22895-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22895-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22895-113">See also</span></span>

- [<span data-ttu-id="22895-114">IDebuggerThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="22895-114">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
