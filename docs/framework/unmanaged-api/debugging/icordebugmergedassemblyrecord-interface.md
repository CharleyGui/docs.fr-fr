---
title: ICorDebugMergedAssemblyRecord, interface
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: 6d5d862110cd91e8ac81c96e50486be10c579903
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793069"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="9e7c1-102">ICorDebugMergedAssemblyRecord, interface</span><span class="sxs-lookup"><span data-stu-id="9e7c1-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="9e7c1-103">Fournit des informations sur un assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="9e7c1-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e7c1-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9e7c1-104">Methods</span></span>  
  
|<span data-ttu-id="9e7c1-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="9e7c1-105">Method</span></span>|<span data-ttu-id="9e7c1-106">Description</span><span class="sxs-lookup"><span data-stu-id="9e7c1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e7c1-107">GetCulture, méthode</span><span class="sxs-lookup"><span data-stu-id="9e7c1-107">GetCulture Method</span></span>](icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="9e7c1-108">Obtient la chaîne de nom de culture de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="9e7c1-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="9e7c1-109">GetIndex, méthode</span><span class="sxs-lookup"><span data-stu-id="9e7c1-109">GetIndex Method</span></span>](icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="9e7c1-110">Obtient l'index de préfixe de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="9e7c1-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="9e7c1-111">GetPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="9e7c1-111">GetPublicKey Method</span></span>](icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="9e7c1-112">Obtient la clé publique de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="9e7c1-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="9e7c1-113">GetPublicKeyToken, méthode</span><span class="sxs-lookup"><span data-stu-id="9e7c1-113">GetPublicKeyToken Method</span></span>](icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="9e7c1-114">Obtient le jeton de clé publique de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="9e7c1-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="9e7c1-115">GetSimpleName, méthode</span><span class="sxs-lookup"><span data-stu-id="9e7c1-115">GetSimpleName Method</span></span>](icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="9e7c1-116">Obtient le nom simple de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="9e7c1-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="9e7c1-117">GetVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="9e7c1-117">GetVersion Method</span></span>](icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="9e7c1-118">Obtient les informations de version de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="9e7c1-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e7c1-119">Notes</span><span class="sxs-lookup"><span data-stu-id="9e7c1-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e7c1-120">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9e7c1-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="9e7c1-121">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="9e7c1-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e7c1-122">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="9e7c1-122">Requirements</span></span>  
 <span data-ttu-id="9e7c1-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e7c1-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e7c1-124">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e7c1-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e7c1-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e7c1-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e7c1-126">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e7c1-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e7c1-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e7c1-127">See also</span></span>

- [<span data-ttu-id="9e7c1-128">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9e7c1-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9e7c1-129">Débogage</span><span class="sxs-lookup"><span data-stu-id="9e7c1-129">Debugging</span></span>](index.md)
