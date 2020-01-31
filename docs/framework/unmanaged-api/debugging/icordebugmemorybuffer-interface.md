---
title: ICorDebugMemoryBuffer, interface
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
ms.openlocfilehash: fa1bbca1e771cbc2b3475891862875b97b9e7f90
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793138"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="4021f-102">ICorDebugMemoryBuffer, interface</span><span class="sxs-lookup"><span data-stu-id="4021f-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="4021f-103">Représente une mémoire tampon en mémoire.</span><span class="sxs-lookup"><span data-stu-id="4021f-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4021f-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4021f-104">Methods</span></span>  
  
|<span data-ttu-id="4021f-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="4021f-105">Method</span></span>|<span data-ttu-id="4021f-106">Description</span><span class="sxs-lookup"><span data-stu-id="4021f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4021f-107">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="4021f-107">GetSize Method</span></span>](icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="4021f-108">Obtient la taille de la mémoire tampon en octets.</span><span class="sxs-lookup"><span data-stu-id="4021f-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="4021f-109">GetStartAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="4021f-109">GetStartAddress Method</span></span>](icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="4021f-110">Obtient l'adresse de départ de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="4021f-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4021f-111">Notes</span><span class="sxs-lookup"><span data-stu-id="4021f-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4021f-112">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4021f-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="4021f-113">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="4021f-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4021f-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="4021f-114">Requirements</span></span>  
 <span data-ttu-id="4021f-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4021f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4021f-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4021f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4021f-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4021f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4021f-118">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4021f-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4021f-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4021f-119">See also</span></span>

- [<span data-ttu-id="4021f-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="4021f-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4021f-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="4021f-121">Debugging</span></span>](index.md)
