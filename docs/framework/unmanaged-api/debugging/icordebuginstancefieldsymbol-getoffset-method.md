---
title: 'Icordebuginstancefieldsymbol, :: GetOffset,, méthode'
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: 3886e29a1c2fd44fbe50d1eef722f99da7abdbe5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139011"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="1a812-102">Icordebuginstancefieldsymbol, :: GetOffset,, méthode</span><span class="sxs-lookup"><span data-stu-id="1a812-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="1a812-103">Obtient l'offset en octets de ce champ d'instance dans sa classe parente.</span><span class="sxs-lookup"><span data-stu-id="1a812-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a812-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a812-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a812-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1a812-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="1a812-106">Pointeur vers le nombre d'octets correspondant à l'offset de ce champ d'instance dans sa classe parente.</span><span class="sxs-lookup"><span data-stu-id="1a812-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a812-107">Notes</span><span class="sxs-lookup"><span data-stu-id="1a812-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a812-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1a812-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a812-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="1a812-109">Requirements</span></span>  
 <span data-ttu-id="1a812-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a812-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a812-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a812-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a812-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a812-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a812-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a812-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a812-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a812-114">See also</span></span>

- [<span data-ttu-id="1a812-115">ICorDebugInstanceFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="1a812-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="1a812-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1a812-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
