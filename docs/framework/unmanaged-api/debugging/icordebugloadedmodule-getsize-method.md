---
title: ICorDebugLoadedModule::GetSize (méthode)
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: 3f2f8a1721847b8f7b845c42aa3c91e032c2d474
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122643"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="c7d99-102">ICorDebugLoadedModule::GetSize (méthode)</span><span class="sxs-lookup"><span data-stu-id="c7d99-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="c7d99-103">Obtient la taille en octets du module chargé.</span><span class="sxs-lookup"><span data-stu-id="c7d99-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7d99-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7d99-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7d99-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c7d99-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="c7d99-106">[out] Pointeur vers le nombre d'octets dans le module chargé.</span><span class="sxs-lookup"><span data-stu-id="c7d99-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7d99-107">Notes</span><span class="sxs-lookup"><span data-stu-id="c7d99-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7d99-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c7d99-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7d99-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="c7d99-109">Requirements</span></span>  
 <span data-ttu-id="c7d99-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7d99-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7d99-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7d99-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7d99-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7d99-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7d99-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7d99-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d99-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7d99-114">See also</span></span>

- [<span data-ttu-id="c7d99-115">ICorDebugLoadedModule, interface</span><span class="sxs-lookup"><span data-stu-id="c7d99-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="c7d99-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c7d99-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
