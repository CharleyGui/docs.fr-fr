---
title: ICorDebugInstanceFieldSymbol::GetOffset, méthode
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 453f691f414050905f5d73e201ebeed79e2aaf50
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910202"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="9fdfc-102">ICorDebugInstanceFieldSymbol::GetOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="9fdfc-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="9fdfc-103">Obtient l'offset en octets de ce champ d'instance dans sa classe parente.</span><span class="sxs-lookup"><span data-stu-id="9fdfc-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fdfc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fdfc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fdfc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9fdfc-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="9fdfc-106">Pointeur vers le nombre d'octets correspondant à l'offset de ce champ d'instance dans sa classe parente.</span><span class="sxs-lookup"><span data-stu-id="9fdfc-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fdfc-107">Notes</span><span class="sxs-lookup"><span data-stu-id="9fdfc-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9fdfc-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9fdfc-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fdfc-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9fdfc-109">Requirements</span></span>  
 <span data-ttu-id="9fdfc-110">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fdfc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fdfc-111">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9fdfc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9fdfc-112">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9fdfc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fdfc-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fdfc-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fdfc-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9fdfc-114">See also</span></span>

- [<span data-ttu-id="9fdfc-115">ICorDebugInstanceFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="9fdfc-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="9fdfc-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9fdfc-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
