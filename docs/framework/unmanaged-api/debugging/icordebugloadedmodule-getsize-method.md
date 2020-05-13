---
title: ICorDebugLoadedModule::GetSize (méthode)
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: 6a1c8c94b3c45ac995501b84bb4a69d73e7db25b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209849"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="1a87c-102">ICorDebugLoadedModule::GetSize (méthode)</span><span class="sxs-lookup"><span data-stu-id="1a87c-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="1a87c-103">Obtient la taille en octets du module chargé.</span><span class="sxs-lookup"><span data-stu-id="1a87c-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a87c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a87c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a87c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1a87c-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="1a87c-106">[out] Pointeur vers le nombre d'octets dans le module chargé.</span><span class="sxs-lookup"><span data-stu-id="1a87c-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a87c-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="1a87c-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a87c-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1a87c-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a87c-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1a87c-109">Requirements</span></span>  
 <span data-ttu-id="1a87c-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a87c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a87c-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a87c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a87c-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a87c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a87c-113">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a87c-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a87c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a87c-114">See also</span></span>

- [<span data-ttu-id="1a87c-115">ICorDebugLoadedModule (interface)</span><span class="sxs-lookup"><span data-stu-id="1a87c-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="1a87c-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1a87c-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
