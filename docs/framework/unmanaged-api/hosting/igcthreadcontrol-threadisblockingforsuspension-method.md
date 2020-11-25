---
title: IGCThreadControl::ThreadIsBlockingForSuspension, méthode
ms.date: 03/30/2017
api_name:
- IGCThreadControl.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type:
- apiref
ms.openlocfilehash: 39834ba868a21ead3113f2f0d9157cd210d9798c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721645"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="a4704-102">IGCThreadControl::ThreadIsBlockingForSuspension, méthode</span><span class="sxs-lookup"><span data-stu-id="a4704-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>

<span data-ttu-id="a4704-103">Avertit l’hôte que le thread qui effectue l’appel est sur le présent bloqué, peut-être pour une garbage collection ou une autre suspension.</span><span class="sxs-lookup"><span data-stu-id="a4704-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4704-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4704-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="a4704-105">Notes</span><span class="sxs-lookup"><span data-stu-id="a4704-105">Remarks</span></span>  

 <span data-ttu-id="a4704-106">L’hôte peut choisir dans le `ThreadIsBlockingForSuspension` rappel s’il faut replanifier un thread.</span><span class="sxs-lookup"><span data-stu-id="a4704-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4704-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a4704-107">Requirements</span></span>  

 <span data-ttu-id="a4704-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4704-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4704-109">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a4704-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a4704-110">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a4704-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4704-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4704-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4704-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4704-112">See also</span></span>

- [<span data-ttu-id="a4704-113">IGCThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="a4704-113">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
