---
title: ICorDebugMergedAssemblyRecord, interface
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: 721f6c1cf468b3b518d2ea213588ae2410249690
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208718"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="2d038-102">ICorDebugMergedAssemblyRecord, interface</span><span class="sxs-lookup"><span data-stu-id="2d038-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="2d038-103">Fournit des informations sur un assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="2d038-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2d038-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2d038-104">Methods</span></span>  
  
|<span data-ttu-id="2d038-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="2d038-105">Method</span></span>|<span data-ttu-id="2d038-106">Description</span><span class="sxs-lookup"><span data-stu-id="2d038-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2d038-107">GetCulture, méthode</span><span class="sxs-lookup"><span data-stu-id="2d038-107">GetCulture Method</span></span>](icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="2d038-108">Obtient la chaîne de nom de culture de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="2d038-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="2d038-109">GetIndex, méthode</span><span class="sxs-lookup"><span data-stu-id="2d038-109">GetIndex Method</span></span>](icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="2d038-110">Obtient l'index de préfixe de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="2d038-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="2d038-111">GetPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="2d038-111">GetPublicKey Method</span></span>](icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="2d038-112">Obtient la clé publique de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="2d038-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="2d038-113">GetPublicKeyToken, méthode</span><span class="sxs-lookup"><span data-stu-id="2d038-113">GetPublicKeyToken Method</span></span>](icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="2d038-114">Obtient le jeton de clé publique de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="2d038-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="2d038-115">GetSimpleName, méthode</span><span class="sxs-lookup"><span data-stu-id="2d038-115">GetSimpleName Method</span></span>](icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="2d038-116">Obtient le nom simple de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="2d038-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="2d038-117">GetVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="2d038-117">GetVersion Method</span></span>](icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="2d038-118">Obtient les informations de version de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="2d038-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d038-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="2d038-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d038-120">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2d038-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="2d038-121">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="2d038-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d038-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2d038-122">Requirements</span></span>  
 <span data-ttu-id="2d038-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d038-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d038-124">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d038-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d038-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d038-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d038-126">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d038-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d038-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d038-127">See also</span></span>

- [<span data-ttu-id="2d038-128">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="2d038-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2d038-129">Débogage</span><span class="sxs-lookup"><span data-stu-id="2d038-129">Debugging</span></span>](index.md)
