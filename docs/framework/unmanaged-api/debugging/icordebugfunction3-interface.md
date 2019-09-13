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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3eebdf56796fe599ec6ff62d7008d1af3be796e
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926834"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="5c7a6-102">ICorDebugFunction3, interface</span><span class="sxs-lookup"><span data-stu-id="5c7a6-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="5c7a6-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="5c7a6-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="5c7a6-104">Étend logiquement l’interface ICorDebugFunction pour fournir l’accès au code à partir d’une demande ReJIT.</span><span class="sxs-lookup"><span data-stu-id="5c7a6-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5c7a6-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5c7a6-105">Methods</span></span>  
  
|<span data-ttu-id="5c7a6-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="5c7a6-106">Method</span></span>|<span data-ttu-id="5c7a6-107">Description</span><span class="sxs-lookup"><span data-stu-id="5c7a6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5c7a6-108">GetActiveReJitRequestILCode, méthode</span><span class="sxs-lookup"><span data-stu-id="5c7a6-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="5c7a6-109">Obtient un pointeur d’interface vers un [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) qui contient le langage intermédiaire d’une requête ReJIT active.</span><span class="sxs-lookup"><span data-stu-id="5c7a6-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c7a6-110">Notes</span><span class="sxs-lookup"><span data-stu-id="5c7a6-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c7a6-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5c7a6-111">Requirements</span></span>  
 <span data-ttu-id="5c7a6-112">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c7a6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c7a6-113">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5c7a6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c7a6-114">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c7a6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c7a6-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c7a6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c7a6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c7a6-116">See also</span></span>

- [<span data-ttu-id="5c7a6-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5c7a6-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5c7a6-118">Débogage</span><span class="sxs-lookup"><span data-stu-id="5c7a6-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="5c7a6-119">ReJIT Guide pratique</span><span class="sxs-lookup"><span data-stu-id="5c7a6-119">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
