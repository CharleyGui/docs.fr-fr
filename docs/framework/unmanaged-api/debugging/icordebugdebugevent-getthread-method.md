---
title: Méthode ICorDebugDebugEvent::GetThread
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: 0900ac2ae5bcf2141e720dad6efdf68d4fafaccc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793533"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="170df-102">Méthode ICorDebugDebugEvent::GetThread</span><span class="sxs-lookup"><span data-stu-id="170df-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="170df-103">Obtient le thread sur lequel l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="170df-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="170df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="170df-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="170df-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="170df-105">Parameters</span></span>  
 <span data-ttu-id="170df-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="170df-106">ppThread</span></span>  
 <span data-ttu-id="170df-107">[out] Pointeur vers l'adresse d'un objet ICorDebugThread qui représente le thread sur lequel l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="170df-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="170df-108">Notes</span><span class="sxs-lookup"><span data-stu-id="170df-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="170df-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="170df-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="170df-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="170df-110">Requirements</span></span>  
 <span data-ttu-id="170df-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="170df-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="170df-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="170df-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="170df-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="170df-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="170df-114">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="170df-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="170df-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="170df-115">See also</span></span>

- [<span data-ttu-id="170df-116">ICorDebugDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="170df-116">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="170df-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="170df-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
