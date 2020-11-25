---
title: ICorDebugNativeFrame, interface
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
ms.openlocfilehash: 043dc0fdd5218d7bc6b80428d1eb891b3f01ee8c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695528"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="1a57e-102">ICorDebugNativeFrame, interface</span><span class="sxs-lookup"><span data-stu-id="1a57e-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="1a57e-103">Implémentation spécialisée de ICorDebugFrame utilisée pour les frames natifs.</span><span class="sxs-lookup"><span data-stu-id="1a57e-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a57e-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="1a57e-104">Methods</span></span>  
  
|<span data-ttu-id="1a57e-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="1a57e-105">Method</span></span>|<span data-ttu-id="1a57e-106">Description</span><span class="sxs-lookup"><span data-stu-id="1a57e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1a57e-107">CanSetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="1a57e-107">CanSetIP Method</span></span>](icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="1a57e-108">Obtient une valeur qui indique s’il est possible de définir en toute sécurité le pointeur d’instruction à l’emplacement d’offset spécifié en code natif.</span><span class="sxs-lookup"><span data-stu-id="1a57e-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="1a57e-109">GetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="1a57e-109">GetIP Method</span></span>](icordebugnativeframe-getip-method.md)|<span data-ttu-id="1a57e-110">Obtient l’offset du frame de pile en code natif.</span><span class="sxs-lookup"><span data-stu-id="1a57e-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="1a57e-111">GetLocalDoubleRegisterValue, méthode</span><span class="sxs-lookup"><span data-stu-id="1a57e-111">GetLocalDoubleRegisterValue Method</span></span>](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="1a57e-112">Obtient un pointeur vers un ICorDebugValue qui représente la valeur d’un argument ou d’une variable locale stockée dans deux registres de mémoire d’un frame natif.</span><span class="sxs-lookup"><span data-stu-id="1a57e-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="1a57e-113">GetLocalMemoryRegisterValue, méthode</span><span class="sxs-lookup"><span data-stu-id="1a57e-113">GetLocalMemoryRegisterValue Method</span></span>](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="1a57e-114">Obtient un pointeur vers un `ICorDebugValue` qui représente la valeur d’une variable locale, dont les bits de poids faible sont stockés dans le registre spécifié et les bits élevés sont stockés à l’adresse mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1a57e-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="1a57e-115">GetLocalMemoryValue, méthode</span><span class="sxs-lookup"><span data-stu-id="1a57e-115">GetLocalMemoryValue Method</span></span>](icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="1a57e-116">Obtient un pointeur vers un `ICorDebugValue` qui représente la valeur d’une variable locale stockée à l’adresse mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1a57e-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="1a57e-117">GetLocalRegisterMemoryValue, méthode</span><span class="sxs-lookup"><span data-stu-id="1a57e-117">GetLocalRegisterMemoryValue Method</span></span>](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="1a57e-118">Obtient un pointeur vers un `ICorDebugValue` qui représente la valeur d’une variable locale, dont les bits élevés sont stockés dans le registre spécifié et les bits de poids faible sont stockés à l’adresse mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1a57e-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="1a57e-119">GetLocalRegisterValue, méthode</span><span class="sxs-lookup"><span data-stu-id="1a57e-119">GetLocalRegisterValue Method</span></span>](icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="1a57e-120">Obtient un pointeur vers un `ICorDebugValue` qui représente la valeur d’un argument ou d’une variable locale stockée dans le registre natif spécifié.</span><span class="sxs-lookup"><span data-stu-id="1a57e-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="1a57e-121">GetRegisterSet, méthode</span><span class="sxs-lookup"><span data-stu-id="1a57e-121">GetRegisterSet Method</span></span>](icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="1a57e-122">Obtient un pointeur vers un [ICorDebugRegisterSet](icordebugregisterset-interface.md) qui représente le jeu de registres pour ce `ICorDebugNativeFrame` .</span><span class="sxs-lookup"><span data-stu-id="1a57e-122">Gets a pointer to an [ICorDebugRegisterSet](icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="1a57e-123">SetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="1a57e-123">SetIP Method</span></span>](icordebugnativeframe-setip-method.md)|<span data-ttu-id="1a57e-124">Définit le pointeur d’instruction à l’emplacement d’offset spécifié en code natif.</span><span class="sxs-lookup"><span data-stu-id="1a57e-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a57e-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="1a57e-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a57e-126">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="1a57e-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a57e-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1a57e-127">Requirements</span></span>  

 <span data-ttu-id="1a57e-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a57e-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a57e-129">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a57e-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a57e-130">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a57e-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a57e-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a57e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a57e-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a57e-132">See also</span></span>

- [<span data-ttu-id="1a57e-133">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1a57e-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
