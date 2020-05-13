---
title: ICorDebugMemoryBuffer, interface
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
ms.openlocfilehash: 60f3b0c3230c524ca7d308d3cb80e50b0693715d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212332"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="f1f1c-102">ICorDebugMemoryBuffer, interface</span><span class="sxs-lookup"><span data-stu-id="f1f1c-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="f1f1c-103">Représente une mémoire tampon en mémoire.</span><span class="sxs-lookup"><span data-stu-id="f1f1c-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f1f1c-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f1f1c-104">Methods</span></span>  
  
|<span data-ttu-id="f1f1c-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f1f1c-105">Method</span></span>|<span data-ttu-id="f1f1c-106">Description</span><span class="sxs-lookup"><span data-stu-id="f1f1c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f1f1c-107">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="f1f1c-107">GetSize Method</span></span>](icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="f1f1c-108">Obtient la taille de la mémoire tampon en octets.</span><span class="sxs-lookup"><span data-stu-id="f1f1c-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="f1f1c-109">GetStartAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="f1f1c-109">GetStartAddress Method</span></span>](icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="f1f1c-110">Obtient l'adresse de départ de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="f1f1c-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1f1c-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="f1f1c-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1f1c-112">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f1f1c-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="f1f1c-113">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="f1f1c-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1f1c-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f1f1c-114">Requirements</span></span>  
 <span data-ttu-id="f1f1c-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1f1c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1f1c-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1f1c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1f1c-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1f1c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1f1c-118">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1f1c-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1f1c-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1f1c-119">See also</span></span>

- [<span data-ttu-id="f1f1c-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f1f1c-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f1f1c-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="f1f1c-121">Debugging</span></span>](index.md)
