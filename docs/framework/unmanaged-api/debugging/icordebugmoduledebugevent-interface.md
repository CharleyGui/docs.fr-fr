---
title: ICorDebugModuleDebugEvent, interface
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: 62d419a193cff000e1dd748d0cbb6b61775a81aa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695814"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="efa01-102">ICorDebugModuleDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="efa01-102">ICorDebugModuleDebugEvent Interface</span></span>

<span data-ttu-id="efa01-103">Étend l’interface [ICorDebugDebugEvent](icordebugdebugevent-interface.md) pour prendre en charge les événements au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="efa01-103">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="efa01-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="efa01-104">Methods</span></span>  
  
|<span data-ttu-id="efa01-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="efa01-105">Method</span></span>|<span data-ttu-id="efa01-106">Description</span><span class="sxs-lookup"><span data-stu-id="efa01-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="efa01-107">GetModule, méthode</span><span class="sxs-lookup"><span data-stu-id="efa01-107">GetModule Method</span></span>](icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="efa01-108">Obtient le module fusionné qui vient d’être chargé ou déchargé.</span><span class="sxs-lookup"><span data-stu-id="efa01-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="efa01-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="efa01-109">Remarks</span></span>  

 <span data-ttu-id="efa01-110">Les types d’événements [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) et [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) implémentent cette interface.</span><span class="sxs-lookup"><span data-stu-id="efa01-110">The [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="efa01-111">L'interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="efa01-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="efa01-112">Une tentative d'appel à `QueryInterface` pour récupérer un pointeur d'interface retourne `E_NOINTERFACE` pour les scénarios ICorDebug en dehors de .NET Native.</span><span class="sxs-lookup"><span data-stu-id="efa01-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efa01-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="efa01-113">Requirements</span></span>  

 <span data-ttu-id="efa01-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efa01-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efa01-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="efa01-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="efa01-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efa01-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efa01-117">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efa01-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efa01-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efa01-118">See also</span></span>

- [<span data-ttu-id="efa01-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="efa01-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="efa01-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="efa01-120">Debugging</span></span>](index.md)
