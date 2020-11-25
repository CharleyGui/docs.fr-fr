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
ms.openlocfilehash: 1c45faecdb8b95af8d9e981962151c2c5d071a4f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731889"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="e226a-102">ICorDebugExceptionObjectCallStackEnum, interface</span><span class="sxs-lookup"><span data-stu-id="e226a-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>

<span data-ttu-id="e226a-103">Fournit un énumérateur pour les informations de la pile des appels qui sont incorporées dans un objet exception.</span><span class="sxs-lookup"><span data-stu-id="e226a-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="e226a-104">Cette interface est une sous-classe de l'interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="e226a-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e226a-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e226a-105">Methods</span></span>  
  
|<span data-ttu-id="e226a-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="e226a-106">Method</span></span>|<span data-ttu-id="e226a-107">Description</span><span class="sxs-lookup"><span data-stu-id="e226a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e226a-108">Icordebugexceptionobjectcallstackenum, :: suivant</span><span class="sxs-lookup"><span data-stu-id="e226a-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="e226a-109">Obtient un nombre spécifié d’objets [cordebugexceptionobjectstackframe,](cordebugexceptionobjectstackframe-structure.md) qui contiennent des informations sur la pile des appels d’un objet exception.</span><span class="sxs-lookup"><span data-stu-id="e226a-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e226a-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="e226a-110">Remarks</span></span>  

 <span data-ttu-id="e226a-111">L' `ICorDebugExceptionObjectCallStackEnum` interface implémente l’interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="e226a-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="e226a-112">Une `ICorDebugExceptionObjectCallStackEnum` instance est remplie avec des objets [cordebugexceptionobjectstackframe,](cordebugexceptionobjectstackframe-structure.md) en appelant la méthode [icordebugexceptionobjectvalue, :: enumerateexceptioncallstack,](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e226a-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="e226a-113">Les éléments de la pile des appels de la collection peuvent être énumérés en appelant la méthode [icordebugexceptionobjectcallstackenum, :: Next](icordebugexceptionobjectcallstackenum-next-method.md)</span><span class="sxs-lookup"><span data-stu-id="e226a-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e226a-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e226a-114">Requirements</span></span>  

 <span data-ttu-id="e226a-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e226a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e226a-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e226a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e226a-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e226a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e226a-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e226a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e226a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e226a-119">See also</span></span>

- [<span data-ttu-id="e226a-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e226a-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e226a-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="e226a-121">Debugging</span></span>](index.md)
