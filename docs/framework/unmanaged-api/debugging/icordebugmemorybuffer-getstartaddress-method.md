---
title: 'ICorDebugMemoryBuffer :: Getstartaddress,, méthode'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: e2876398ceaf863bbb3c7e576d59b89c52f1bdaf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127986"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="1c2b6-102">ICorDebugMemoryBuffer :: Getstartaddress,, méthode</span><span class="sxs-lookup"><span data-stu-id="1c2b6-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="1c2b6-103">Obtient l'adresse de départ de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="1c2b6-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c2b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c2b6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c2b6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1c2b6-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="1c2b6-106">[out] Pointeur vers l'adresse de départ de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="1c2b6-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c2b6-107">Notes</span><span class="sxs-lookup"><span data-stu-id="1c2b6-107">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="1c2b6-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1c2b6-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c2b6-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="1c2b6-109">Requirements</span></span>  
 <span data-ttu-id="1c2b6-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c2b6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c2b6-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c2b6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c2b6-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c2b6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c2b6-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c2b6-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c2b6-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c2b6-114">See also</span></span>

- [<span data-ttu-id="1c2b6-115">ICorDebugMemoryBuffer, interface</span><span class="sxs-lookup"><span data-stu-id="1c2b6-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="1c2b6-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1c2b6-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
