---
title: ICorDebugFunction, interface
ms.date: 03/30/2017
api_name:
- ICorDebugFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction
helpviewer_keywords:
- ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 550b85474c1ccd7e125549e86df906439caf410e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621495"
---
# <a name="icordebugfunction-interface"></a><span data-ttu-id="f6d08-102">ICorDebugFunction, interface</span><span class="sxs-lookup"><span data-stu-id="f6d08-102">ICorDebugFunction Interface</span></span>

<span data-ttu-id="f6d08-103">Représente une fonction ou une méthode managée.</span><span class="sxs-lookup"><span data-stu-id="f6d08-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f6d08-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f6d08-104">Methods</span></span>  
  
|<span data-ttu-id="f6d08-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f6d08-105">Method</span></span>|<span data-ttu-id="f6d08-106">Description</span><span class="sxs-lookup"><span data-stu-id="f6d08-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f6d08-107">CreateBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="f6d08-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="f6d08-108">Crée un point d’arrêt au début de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="f6d08-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="f6d08-109">GetClass, méthode</span><span class="sxs-lookup"><span data-stu-id="f6d08-109">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|<span data-ttu-id="f6d08-110">Obtient un objet ICorDebugClass qui représente la classe de que cette fonction est membre.</span><span class="sxs-lookup"><span data-stu-id="f6d08-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="f6d08-111">GetCurrentVersionNumber, méthode</span><span class="sxs-lookup"><span data-stu-id="f6d08-111">GetCurrentVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="f6d08-112">Obtient le numéro de version de la dernière modification apportée à cette fonction.</span><span class="sxs-lookup"><span data-stu-id="f6d08-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="f6d08-113">GetILCode, méthode</span><span class="sxs-lookup"><span data-stu-id="f6d08-113">GetILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|<span data-ttu-id="f6d08-114">Obtient le code de Microsoft intermediate language (MSIL) pour cette fonction.</span><span class="sxs-lookup"><span data-stu-id="f6d08-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="f6d08-115">GetLocalVarSigToken, méthode</span><span class="sxs-lookup"><span data-stu-id="f6d08-115">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="f6d08-116">Obtient les métadonnées de jeton pour la signature de variable locale de la fonction qui est représentée par ce `ICorDebugFunction` instance.</span><span class="sxs-lookup"><span data-stu-id="f6d08-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="f6d08-117">GetModule, méthode</span><span class="sxs-lookup"><span data-stu-id="f6d08-117">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="f6d08-118">Obtient le module dans lequel cette fonction est définie.</span><span class="sxs-lookup"><span data-stu-id="f6d08-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="f6d08-119">GetNativeCode, méthode</span><span class="sxs-lookup"><span data-stu-id="f6d08-119">GetNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|<span data-ttu-id="f6d08-120">Obtient le code natif pour cette fonction.</span><span class="sxs-lookup"><span data-stu-id="f6d08-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="f6d08-121">GetToken, méthode</span><span class="sxs-lookup"><span data-stu-id="f6d08-121">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|<span data-ttu-id="f6d08-122">Obtient les métadonnées de jeton pour cette fonction.</span><span class="sxs-lookup"><span data-stu-id="f6d08-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6d08-123">Notes</span><span class="sxs-lookup"><span data-stu-id="f6d08-123">Remarks</span></span>  
 <span data-ttu-id="f6d08-124">Le `ICorDebugFunction` interface ne représente pas une fonction avec des paramètres de type générique.</span><span class="sxs-lookup"><span data-stu-id="f6d08-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="f6d08-125">Par exemple, un `ICorDebugFunction` instance représenteraient `Func<T>` mais pas `Func<string>`.</span><span class="sxs-lookup"><span data-stu-id="f6d08-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="f6d08-126">Appelez [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) pour obtenir les paramètres de type générique.</span><span class="sxs-lookup"><span data-stu-id="f6d08-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="f6d08-127">La relation entre le jeton de métadonnées d’une méthode `mdMethodDef`et d’une méthode `ICorDebugFunction` objet dépend de si Modifier & Continuer est autorisé sur la fonction :</span><span class="sxs-lookup"><span data-stu-id="f6d08-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
- <span data-ttu-id="f6d08-128">Si Modifier & Continuer n’est pas autorisée sur la fonction, il existe une relation un à un entre le `ICorDebugFunction` objet et le `mdMethodDef` jeton.</span><span class="sxs-lookup"><span data-stu-id="f6d08-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="f6d08-129">Autrement dit, la fonction a un `ICorDebugFunction` objet et l’autre `mdMethodDef` jeton.</span><span class="sxs-lookup"><span data-stu-id="f6d08-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
- <span data-ttu-id="f6d08-130">Si Modifier & Continuer est autorisé sur la fonction, il existe une relation plusieurs-à-un entre le `ICorDebugFunction` objet et le `mdMethodDef` jeton.</span><span class="sxs-lookup"><span data-stu-id="f6d08-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="f6d08-131">Autrement dit, la fonction peut avoir plusieurs instances de `ICorDebugFunction`, un pour chaque version de la fonction, mais une seule `mdMethodDef` jeton.</span><span class="sxs-lookup"><span data-stu-id="f6d08-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6d08-132">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="f6d08-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6d08-133">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f6d08-133">Requirements</span></span>  
 <span data-ttu-id="f6d08-134">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6d08-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6d08-135">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6d08-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6d08-136">**Bibliothèque :**  CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6d08-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6d08-137">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6d08-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6d08-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6d08-138">See also</span></span>

- [<span data-ttu-id="f6d08-139">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f6d08-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
