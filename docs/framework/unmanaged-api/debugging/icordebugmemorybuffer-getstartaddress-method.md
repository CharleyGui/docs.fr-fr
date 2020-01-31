---
title: ICorDebugMemoryBuffer::GetStartAddress, méthode
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: f2b09c847a6bf577b78c8155f85f07b93877fbe9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793165"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="15989-102">ICorDebugMemoryBuffer::GetStartAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="15989-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="15989-103">Obtient l'adresse de départ de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="15989-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15989-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15989-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15989-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="15989-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="15989-106">[out] Pointeur vers l'adresse de départ de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="15989-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15989-107">Notes</span><span class="sxs-lookup"><span data-stu-id="15989-107">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="15989-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="15989-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15989-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="15989-109">Requirements</span></span>  
 <span data-ttu-id="15989-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15989-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15989-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="15989-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15989-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15989-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15989-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15989-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15989-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15989-114">See also</span></span>

- [<span data-ttu-id="15989-115">ICorDebugMemoryBuffer, interface</span><span class="sxs-lookup"><span data-stu-id="15989-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="15989-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="15989-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
