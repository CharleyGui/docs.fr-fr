---
title: IDebuggerThreadControl::ThreadIsBlockingForDebugger, méthode
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ThreadIsBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForDebugger
helpviewer_keywords:
- ThreadIsBlockingForDebugger method [.NET Framework hosting]
- IDebuggerThreadControl::ThreadIsBlockingForDebugger method [.NET Framework hosting]
ms.assetid: d4d7cb2d-69da-48b3-879a-1a8a68c9bfa8
topic_type:
- apiref
ms.openlocfilehash: 8c2741d7db60781fef12293f3be0b515a55b7885
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705505"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="5054c-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger, méthode</span><span class="sxs-lookup"><span data-stu-id="5054c-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>

<span data-ttu-id="5054c-103">Avertit l’hôte que le thread qui envoie ce rappel va être bloqué dans les services de débogage.</span><span class="sxs-lookup"><span data-stu-id="5054c-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5054c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5054c-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="5054c-105">Notes</span><span class="sxs-lookup"><span data-stu-id="5054c-105">Remarks</span></span>  

 <span data-ttu-id="5054c-106">La `ThreadIsBlockingForDebugger` méthode est toujours appelée sur un thread d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5054c-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="5054c-107">La `ThreadIsBlockingForDebugger` méthode donne à l’hôte la possibilité d’effectuer une autre action pendant que le thread se bloque.</span><span class="sxs-lookup"><span data-stu-id="5054c-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5054c-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5054c-108">Requirements</span></span>  

 <span data-ttu-id="5054c-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5054c-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5054c-110">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5054c-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5054c-111">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5054c-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5054c-112">**Versions du .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5054c-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5054c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5054c-113">See also</span></span>

- [<span data-ttu-id="5054c-114">IDebuggerThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="5054c-114">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
