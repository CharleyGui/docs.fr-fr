---
title: ICorDebugModule, interface
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
ms.openlocfilehash: 105e56f2508eabbb6876a09d35e6abfbfc08950b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212241"
---
# <a name="icordebugmodule-interface"></a><span data-ttu-id="d0037-102">ICorDebugModule, interface</span><span class="sxs-lookup"><span data-stu-id="d0037-102">ICorDebugModule Interface</span></span>

<span data-ttu-id="d0037-103">Représente un module common language runtime (CLR), qui est un fichier exécutable ou une bibliothèque de liens dynamiques (DLL).</span><span class="sxs-lookup"><span data-stu-id="d0037-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0037-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d0037-104">Methods</span></span>  
  
|<span data-ttu-id="d0037-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d0037-105">Method</span></span>|<span data-ttu-id="d0037-106">Description</span><span class="sxs-lookup"><span data-stu-id="d0037-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0037-107">CreateBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="d0037-107">CreateBreakpoint Method</span></span>](icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="d0037-108">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="d0037-108">Not implemented.</span></span>|  
|[<span data-ttu-id="d0037-109">EnableClassLoadCallbacks, méthode</span><span class="sxs-lookup"><span data-stu-id="d0037-109">EnableClassLoadCallbacks Method</span></span>](icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="d0037-110">Détermine si les rappels [ICorDebugManagedCallback :: LoadClass](icordebugmanagedcallback-loadclass-method.md) et [ICorDebugManagedCallback :: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) sont appelés pour ce module.</span><span class="sxs-lookup"><span data-stu-id="d0037-110">Determines whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="d0037-111">EnableJITDebugging, méthode</span><span class="sxs-lookup"><span data-stu-id="d0037-111">EnableJITDebugging Method</span></span>](icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="d0037-112">Détermine si le compilateur juste-à-temps (JIT) préserve les informations de débogage pour les méthodes dans ce module.</span><span class="sxs-lookup"><span data-stu-id="d0037-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="d0037-113">GetAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="d0037-113">GetAssembly Method</span></span>](icordebugmodule-getassembly-method.md)|<span data-ttu-id="d0037-114">Obtient l’assembly conteneur pour ce module.</span><span class="sxs-lookup"><span data-stu-id="d0037-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="d0037-115">GetBaseAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="d0037-115">GetBaseAddress Method</span></span>](icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="d0037-116">Obtient l’adresse de base du module.</span><span class="sxs-lookup"><span data-stu-id="d0037-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="d0037-117">GetClassFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="d0037-117">GetClassFromToken Method</span></span>](icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="d0037-118">Obtient la ICorDebugClass à partir des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d0037-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="d0037-119">GetEditAndContinueSnapshot, méthode</span><span class="sxs-lookup"><span data-stu-id="d0037-119">GetEditAndContinueSnapshot Method</span></span>](icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="d0037-120">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="d0037-120">Deprecated.</span></span>|  
|[<span data-ttu-id="d0037-121">GetFunctionFromRVA, méthode</span><span class="sxs-lookup"><span data-stu-id="d0037-121">GetFunctionFromRVA Method</span></span>](icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="d0037-122">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="d0037-122">Not implemented.</span></span>|  
|[<span data-ttu-id="d0037-123">GetFunctionFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="d0037-123">GetFunctionFromToken Method</span></span>](icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="d0037-124">Obtient la fonction spécifiée par le jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d0037-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="d0037-125">GetGlobalVariableValue, méthode</span><span class="sxs-lookup"><span data-stu-id="d0037-125">GetGlobalVariableValue Method</span></span>](icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="d0037-126">Obtient un objet de valeur pour la variable globale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d0037-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="d0037-127">GetMetaDataInterface, méthode</span><span class="sxs-lookup"><span data-stu-id="d0037-127">GetMetaDataInterface Method</span></span>](icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="d0037-128">Obtient un pointeur d’interface de métadonnées qui peut être utilisé pour examiner les métadonnées du module.</span><span class="sxs-lookup"><span data-stu-id="d0037-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="d0037-129">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="d0037-129">GetName Method</span></span>](icordebugmodule-getname-method.md)|<span data-ttu-id="d0037-130">Obtient le nom de fichier du module.</span><span class="sxs-lookup"><span data-stu-id="d0037-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="d0037-131">GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="d0037-131">GetProcess Method</span></span>](icordebugmodule-getprocess-method.md)|<span data-ttu-id="d0037-132">Obtient le processus conteneur pour ce module.</span><span class="sxs-lookup"><span data-stu-id="d0037-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="d0037-133">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="d0037-133">GetSize Method</span></span>](icordebugmodule-getsize-method.md)|<span data-ttu-id="d0037-134">Obtient la taille du module en octets.</span><span class="sxs-lookup"><span data-stu-id="d0037-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="d0037-135">GetToken, méthode</span><span class="sxs-lookup"><span data-stu-id="d0037-135">GetToken Method</span></span>](icordebugmodule-gettoken-method.md)|<span data-ttu-id="d0037-136">Obtient le jeton pour l’entrée de table pour ce module.</span><span class="sxs-lookup"><span data-stu-id="d0037-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="d0037-137">IsDynamic, méthode</span><span class="sxs-lookup"><span data-stu-id="d0037-137">IsDynamic Method</span></span>](icordebugmodule-isdynamic-method.md)|<span data-ttu-id="d0037-138">Indique si le module est dynamique.</span><span class="sxs-lookup"><span data-stu-id="d0037-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="d0037-139">IsInMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="d0037-139">IsInMemory Method</span></span>](icordebugmodule-isinmemory-method.md)|<span data-ttu-id="d0037-140">Indique si ce module existe uniquement en mémoire.</span><span class="sxs-lookup"><span data-stu-id="d0037-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0037-141">Remarks</span><span class="sxs-lookup"><span data-stu-id="d0037-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0037-142">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="d0037-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0037-143">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d0037-143">Requirements</span></span>  
 <span data-ttu-id="d0037-144">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0037-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0037-145">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0037-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0037-146">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0037-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0037-147">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0037-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0037-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0037-148">See also</span></span>

- [<span data-ttu-id="d0037-149">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="d0037-149">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="d0037-150">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d0037-150">Debugging Interfaces</span></span>](debugging-interfaces.md)
