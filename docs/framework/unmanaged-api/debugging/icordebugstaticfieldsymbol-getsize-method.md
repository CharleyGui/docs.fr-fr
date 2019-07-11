---
title: ICorDebugStaticFieldSymbol::GetSize, méthode
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a30778a287b4115df552444549a92c006288005
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760753"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="96874-102">ICorDebugStaticFieldSymbol::GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="96874-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="96874-103">Obtient la taille en octets du champ static.</span><span class="sxs-lookup"><span data-stu-id="96874-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96874-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96874-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96874-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="96874-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="96874-106">[out] Pointeur vers la longueur du champ.</span><span class="sxs-lookup"><span data-stu-id="96874-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96874-107">Notes</span><span class="sxs-lookup"><span data-stu-id="96874-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96874-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="96874-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96874-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="96874-109">Requirements</span></span>  
 <span data-ttu-id="96874-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96874-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96874-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96874-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96874-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96874-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96874-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96874-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96874-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96874-114">See also</span></span>

- [<span data-ttu-id="96874-115">ICorDebugStaticFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="96874-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="96874-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="96874-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
