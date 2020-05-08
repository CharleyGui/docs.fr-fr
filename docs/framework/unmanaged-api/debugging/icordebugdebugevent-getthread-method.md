---
title: ICorDebugDebugEvent::GetThread, méthode
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: acce18517c105739417fc734b49ff004ca9546dc
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976376"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="80303-102">ICorDebugDebugEvent::GetThread, méthode</span><span class="sxs-lookup"><span data-stu-id="80303-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="80303-103">Obtient le thread sur lequel l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="80303-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80303-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80303-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80303-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="80303-105">Parameters</span></span>  
 <span data-ttu-id="80303-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="80303-106">ppThread</span></span>  
 <span data-ttu-id="80303-107">[out] Pointeur vers l'adresse d'un objet ICorDebugThread qui représente le thread sur lequel l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="80303-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80303-108">Notes </span><span class="sxs-lookup"><span data-stu-id="80303-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80303-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="80303-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80303-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="80303-110">Requirements</span></span>  
 <span data-ttu-id="80303-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80303-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80303-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80303-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80303-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80303-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80303-114">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80303-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80303-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80303-115">See also</span></span>

- [<span data-ttu-id="80303-116">ICorDebugDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="80303-116">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="80303-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="80303-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
