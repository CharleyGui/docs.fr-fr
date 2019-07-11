---
title: ICorDebugMemoryBuffer::GetSize, méthode
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0db104dbfa61b836aa01b99be45725ed4c04c798
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752782"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="2af72-102">ICorDebugMemoryBuffer::GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="2af72-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="2af72-103">Obtient la taille de la mémoire tampon en octets.</span><span class="sxs-lookup"><span data-stu-id="2af72-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2af72-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2af72-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2af72-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2af72-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="2af72-106">[out] Pointeur vers la taille de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="2af72-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2af72-107">Notes</span><span class="sxs-lookup"><span data-stu-id="2af72-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2af72-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2af72-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2af72-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2af72-109">Requirements</span></span>  
 <span data-ttu-id="2af72-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2af72-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2af72-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2af72-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2af72-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2af72-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2af72-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2af72-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2af72-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2af72-114">See also</span></span>

- [<span data-ttu-id="2af72-115">ICorDebugMemoryBuffer, interface</span><span class="sxs-lookup"><span data-stu-id="2af72-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="2af72-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="2af72-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
