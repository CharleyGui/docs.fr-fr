---
title: ICorDebugLoadedModule::GetSize, méthode
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: f207cd1c612b6444a9512adaa356ac2d01de7b9f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788460"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="61a2d-102">ICorDebugLoadedModule::GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="61a2d-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="61a2d-103">Obtient la taille en octets du module chargé.</span><span class="sxs-lookup"><span data-stu-id="61a2d-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61a2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61a2d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61a2d-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="61a2d-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="61a2d-106">[out] Pointeur vers le nombre d'octets dans le module chargé.</span><span class="sxs-lookup"><span data-stu-id="61a2d-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61a2d-107">Notes</span><span class="sxs-lookup"><span data-stu-id="61a2d-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61a2d-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="61a2d-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61a2d-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="61a2d-109">Requirements</span></span>  
 <span data-ttu-id="61a2d-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61a2d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61a2d-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61a2d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61a2d-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61a2d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61a2d-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61a2d-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61a2d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61a2d-114">See also</span></span>

- [<span data-ttu-id="61a2d-115">ICorDebugLoadedModule, interface</span><span class="sxs-lookup"><span data-stu-id="61a2d-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="61a2d-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="61a2d-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
