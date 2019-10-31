---
title: 'Icordebuginstancefieldsymbol, :: deméthode, méthode'
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
ms.openlocfilehash: 71828cd8486e2ff09190d23473dbab303b92f933
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139030"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="0a947-102">Icordebuginstancefieldsymbol, :: deméthode, méthode</span><span class="sxs-lookup"><span data-stu-id="0a947-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="0a947-103">Obtient la taille en octets du champ d'instance.</span><span class="sxs-lookup"><span data-stu-id="0a947-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a947-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a947-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a947-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0a947-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="0a947-106">[out] Pointeur vers la longueur du champ.</span><span class="sxs-lookup"><span data-stu-id="0a947-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a947-107">Notes</span><span class="sxs-lookup"><span data-stu-id="0a947-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a947-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0a947-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a947-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="0a947-109">Requirements</span></span>  
 <span data-ttu-id="0a947-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a947-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a947-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a947-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a947-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a947-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a947-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a947-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a947-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a947-114">See also</span></span>

- [<span data-ttu-id="0a947-115">ICorDebugInstanceFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="0a947-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="0a947-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0a947-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
