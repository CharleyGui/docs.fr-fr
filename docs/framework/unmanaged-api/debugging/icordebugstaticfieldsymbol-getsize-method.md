---
title: 'ICorDebugStaticFieldSymbol :: deméthode, méthode'
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
ms.openlocfilehash: 0fa9c519a40624dd8c5471231263d2430738af87
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131768"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="236f2-102">ICorDebugStaticFieldSymbol :: deméthode, méthode</span><span class="sxs-lookup"><span data-stu-id="236f2-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="236f2-103">Obtient la taille en octets du champ static.</span><span class="sxs-lookup"><span data-stu-id="236f2-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="236f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="236f2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="236f2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="236f2-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="236f2-106">[out] Pointeur vers la longueur du champ.</span><span class="sxs-lookup"><span data-stu-id="236f2-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="236f2-107">Notes</span><span class="sxs-lookup"><span data-stu-id="236f2-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="236f2-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="236f2-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="236f2-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="236f2-109">Requirements</span></span>  
 <span data-ttu-id="236f2-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="236f2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="236f2-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="236f2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="236f2-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="236f2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="236f2-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="236f2-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="236f2-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="236f2-114">See also</span></span>

- [<span data-ttu-id="236f2-115">ICorDebugStaticFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="236f2-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="236f2-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="236f2-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
