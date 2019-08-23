---
title: ICorDebugMergedAssemblyRecord, interface
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8fd7a5f630bcf97277a4f98f2408ecaf04883fa3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916987"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="1939e-102">ICorDebugMergedAssemblyRecord, interface</span><span class="sxs-lookup"><span data-stu-id="1939e-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="1939e-103">Fournit des informations sur un assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="1939e-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1939e-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="1939e-104">Methods</span></span>  
  
|<span data-ttu-id="1939e-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="1939e-105">Method</span></span>|<span data-ttu-id="1939e-106">Description</span><span class="sxs-lookup"><span data-stu-id="1939e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1939e-107">GetCulture, méthode</span><span class="sxs-lookup"><span data-stu-id="1939e-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="1939e-108">Obtient la chaîne de nom de culture de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="1939e-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="1939e-109">GetIndex, méthode</span><span class="sxs-lookup"><span data-stu-id="1939e-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="1939e-110">Obtient l'index de préfixe de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="1939e-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="1939e-111">GetPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="1939e-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="1939e-112">Obtient la clé publique de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="1939e-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="1939e-113">GetPublicKeyToken, méthode</span><span class="sxs-lookup"><span data-stu-id="1939e-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="1939e-114">Obtient le jeton de clé publique de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="1939e-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="1939e-115">GetSimpleName, méthode</span><span class="sxs-lookup"><span data-stu-id="1939e-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="1939e-116">Obtient le nom simple de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="1939e-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="1939e-117">GetVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="1939e-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="1939e-118">Obtient les informations de version de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="1939e-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1939e-119">Notes</span><span class="sxs-lookup"><span data-stu-id="1939e-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1939e-120">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1939e-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="1939e-121">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="1939e-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1939e-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1939e-122">Requirements</span></span>  
 <span data-ttu-id="1939e-123">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1939e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1939e-124">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1939e-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1939e-125">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1939e-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1939e-126">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1939e-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1939e-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1939e-127">See also</span></span>

- [<span data-ttu-id="1939e-128">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1939e-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1939e-129">Débogage</span><span class="sxs-lookup"><span data-stu-id="1939e-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
