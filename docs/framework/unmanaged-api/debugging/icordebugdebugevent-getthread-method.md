---
title: ICorDebugDebugEvent::GetThread, méthode
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f85dccd5b59610c52adcf685828984c9344fd49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911280"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="d7af8-102">ICorDebugDebugEvent::GetThread, méthode</span><span class="sxs-lookup"><span data-stu-id="d7af8-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="d7af8-103">Obtient le thread sur lequel l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="d7af8-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7af8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7af8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7af8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d7af8-105">Parameters</span></span>  
 <span data-ttu-id="d7af8-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="d7af8-106">ppThread</span></span>  
 <span data-ttu-id="d7af8-107">à Pointeur vers l’adresse d’un objet ICorDebugThread qui représente le thread sur lequel l’événement s’est produit.</span><span class="sxs-lookup"><span data-stu-id="d7af8-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7af8-108">Notes</span><span class="sxs-lookup"><span data-stu-id="d7af8-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7af8-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d7af8-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7af8-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d7af8-110">Requirements</span></span>  
 <span data-ttu-id="d7af8-111">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7af8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7af8-112">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d7af8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7af8-113">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7af8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7af8-114">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7af8-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7af8-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7af8-115">See also</span></span>

- [<span data-ttu-id="d7af8-116">ICorDebugDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="d7af8-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="d7af8-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d7af8-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
