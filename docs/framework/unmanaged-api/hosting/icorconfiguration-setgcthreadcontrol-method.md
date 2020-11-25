---
title: ICorConfiguration::SetGCThreadControl, méthode
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
ms.openlocfilehash: 28b012bbe3f8c11ecd0afb8b5905336bd99c349c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724024"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="62dd7-102">ICorConfiguration::SetGCThreadControl, méthode</span><span class="sxs-lookup"><span data-stu-id="62dd7-102">ICorConfiguration::SetGCThreadControl Method</span></span>

<span data-ttu-id="62dd7-103">Définit l’interface de rappel pour les threads de planification pour les tâches non-Runtime qui seraient sinon bloquées pour un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="62dd7-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62dd7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62dd7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62dd7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="62dd7-105">Parameters</span></span>  

 `pGCThreadControl`  
 <span data-ttu-id="62dd7-106">dans Pointeur vers un objet [IGCThreadControl](igcthreadcontrol-interface.md) qui avertit l’hôte de la suspension des threads pour les tâches qui ne sont pas au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="62dd7-106">[in] A pointer to an [IGCThreadControl](igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62dd7-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="62dd7-107">Remarks</span></span>  

 <span data-ttu-id="62dd7-108">L’hôte peut choisir dans le rappel [IGCThreadControl :: ThreadIsBlockingForSuspension](igcthreadcontrol-threadisblockingforsuspension-method.md) s’il faut replanifier un thread.</span><span class="sxs-lookup"><span data-stu-id="62dd7-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62dd7-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="62dd7-109">Requirements</span></span>  

 <span data-ttu-id="62dd7-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62dd7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62dd7-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="62dd7-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="62dd7-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="62dd7-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62dd7-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62dd7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62dd7-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62dd7-114">See also</span></span>

- [<span data-ttu-id="62dd7-115">ICorConfiguration, interface</span><span class="sxs-lookup"><span data-stu-id="62dd7-115">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
