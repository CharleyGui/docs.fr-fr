---
title: ICorDebugMemoryBuffer::GetSize, méthode
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
ms.openlocfilehash: 51c13b67951c714d1aec602ffea22891328565a0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793187"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="1ee96-102">ICorDebugMemoryBuffer::GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="1ee96-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="1ee96-103">Obtient la taille de la mémoire tampon en octets.</span><span class="sxs-lookup"><span data-stu-id="1ee96-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ee96-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ee96-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ee96-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="1ee96-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="1ee96-106">[out] Pointeur vers la taille de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="1ee96-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ee96-107">Notes</span><span class="sxs-lookup"><span data-stu-id="1ee96-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ee96-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1ee96-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ee96-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="1ee96-109">Requirements</span></span>  
 <span data-ttu-id="1ee96-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ee96-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ee96-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ee96-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ee96-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ee96-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ee96-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ee96-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ee96-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ee96-114">See also</span></span>

- [<span data-ttu-id="1ee96-115">ICorDebugMemoryBuffer, interface</span><span class="sxs-lookup"><span data-stu-id="1ee96-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="1ee96-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1ee96-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
