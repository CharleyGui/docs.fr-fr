---
title: ICorDebugStaticFieldSymbol::GetSize, méthode
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
ms.openlocfilehash: 34567247935588363d96b141717d7ec07bb76546
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677208"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="f13d2-102">ICorDebugStaticFieldSymbol::GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="f13d2-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>

<span data-ttu-id="f13d2-103">Obtient la taille en octets du champ static.</span><span class="sxs-lookup"><span data-stu-id="f13d2-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f13d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f13d2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f13d2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f13d2-105">Parameters</span></span>  

 `pcbSize`  
 <span data-ttu-id="f13d2-106">[out] Pointeur vers la longueur du champ.</span><span class="sxs-lookup"><span data-stu-id="f13d2-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f13d2-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="f13d2-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f13d2-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f13d2-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f13d2-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f13d2-109">Requirements</span></span>  

 <span data-ttu-id="f13d2-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f13d2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f13d2-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f13d2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f13d2-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f13d2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f13d2-113">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f13d2-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f13d2-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f13d2-114">See also</span></span>

- [<span data-ttu-id="f13d2-115">ICorDebugStaticFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="f13d2-115">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="f13d2-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f13d2-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
