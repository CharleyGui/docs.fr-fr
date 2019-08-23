---
title: ICorDebugLoadedModule::GetSize (méthode)
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3067cdee1d3a5df0ad5594bce581139431fd1846
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936873"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="7d2d6-102">ICorDebugLoadedModule::GetSize (méthode)</span><span class="sxs-lookup"><span data-stu-id="7d2d6-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="7d2d6-103">Obtient la taille en octets du module chargé.</span><span class="sxs-lookup"><span data-stu-id="7d2d6-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d2d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d2d6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d2d6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d2d6-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="7d2d6-106">[out] Pointeur vers le nombre d'octets dans le module chargé.</span><span class="sxs-lookup"><span data-stu-id="7d2d6-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d2d6-107">Notes</span><span class="sxs-lookup"><span data-stu-id="7d2d6-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d2d6-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7d2d6-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d2d6-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7d2d6-109">Requirements</span></span>  
 <span data-ttu-id="7d2d6-110">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d2d6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d2d6-111">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7d2d6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d2d6-112">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d2d6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d2d6-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d2d6-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d2d6-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d2d6-114">See also</span></span>

- [<span data-ttu-id="7d2d6-115">ICorDebugLoadedModule, interface</span><span class="sxs-lookup"><span data-stu-id="7d2d6-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="7d2d6-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="7d2d6-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
