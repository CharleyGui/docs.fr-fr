---
title: ICorDebugStaticFieldSymbol::GetSize, méthode
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d99e06c1093dbc67e9c1999e4b9ccabd6579340e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962661"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="be2bc-102">ICorDebugStaticFieldSymbol::GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="be2bc-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="be2bc-103">Obtient la taille en octets du champ static.</span><span class="sxs-lookup"><span data-stu-id="be2bc-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be2bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be2bc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be2bc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="be2bc-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="be2bc-106">[out] Pointeur vers la longueur du champ.</span><span class="sxs-lookup"><span data-stu-id="be2bc-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be2bc-107">Notes</span><span class="sxs-lookup"><span data-stu-id="be2bc-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be2bc-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="be2bc-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be2bc-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="be2bc-109">Requirements</span></span>  
 <span data-ttu-id="be2bc-110">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be2bc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be2bc-111">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="be2bc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be2bc-112">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be2bc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be2bc-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be2bc-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be2bc-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be2bc-114">See also</span></span>

- [<span data-ttu-id="be2bc-115">ICorDebugStaticFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="be2bc-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="be2bc-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="be2bc-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
