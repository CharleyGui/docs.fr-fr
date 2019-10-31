---
title: 'ICorDebugMemoryBuffer :: deméthode, méthode'
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
ms.openlocfilehash: 1693860abe99884ee443be0666dfb6b485a219a0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128007"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="83deb-102">ICorDebugMemoryBuffer :: deméthode, méthode</span><span class="sxs-lookup"><span data-stu-id="83deb-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="83deb-103">Obtient la taille de la mémoire tampon en octets.</span><span class="sxs-lookup"><span data-stu-id="83deb-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83deb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83deb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83deb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="83deb-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="83deb-106">[out] Pointeur vers la taille de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="83deb-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83deb-107">Notes</span><span class="sxs-lookup"><span data-stu-id="83deb-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="83deb-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="83deb-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83deb-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="83deb-109">Requirements</span></span>  
 <span data-ttu-id="83deb-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83deb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83deb-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83deb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83deb-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83deb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83deb-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83deb-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83deb-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83deb-114">See also</span></span>

- [<span data-ttu-id="83deb-115">ICorDebugMemoryBuffer, interface</span><span class="sxs-lookup"><span data-stu-id="83deb-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="83deb-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="83deb-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
