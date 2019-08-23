---
title: ICorDebugVariableSymbol, interface
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fb2538894184c19bc107ce52cbef3ac86a97345
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967979"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="f8b81-102">ICorDebugVariableSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="f8b81-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="f8b81-103">Récupère les informations sur les symboles de débogage pour une variable.</span><span class="sxs-lookup"><span data-stu-id="f8b81-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8b81-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f8b81-104">Methods</span></span>  
  
|<span data-ttu-id="f8b81-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f8b81-105">Method</span></span>|<span data-ttu-id="f8b81-106">Description</span><span class="sxs-lookup"><span data-stu-id="f8b81-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8b81-107">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="f8b81-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="f8b81-108">Obtient le nom d'une variable.</span><span class="sxs-lookup"><span data-stu-id="f8b81-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="f8b81-109">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="f8b81-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="f8b81-110">Obtient la taille d'une variable en octets.</span><span class="sxs-lookup"><span data-stu-id="f8b81-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="f8b81-111">GetSlotIndex, méthode</span><span class="sxs-lookup"><span data-stu-id="f8b81-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="f8b81-112">Obtient l'index d'emplacement géré d'une variable locale.</span><span class="sxs-lookup"><span data-stu-id="f8b81-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="f8b81-113">GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="f8b81-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="f8b81-114">Obtient la valeur d'une variable sous forme d'un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="f8b81-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="f8b81-115">SetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="f8b81-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="f8b81-116">Affecte la valeur d'un tableau d'octets à une variable.</span><span class="sxs-lookup"><span data-stu-id="f8b81-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8b81-117">Notes</span><span class="sxs-lookup"><span data-stu-id="f8b81-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8b81-118">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f8b81-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="f8b81-119">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="f8b81-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8b81-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f8b81-120">Requirements</span></span>  
 <span data-ttu-id="f8b81-121">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8b81-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8b81-122">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f8b81-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8b81-123">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8b81-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8b81-124">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8b81-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8b81-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8b81-125">See also</span></span>

- [<span data-ttu-id="f8b81-126">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f8b81-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f8b81-127">Débogage</span><span class="sxs-lookup"><span data-stu-id="f8b81-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
