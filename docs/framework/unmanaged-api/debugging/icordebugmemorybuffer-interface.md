---
title: ICorDebugMemoryBuffer, interface
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
ms.openlocfilehash: 9e43f9a2297eb56755c7a6bba73e994441cbfeaa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127977"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="b8efe-102">ICorDebugMemoryBuffer, interface</span><span class="sxs-lookup"><span data-stu-id="b8efe-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="b8efe-103">Représente une mémoire tampon en mémoire.</span><span class="sxs-lookup"><span data-stu-id="b8efe-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b8efe-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b8efe-104">Methods</span></span>  
  
|<span data-ttu-id="b8efe-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="b8efe-105">Method</span></span>|<span data-ttu-id="b8efe-106">Description</span><span class="sxs-lookup"><span data-stu-id="b8efe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b8efe-107">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="b8efe-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="b8efe-108">Obtient la taille de la mémoire tampon en octets.</span><span class="sxs-lookup"><span data-stu-id="b8efe-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="b8efe-109">GetStartAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="b8efe-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="b8efe-110">Obtient l'adresse de départ de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="b8efe-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8efe-111">Notes</span><span class="sxs-lookup"><span data-stu-id="b8efe-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8efe-112">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b8efe-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="b8efe-113">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="b8efe-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8efe-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="b8efe-114">Requirements</span></span>  
 <span data-ttu-id="b8efe-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8efe-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8efe-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8efe-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8efe-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8efe-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8efe-118">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8efe-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8efe-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8efe-119">See also</span></span>

- [<span data-ttu-id="b8efe-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="b8efe-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b8efe-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="b8efe-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
