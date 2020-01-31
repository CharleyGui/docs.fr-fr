---
title: ICorDebugExceptionObjectCallStackEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
ms.openlocfilehash: 9d98bccdfb83cec547b185693c28f25017d3225f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782795"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="5abac-102">ICorDebugExceptionObjectCallStackEnum, interface</span><span class="sxs-lookup"><span data-stu-id="5abac-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="5abac-103">Fournit un énumérateur pour les informations de la pile des appels qui sont incorporées dans un objet exception.</span><span class="sxs-lookup"><span data-stu-id="5abac-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="5abac-104">Cette interface est une sous-classe de l'interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="5abac-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5abac-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5abac-105">Methods</span></span>  
  
|<span data-ttu-id="5abac-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="5abac-106">Method</span></span>|<span data-ttu-id="5abac-107">Description</span><span class="sxs-lookup"><span data-stu-id="5abac-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5abac-108">ICorDebugExceptionObjectCallStackEnum::Next</span><span class="sxs-lookup"><span data-stu-id="5abac-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="5abac-109">Obtient un nombre spécifié d’objets [cordebugexceptionobjectstackframe,](cordebugexceptionobjectstackframe-structure.md) qui contiennent des informations sur la pile des appels d’un objet exception.</span><span class="sxs-lookup"><span data-stu-id="5abac-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5abac-110">Notes</span><span class="sxs-lookup"><span data-stu-id="5abac-110">Remarks</span></span>  
 <span data-ttu-id="5abac-111">L’interface `ICorDebugExceptionObjectCallStackEnum` implémente l’interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="5abac-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="5abac-112">Une instance `ICorDebugExceptionObjectCallStackEnum` est remplie avec des objets [cordebugexceptionobjectstackframe,](cordebugexceptionobjectstackframe-structure.md) en appelant la méthode [Icordebugexceptionobjectvalue, :: enumerateexceptioncallstack,](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5abac-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="5abac-113">Les éléments de la pile des appels de la collection peuvent être énumérés en appelant la méthode [icordebugexceptionobjectcallstackenum, :: Next](icordebugexceptionobjectcallstackenum-next-method.md)</span><span class="sxs-lookup"><span data-stu-id="5abac-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5abac-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="5abac-114">Requirements</span></span>  
 <span data-ttu-id="5abac-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5abac-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5abac-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5abac-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5abac-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5abac-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5abac-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5abac-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5abac-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5abac-119">See also</span></span>

- [<span data-ttu-id="5abac-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5abac-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5abac-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="5abac-121">Debugging</span></span>](index.md)
