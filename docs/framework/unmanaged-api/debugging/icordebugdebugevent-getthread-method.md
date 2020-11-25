---
title: ICorDebugDebugEvent::GetThread, méthode
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: ca6aba7897d9e97743d29db49bd058e140f84e6e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713585"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="24831-102">ICorDebugDebugEvent::GetThread, méthode</span><span class="sxs-lookup"><span data-stu-id="24831-102">ICorDebugDebugEvent::GetThread Method</span></span>

<span data-ttu-id="24831-103">Obtient le thread sur lequel l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="24831-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24831-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24831-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24831-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="24831-105">Parameters</span></span>  

 <span data-ttu-id="24831-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="24831-106">ppThread</span></span>  
 <span data-ttu-id="24831-107">[out] Pointeur vers l'adresse d'un objet ICorDebugThread qui représente le thread sur lequel l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="24831-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24831-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="24831-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24831-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="24831-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24831-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="24831-110">Requirements</span></span>  

 <span data-ttu-id="24831-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24831-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24831-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24831-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24831-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24831-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24831-114">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24831-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24831-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24831-115">See also</span></span>

- [<span data-ttu-id="24831-116">ICorDebugDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="24831-116">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="24831-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="24831-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
