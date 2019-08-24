---
title: 'ICorDebugMemoryBuffer:: Getstartaddress,, méthode'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1394624051baa9e7dd21e29788d5fab28332081b
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987545"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="1bda0-102">ICorDebugMemoryBuffer:: Getstartaddress,, méthode</span><span class="sxs-lookup"><span data-stu-id="1bda0-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="1bda0-103">Obtient l'adresse de départ de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="1bda0-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bda0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bda0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bda0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1bda0-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="1bda0-106">[out] Pointeur vers l'adresse de départ de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="1bda0-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bda0-107">Notes</span><span class="sxs-lookup"><span data-stu-id="1bda0-107">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="1bda0-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1bda0-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bda0-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1bda0-109">Requirements</span></span>  
 <span data-ttu-id="1bda0-110">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bda0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bda0-111">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1bda0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1bda0-112">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bda0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bda0-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bda0-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bda0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bda0-114">See also</span></span>

- [<span data-ttu-id="1bda0-115">ICorDebugMemoryBuffer, interface</span><span class="sxs-lookup"><span data-stu-id="1bda0-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="1bda0-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1bda0-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
