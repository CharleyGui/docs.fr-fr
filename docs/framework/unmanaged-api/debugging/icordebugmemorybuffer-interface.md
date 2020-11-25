---
title: ICorDebugMemoryBuffer, interface
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
ms.openlocfilehash: 2765852309401d2aa30f91b506ba55156cd8a3e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710731"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="56e34-102">ICorDebugMemoryBuffer, interface</span><span class="sxs-lookup"><span data-stu-id="56e34-102">ICorDebugMemoryBuffer Interface</span></span>

<span data-ttu-id="56e34-103">Représente une mémoire tampon en mémoire.</span><span class="sxs-lookup"><span data-stu-id="56e34-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="56e34-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="56e34-104">Methods</span></span>  
  
|<span data-ttu-id="56e34-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="56e34-105">Method</span></span>|<span data-ttu-id="56e34-106">Description</span><span class="sxs-lookup"><span data-stu-id="56e34-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="56e34-107">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="56e34-107">GetSize Method</span></span>](icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="56e34-108">Obtient la taille de la mémoire tampon en octets.</span><span class="sxs-lookup"><span data-stu-id="56e34-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="56e34-109">GetStartAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="56e34-109">GetStartAddress Method</span></span>](icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="56e34-110">Obtient l'adresse de départ de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="56e34-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56e34-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="56e34-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56e34-112">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="56e34-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="56e34-113">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="56e34-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56e34-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="56e34-114">Requirements</span></span>  

 <span data-ttu-id="56e34-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56e34-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56e34-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56e34-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56e34-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56e34-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56e34-118">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56e34-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56e34-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56e34-119">See also</span></span>

- [<span data-ttu-id="56e34-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="56e34-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="56e34-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="56e34-121">Debugging</span></span>](index.md)
