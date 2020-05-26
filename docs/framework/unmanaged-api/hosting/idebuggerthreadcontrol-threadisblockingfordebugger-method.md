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
ms.openlocfilehash: f7cdc3fe9d52db56d0280bc602d3a9f2f54e8246
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805253"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="0c8f9-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger, méthode</span><span class="sxs-lookup"><span data-stu-id="0c8f9-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="0c8f9-103">Avertit l’hôte que le thread qui envoie ce rappel va être bloqué dans les services de débogage.</span><span class="sxs-lookup"><span data-stu-id="0c8f9-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c8f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c8f9-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="0c8f9-105">Notes</span><span class="sxs-lookup"><span data-stu-id="0c8f9-105">Remarks</span></span>  
 <span data-ttu-id="0c8f9-106">La `ThreadIsBlockingForDebugger` méthode est toujours appelée sur un thread d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0c8f9-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="0c8f9-107">La `ThreadIsBlockingForDebugger` méthode donne à l’hôte la possibilité d’effectuer une autre action pendant que le thread se bloque.</span><span class="sxs-lookup"><span data-stu-id="0c8f9-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c8f9-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0c8f9-108">Requirements</span></span>  
 <span data-ttu-id="0c8f9-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c8f9-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c8f9-110">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0c8f9-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c8f9-111">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0c8f9-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c8f9-112">**Versions du .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c8f9-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c8f9-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c8f9-113">See also</span></span>

- [<span data-ttu-id="0c8f9-114">IDebuggerThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="0c8f9-114">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
