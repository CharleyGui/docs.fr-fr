---
title: ICLRDebugging::OpenVirtualProcess, méthode
ms.date: 03/30/2017
api_name:
- ICLRDebugging.OpenVirtualProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type:
- apiref
ms.openlocfilehash: 2edd7f628e17c8dc6cbcbb577d06269ba8c64cb1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723536"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a><span data-ttu-id="083bc-102">ICLRDebugging::OpenVirtualProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="083bc-102">ICLRDebugging::OpenVirtualProcess Method</span></span>

<span data-ttu-id="083bc-103">Obtient l’interface ICorDebugProcess qui correspond à un module common language runtime (CLR) chargé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="083bc-103">Gets the ICorDebugProcess interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="083bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="083bc-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="083bc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="083bc-105">Parameters</span></span>  

 `moduleBaseAddress`  
 <span data-ttu-id="083bc-106">dans Adresse de base d’un module dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="083bc-106">[in] The base address of a module in the target process.</span></span> <span data-ttu-id="083bc-107">COR_E_NOT_CLR est retourné si le module spécifié n’est pas un module CLR.</span><span class="sxs-lookup"><span data-stu-id="083bc-107">COR_E_NOT_CLR will be returned if the specified module is not a CLR module.</span></span>  
  
 `pDataTarget`  
 <span data-ttu-id="083bc-108">dans Abstraction de cible de données qui permet au débogueur managé d’inspecter l’état du processus.</span><span class="sxs-lookup"><span data-stu-id="083bc-108">[in] A data target abstraction that allows the managed debugger to inspect process state.</span></span> <span data-ttu-id="083bc-109">Le débogueur doit implémenter l’interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="083bc-109">The debugger must implement the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="083bc-110">Vous devez implémenter l’interface [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) pour prendre en charge les scénarios où le CLR qui est débogué n’est pas installé localement sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="083bc-110">You should implement the [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface to support scenarios where the CLR that is being debugged is not installed locally on the computer.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="083bc-111">dans Interface de rappel de fournisseur de bibliothèque qui permet de localiser et de charger des bibliothèques de débogage spécifiques à la version à la demande.</span><span class="sxs-lookup"><span data-stu-id="083bc-111">[in] A library provider callback interface that allows version-specific debugging libraries to be located and loaded on demand.</span></span> <span data-ttu-id="083bc-112">Ce paramètre est obligatoire uniquement si `ppProcess` ou `pFlags` n’est pas `null` .</span><span class="sxs-lookup"><span data-stu-id="083bc-112">This parameter is required only if `ppProcess` or `pFlags` is not `null`.</span></span>  
  
 `pMaxDebuggerSupportedVersion`  
 <span data-ttu-id="083bc-113">dans Version la plus récente du CLR que ce débogueur peut déboguer.</span><span class="sxs-lookup"><span data-stu-id="083bc-113">[in] The highest version of the CLR that this debugger can debug.</span></span> <span data-ttu-id="083bc-114">Vous devez spécifier les versions majeure, mineure et de build de la dernière version du CLR que ce débogueur prend en charge, et définir le numéro de révision sur 65535 pour prendre en charge les futures versions de maintenance du CLR sur place.</span><span class="sxs-lookup"><span data-stu-id="083bc-114">You should specify the major, minor, and build versions from the latest CLR version this debugger supports, and set the revision number to 65535 to accommodate future in-place CLR servicing releases.</span></span>  
  
 `riidProcess`  
 <span data-ttu-id="083bc-115">dans ID de l’interface ICorDebugProcess à récupérer.</span><span class="sxs-lookup"><span data-stu-id="083bc-115">[in] The ID of the ICorDebugProcess interface to retrieve.</span></span> <span data-ttu-id="083bc-116">Actuellement, les seules valeurs acceptées sont IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 et IID_CORDEBUGPROCESS.</span><span class="sxs-lookup"><span data-stu-id="083bc-116">Currently, the only accepted values are IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2, and IID_CORDEBUGPROCESS.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="083bc-117">à Pointeur vers l’interface COM qui est identifiée par `riidProcess` .</span><span class="sxs-lookup"><span data-stu-id="083bc-117">[out] A pointer to the COM interface that is identified by `riidProcess`.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="083bc-118">[in, out] Version du CLR.</span><span class="sxs-lookup"><span data-stu-id="083bc-118">[in, out] The version of the CLR.</span></span> <span data-ttu-id="083bc-119">En entrée, cette valeur peut être `null` .</span><span class="sxs-lookup"><span data-stu-id="083bc-119">On input, this value can be `null`.</span></span> <span data-ttu-id="083bc-120">Il peut également pointer vers une structure [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) , auquel cas le champ de la structure `wStructVersion` doit être initialisé à 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="083bc-120">It can also point to a [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) structure, in which case the structure's `wStructVersion` field must be initialized to 0 (zero).</span></span>  
  
 <span data-ttu-id="083bc-121">Lors de la sortie, la structure retournée est `CLR_DEBUGGING_VERSION` renseignée avec les informations de version pour le CLR.</span><span class="sxs-lookup"><span data-stu-id="083bc-121">On output, the returned `CLR_DEBUGGING_VERSION` structure will be filled in with the version information for the CLR.</span></span>  
  
 `pdwFlags`  
 <span data-ttu-id="083bc-122">à Indicateurs d’information sur le runtime spécifié.</span><span class="sxs-lookup"><span data-stu-id="083bc-122">[out] Informational flags about the specified runtime.</span></span> <span data-ttu-id="083bc-123">Pour obtenir une description des indicateurs, consultez la rubrique [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="083bc-123">See the [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) topic for a description of the flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="083bc-124">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="083bc-124">Return Value</span></span>  

 <span data-ttu-id="083bc-125">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="083bc-125">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="083bc-126">HRESULT</span><span class="sxs-lookup"><span data-stu-id="083bc-126">HRESULT</span></span>|<span data-ttu-id="083bc-127">Description</span><span class="sxs-lookup"><span data-stu-id="083bc-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="083bc-128">S_OK</span><span class="sxs-lookup"><span data-stu-id="083bc-128">S_OK</span></span>|<span data-ttu-id="083bc-129">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="083bc-129">The method completed successfully.</span></span>|  
|<span data-ttu-id="083bc-130">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="083bc-130">E_POINTER</span></span>|<span data-ttu-id="083bc-131">`pDataTarget` a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="083bc-131">`pDataTarget` is `null`.</span></span>|  
|<span data-ttu-id="083bc-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span><span class="sxs-lookup"><span data-stu-id="083bc-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span></span>|<span data-ttu-id="083bc-133">Le rappel [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) retourne une erreur ou ne fournit pas de handle valide.</span><span class="sxs-lookup"><span data-stu-id="083bc-133">The [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) callback returns an error or does not provide a valid handle.</span></span>|  
|<span data-ttu-id="083bc-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="083bc-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span></span>|<span data-ttu-id="083bc-135">`pDataTarget` n’implémente pas les interfaces cibles de données requises pour cette version du Runtime.</span><span class="sxs-lookup"><span data-stu-id="083bc-135">`pDataTarget` does not implement the required data target interfaces for this version of the runtime.</span></span>|  
|<span data-ttu-id="083bc-136">CORDBG_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="083bc-136">CORDBG_E_NOT_CLR</span></span>|<span data-ttu-id="083bc-137">Le module indiqué n’est pas un module CLR.</span><span class="sxs-lookup"><span data-stu-id="083bc-137">The indicated module is not a CLR module.</span></span> <span data-ttu-id="083bc-138">Ce HRESULT est également retourné lorsqu’un module CLR ne peut pas être détecté parce que la mémoire a été endommagée, que le module n’est pas disponible ou que la version du CLR est ultérieure à la version du shim.</span><span class="sxs-lookup"><span data-stu-id="083bc-138">This HRESULT is also returned when a CLR module cannot be detected because memory has been corrupted, the module is not available, or the CLR version is later than the shim version.</span></span>|  
|<span data-ttu-id="083bc-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span><span class="sxs-lookup"><span data-stu-id="083bc-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span></span>|<span data-ttu-id="083bc-140">Cette version du runtime ne prend pas en charge ce modèle de débogage.</span><span class="sxs-lookup"><span data-stu-id="083bc-140">This runtime version does not support this debugging model.</span></span> <span data-ttu-id="083bc-141">Actuellement, le modèle de débogage n’est pas pris en charge par les versions CLR antérieures au .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="083bc-141">Currently, the debugging model is not supported by CLR versions before the .NET Framework 4.</span></span> <span data-ttu-id="083bc-142">Le `pwszVersion` paramètre de sortie est toujours défini sur la valeur correcte après cette erreur.</span><span class="sxs-lookup"><span data-stu-id="083bc-142">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="083bc-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span><span class="sxs-lookup"><span data-stu-id="083bc-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span></span>|<span data-ttu-id="083bc-144">La version du CLR est supérieure à la version que ce débogueur prétend prendre en charge.</span><span class="sxs-lookup"><span data-stu-id="083bc-144">The version of the CLR is greater than the version this debugger claims to support.</span></span> <span data-ttu-id="083bc-145">Le `pwszVersion` paramètre de sortie est toujours défini sur la valeur correcte après cette erreur.</span><span class="sxs-lookup"><span data-stu-id="083bc-145">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="083bc-146">E_NO_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="083bc-146">E_NO_INTERFACE</span></span>|<span data-ttu-id="083bc-147">L' `riidProcess` interface n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="083bc-147">The `riidProcess` interface is not available.</span></span>|  
|<span data-ttu-id="083bc-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span><span class="sxs-lookup"><span data-stu-id="083bc-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span></span>|<span data-ttu-id="083bc-149">La `CLR_DEBUGGING_VERSION` structure n’a pas de valeur reconnue pour `wStructVersion` .</span><span class="sxs-lookup"><span data-stu-id="083bc-149">The `CLR_DEBUGGING_VERSION` structure does not have a recognized value for `wStructVersion`.</span></span> <span data-ttu-id="083bc-150">La seule valeur acceptée pour l’instant est 0.</span><span class="sxs-lookup"><span data-stu-id="083bc-150">The only accepted value at this time is 0.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="083bc-151">Exceptions</span><span class="sxs-lookup"><span data-stu-id="083bc-151">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="083bc-152">Remarques</span><span class="sxs-lookup"><span data-stu-id="083bc-152">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="083bc-153">Spécifications</span><span class="sxs-lookup"><span data-stu-id="083bc-153">Requirements</span></span>  

 <span data-ttu-id="083bc-154">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="083bc-154">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="083bc-155">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="083bc-155">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="083bc-156">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="083bc-156">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="083bc-157">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="083bc-157">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="083bc-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="083bc-158">See also</span></span>

- [<span data-ttu-id="083bc-159">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="083bc-159">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="083bc-160">Débogage</span><span class="sxs-lookup"><span data-stu-id="083bc-160">Debugging</span></span>](index.md)
