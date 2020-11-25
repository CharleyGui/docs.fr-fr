---
title: ICorDebugMemoryBuffer::GetSize, méthode
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
ms.openlocfilehash: 7f5458dd12ca83c1a5190bbf7fab0f8e5d06a0e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710754"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="493ce-102">ICorDebugMemoryBuffer::GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="493ce-102">ICorDebugMemoryBuffer::GetSize Method</span></span>

<span data-ttu-id="493ce-103">Obtient la taille de la mémoire tampon en octets.</span><span class="sxs-lookup"><span data-stu-id="493ce-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="493ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="493ce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="493ce-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="493ce-105">Parameters</span></span>  

 `pcbBufferLength`  
 <span data-ttu-id="493ce-106">[out] Pointeur vers la taille de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="493ce-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="493ce-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="493ce-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="493ce-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="493ce-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="493ce-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="493ce-109">Requirements</span></span>  

 <span data-ttu-id="493ce-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="493ce-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="493ce-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="493ce-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="493ce-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="493ce-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="493ce-113">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="493ce-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="493ce-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="493ce-114">See also</span></span>

- [<span data-ttu-id="493ce-115">ICorDebugMemoryBuffer, interface</span><span class="sxs-lookup"><span data-stu-id="493ce-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="493ce-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="493ce-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
