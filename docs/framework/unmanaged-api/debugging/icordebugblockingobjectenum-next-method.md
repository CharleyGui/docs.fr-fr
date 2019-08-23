---
title: ICorDebugBlockingObjectEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
- ICorDebugBlockingObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 0121753f-ebea-48d0-aeb2-ed7fda76dc60
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e94e4da0eea06ce9cc0110002b1def9e4dd4989
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939141"
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="f1a78-102">ICorDebugBlockingObjectEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="f1a78-102">ICorDebugBlockingObjectEnum::Next Method</span></span>
<span data-ttu-id="f1a78-103">Obtient le nombre spécifié d’objets [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="f1a78-103">Gets the specified number of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1a78-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1a78-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1a78-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f1a78-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f1a78-106">dans Nombre d’objets à récupérer.</span><span class="sxs-lookup"><span data-stu-id="f1a78-106">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="f1a78-107">à Tableau de pointeurs vers des objets [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="f1a78-107">[out] An array of pointers to [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f1a78-108">à Pointeur vers le nombre d’objets qui ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="f1a78-108">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1a78-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f1a78-109">Return Value</span></span>  
 <span data-ttu-id="f1a78-110">Cette méthode retourne les HRESULT spécifiques suivants.</span><span class="sxs-lookup"><span data-stu-id="f1a78-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="f1a78-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f1a78-111">HRESULT</span></span>|<span data-ttu-id="f1a78-112">Description</span><span class="sxs-lookup"><span data-stu-id="f1a78-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f1a78-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="f1a78-113">S_OK</span></span>|<span data-ttu-id="f1a78-114">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="f1a78-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="f1a78-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f1a78-115">S_FALSE</span></span>|<span data-ttu-id="f1a78-116">`pceltFetched` n’est pas égal à `celt`.</span><span class="sxs-lookup"><span data-stu-id="f1a78-116">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1a78-117">Notes</span><span class="sxs-lookup"><span data-stu-id="f1a78-117">Remarks</span></span>  
 <span data-ttu-id="f1a78-118">Cette méthode fonctionne comme un énumérateur COM classique.</span><span class="sxs-lookup"><span data-stu-id="f1a78-118">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="f1a78-119">Les valeurs du tableau d’entrée doivent être au moins `celt`de la taille.</span><span class="sxs-lookup"><span data-stu-id="f1a78-119">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="f1a78-120">Le tableau sera rempli avec les valeurs suivantes `celt` dans l’énumération ou avec toutes les valeurs restantes si elles sont inférieures à. `celt`</span><span class="sxs-lookup"><span data-stu-id="f1a78-120">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="f1a78-121">Lorsque cette méthode est retournée, `pceltFetched` est rempli avec le nombre de valeurs qui ont été récupérées.</span><span class="sxs-lookup"><span data-stu-id="f1a78-121">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="f1a78-122">Si `values` contient des pointeurs non valides ou pointe vers une mémoire tampon `celt`inférieure à, `pceltFetched` ou si est un pointeur non valide, le résultat n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="f1a78-122">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1a78-123">Bien que la structure [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) n’ait pas besoin d’être libérée, l’interface «ICorDebugValue» à l’intérieur de celle-ci doit être libérée.</span><span class="sxs-lookup"><span data-stu-id="f1a78-123">Although the [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1a78-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f1a78-124">Requirements</span></span>  
 <span data-ttu-id="f1a78-125">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1a78-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1a78-126">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f1a78-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1a78-127">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1a78-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1a78-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1a78-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1a78-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1a78-129">See also</span></span>

- [<span data-ttu-id="f1a78-130">ICorDebugDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="f1a78-130">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="f1a78-131">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f1a78-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f1a78-132">Débogage</span><span class="sxs-lookup"><span data-stu-id="f1a78-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
