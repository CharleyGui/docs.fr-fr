---
title: ICorDebugMergedAssemblyRecord::GetIndex, méthode
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca304b90cee291ef86e225c2b0691631833e53a2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917950"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="41dac-102">ICorDebugMergedAssemblyRecord::GetIndex, méthode</span><span class="sxs-lookup"><span data-stu-id="41dac-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="41dac-103">Obtient l'index de préfixe de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="41dac-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41dac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41dac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41dac-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="41dac-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="41dac-106">[out] Pointeur vers l'index de préfixe.</span><span class="sxs-lookup"><span data-stu-id="41dac-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41dac-107">Notes</span><span class="sxs-lookup"><span data-stu-id="41dac-107">Remarks</span></span>  
 <span data-ttu-id="41dac-108">L'index de préfixe est utilisé pour empêcher les collisions de noms dans les noms de types de métadonnées fusionnées.</span><span class="sxs-lookup"><span data-stu-id="41dac-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41dac-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="41dac-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41dac-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="41dac-110">Requirements</span></span>  
 <span data-ttu-id="41dac-111">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41dac-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41dac-112">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="41dac-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41dac-113">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41dac-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41dac-114">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41dac-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41dac-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41dac-115">See also</span></span>

- [<span data-ttu-id="41dac-116">ICorDebugMergedAssemblyRecord, interface</span><span class="sxs-lookup"><span data-stu-id="41dac-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="41dac-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="41dac-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
