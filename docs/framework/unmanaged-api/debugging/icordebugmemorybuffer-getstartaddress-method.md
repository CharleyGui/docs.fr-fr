---
title: ICorDebugMemoryBuffer::GetStartAddress, méthode
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: 47369c744ee42fb03857a3e69063a04e4f509d0d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212345"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="5557b-102">ICorDebugMemoryBuffer::GetStartAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="5557b-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="5557b-103">Obtient l'adresse de départ de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="5557b-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5557b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5557b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5557b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5557b-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="5557b-106">[out] Pointeur vers l'adresse de départ de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="5557b-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5557b-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="5557b-107">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="5557b-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5557b-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5557b-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5557b-109">Requirements</span></span>  
 <span data-ttu-id="5557b-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5557b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5557b-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5557b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5557b-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5557b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5557b-113">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5557b-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5557b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5557b-114">See also</span></span>

- [<span data-ttu-id="5557b-115">ICorDebugMemoryBuffer, interface</span><span class="sxs-lookup"><span data-stu-id="5557b-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="5557b-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5557b-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
