---
title: ICorDebugFunction3, interface
ms.date: 03/30/2017
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
ms.openlocfilehash: 8c9c507f00780d5ef5c5aeb28a1b10493351f37e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546970"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="11964-102">ICorDebugFunction3, interface</span><span class="sxs-lookup"><span data-stu-id="11964-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="11964-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="11964-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="11964-104">Étend logiquement l’interface ICorDebugFunction pour fournir un accès au code d’une demande ReJIT.</span><span class="sxs-lookup"><span data-stu-id="11964-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="11964-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="11964-105">Methods</span></span>  
  
|<span data-ttu-id="11964-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="11964-106">Method</span></span>|<span data-ttu-id="11964-107">Description</span><span class="sxs-lookup"><span data-stu-id="11964-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="11964-108">GetActiveReJitRequestILCode, méthode</span><span class="sxs-lookup"><span data-stu-id="11964-108">GetActiveReJitRequestILCode Method</span></span>](icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="11964-109">Obtient un pointeur d’interface vers un [ICorDebugILCode](icordebugilcode-interface.md) qui contient le langage intermédiaire d’une requête ReJIT active.</span><span class="sxs-lookup"><span data-stu-id="11964-109">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11964-110">Notes</span><span class="sxs-lookup"><span data-stu-id="11964-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11964-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="11964-111">Requirements</span></span>  
 <span data-ttu-id="11964-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11964-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11964-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11964-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11964-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11964-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11964-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11964-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11964-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11964-116">See also</span></span>

- [<span data-ttu-id="11964-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="11964-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="11964-118">Débogage</span><span class="sxs-lookup"><span data-stu-id="11964-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="11964-119">ReJIT : Guide pratique</span><span class="sxs-lookup"><span data-stu-id="11964-119">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
