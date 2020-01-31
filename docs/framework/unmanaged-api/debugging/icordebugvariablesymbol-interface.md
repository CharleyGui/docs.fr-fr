---
title: ICorDebugVariableSymbol, interface
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: 9d17bc92dcae9e906dfe18d7665fbf489d278234
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790870"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="b92a9-102">ICorDebugVariableSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="b92a9-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="b92a9-103">Récupère les informations sur les symboles de débogage pour une variable.</span><span class="sxs-lookup"><span data-stu-id="b92a9-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b92a9-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b92a9-104">Methods</span></span>  
  
|<span data-ttu-id="b92a9-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="b92a9-105">Method</span></span>|<span data-ttu-id="b92a9-106">Description</span><span class="sxs-lookup"><span data-stu-id="b92a9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b92a9-107">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="b92a9-107">GetName Method</span></span>](icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="b92a9-108">Obtient le nom d'une variable.</span><span class="sxs-lookup"><span data-stu-id="b92a9-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="b92a9-109">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="b92a9-109">GetSize Method</span></span>](icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="b92a9-110">Obtient la taille d'une variable en octets.</span><span class="sxs-lookup"><span data-stu-id="b92a9-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="b92a9-111">GetSlotIndex, méthode</span><span class="sxs-lookup"><span data-stu-id="b92a9-111">GetSlotIndex Method</span></span>](icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="b92a9-112">Obtient l'index d'emplacement géré d'une variable locale.</span><span class="sxs-lookup"><span data-stu-id="b92a9-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="b92a9-113">GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="b92a9-113">GetValue Method</span></span>](icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="b92a9-114">Obtient la valeur d'une variable sous forme d'un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="b92a9-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="b92a9-115">SetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="b92a9-115">SetValue Method</span></span>](icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="b92a9-116">Affecte la valeur d'un tableau d'octets à une variable.</span><span class="sxs-lookup"><span data-stu-id="b92a9-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b92a9-117">Notes</span><span class="sxs-lookup"><span data-stu-id="b92a9-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b92a9-118">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b92a9-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="b92a9-119">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="b92a9-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b92a9-120">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="b92a9-120">Requirements</span></span>  
 <span data-ttu-id="b92a9-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b92a9-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b92a9-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b92a9-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b92a9-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b92a9-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b92a9-124">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b92a9-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b92a9-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b92a9-125">See also</span></span>

- [<span data-ttu-id="b92a9-126">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="b92a9-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b92a9-127">Débogage</span><span class="sxs-lookup"><span data-stu-id="b92a9-127">Debugging</span></span>](index.md)
