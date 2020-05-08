---
title: ICorDebugCode, interface
ms.date: 03/30/2017
api_name:
- ICorDebugCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode
helpviewer_keywords:
- ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type:
- apiref
ms.openlocfilehash: 3736627e7f42ad9db6699c31a0a618e993eef770
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893471"
---
# <a name="icordebugcode-interface"></a><span data-ttu-id="43c52-102">ICorDebugCode, interface</span><span class="sxs-lookup"><span data-stu-id="43c52-102">ICorDebugCode Interface</span></span>

<span data-ttu-id="43c52-103">Représente un segment de code MSIL ou de code natif.</span><span class="sxs-lookup"><span data-stu-id="43c52-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="43c52-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="43c52-104">Methods</span></span>  
  
|<span data-ttu-id="43c52-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="43c52-105">Method</span></span>|<span data-ttu-id="43c52-106">Description</span><span class="sxs-lookup"><span data-stu-id="43c52-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="43c52-107">CreateBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="43c52-107">CreateBreakpoint Method</span></span>](icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="43c52-108">Crée un point d’arrêt à l’offset spécifié.</span><span class="sxs-lookup"><span data-stu-id="43c52-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="43c52-109">GetAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="43c52-109">GetAddress Method</span></span>](icordebugcode-getaddress-method.md)|<span data-ttu-id="43c52-110">Obtient l’adresse virtuelle relative (RVA) du segment de code que ce `ICorDebugCode` représente.</span><span class="sxs-lookup"><span data-stu-id="43c52-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="43c52-111">GetCode, méthode</span><span class="sxs-lookup"><span data-stu-id="43c52-111">GetCode Method</span></span>](icordebugcode-getcode-method.md)|<span data-ttu-id="43c52-112">Obtient tout le code pour la fonction spécifiée, mis en forme pour le code machine.</span><span class="sxs-lookup"><span data-stu-id="43c52-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="43c52-113">Cette méthode a été dépréciée ; Utilisez [ICorDebugCode2 :: GetCodeChunks,](icordebugcode2-getcodechunks-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="43c52-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="43c52-114">GetEnCRemapSequencePoints, méthode</span><span class="sxs-lookup"><span data-stu-id="43c52-114">GetEnCRemapSequencePoints Method</span></span>](icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="43c52-115">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="43c52-115">Not implemented.</span></span>|  
|[<span data-ttu-id="43c52-116">GetFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="43c52-116">GetFunction Method</span></span>](icordebugcode-getfunction-method.md)|<span data-ttu-id="43c52-117">Obtient le « ICorDebugFunction » associé à ce `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="43c52-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="43c52-118">GetILToNativeMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="43c52-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="43c52-119">Obtient un tableau d’instances « COR_DEBUG_IL_TO_NATIVE_MAP » qui représentent les mappages des offsets MSIL aux offsets natifs.</span><span class="sxs-lookup"><span data-stu-id="43c52-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="43c52-120">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="43c52-120">GetSize Method</span></span>](icordebugcode-getsize-method.md)|<span data-ttu-id="43c52-121">Obtient la taille, en octets, du code binaire représenté par ce `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="43c52-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="43c52-122">GetVersionNumber, méthode</span><span class="sxs-lookup"><span data-stu-id="43c52-122">GetVersionNumber Method</span></span>](icordebugcode-getversionnumber-method.md)|<span data-ttu-id="43c52-123">Obtient le nombre de base 1 qui identifie la version du code que ce `ICorDebugCode` représente.</span><span class="sxs-lookup"><span data-stu-id="43c52-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="43c52-124">IsIL, méthode</span><span class="sxs-lookup"><span data-stu-id="43c52-124">IsIL Method</span></span>](icordebugcode-isil-method.md)|<span data-ttu-id="43c52-125">Obtient une valeur qui indique si ce `ICorDebugCode` est compilé en MSIL.</span><span class="sxs-lookup"><span data-stu-id="43c52-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43c52-126">Notes </span><span class="sxs-lookup"><span data-stu-id="43c52-126">Remarks</span></span>  
 <span data-ttu-id="43c52-127">`ICorDebugCode`peut représenter le code MSIL ou le code natif.</span><span class="sxs-lookup"><span data-stu-id="43c52-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="43c52-128">Un objet « ICorDebugFunction » qui représente le code MSIL peut avoir zéro ou un `ICorDebugCode` objet associé.</span><span class="sxs-lookup"><span data-stu-id="43c52-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="43c52-129">Un objet « ICorDebugFunction » qui représente du code natif peut avoir un nombre `ICorDebugCode` quelconque d’objets associés.</span><span class="sxs-lookup"><span data-stu-id="43c52-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43c52-130">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="43c52-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43c52-131">Spécifications</span><span class="sxs-lookup"><span data-stu-id="43c52-131">Requirements</span></span>  
 <span data-ttu-id="43c52-132">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43c52-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43c52-133">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43c52-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43c52-134">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43c52-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43c52-135">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43c52-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43c52-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43c52-136">See also</span></span>

- [<span data-ttu-id="43c52-137">ICorDebugCode3, interface</span><span class="sxs-lookup"><span data-stu-id="43c52-137">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="43c52-138">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="43c52-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
