---
title: ICorDebugLoadedModule::GetSize (méthode)
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: 2ed19cb4a190f2af7581a827e8bd11b748b3d4a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721320"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="9ba8a-102">ICorDebugLoadedModule::GetSize (méthode)</span><span class="sxs-lookup"><span data-stu-id="9ba8a-102">ICorDebugLoadedModule::GetSize Method</span></span>

<span data-ttu-id="9ba8a-103">Obtient la taille en octets du module chargé.</span><span class="sxs-lookup"><span data-stu-id="9ba8a-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ba8a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ba8a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ba8a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9ba8a-105">Parameters</span></span>  

 `pcBytes`  
 <span data-ttu-id="9ba8a-106">[out] Pointeur vers le nombre d'octets dans le module chargé.</span><span class="sxs-lookup"><span data-stu-id="9ba8a-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ba8a-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="9ba8a-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ba8a-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9ba8a-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ba8a-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9ba8a-109">Requirements</span></span>  

 <span data-ttu-id="9ba8a-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ba8a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ba8a-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ba8a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ba8a-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ba8a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ba8a-113">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ba8a-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ba8a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ba8a-114">See also</span></span>

- [<span data-ttu-id="9ba8a-115">ICorDebugLoadedModule (interface)</span><span class="sxs-lookup"><span data-stu-id="9ba8a-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="9ba8a-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9ba8a-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
