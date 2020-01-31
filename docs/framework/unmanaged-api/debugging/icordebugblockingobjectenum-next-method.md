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
ms.openlocfilehash: c25f26bb0f1f34e3799bab4bec7e697d393cccb4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784514"
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="208b3-102">ICorDebugBlockingObjectEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="208b3-102">ICorDebugBlockingObjectEnum::Next Method</span></span>
<span data-ttu-id="208b3-103">Obtient le nombre spécifié d’objets [CorDebugBlockingObject](cordebugblockingobject-structure.md) à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="208b3-103">Gets the specified number of [CorDebugBlockingObject](cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="208b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="208b3-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a><span data-ttu-id="208b3-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="208b3-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="208b3-106">dans Nombre d’objets à récupérer.</span><span class="sxs-lookup"><span data-stu-id="208b3-106">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="208b3-107">à Tableau de pointeurs vers des objets [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="208b3-107">[out] An array of pointers to [CorDebugBlockingObject](cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="208b3-108">à Pointeur vers le nombre d’objets qui ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="208b3-108">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="208b3-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="208b3-109">Return Value</span></span>  
 <span data-ttu-id="208b3-110">Cette méthode retourne les HRESULT spécifiques suivants.</span><span class="sxs-lookup"><span data-stu-id="208b3-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="208b3-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="208b3-111">HRESULT</span></span>|<span data-ttu-id="208b3-112">Description</span><span class="sxs-lookup"><span data-stu-id="208b3-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="208b3-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="208b3-113">S_OK</span></span>|<span data-ttu-id="208b3-114">La méthode s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="208b3-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="208b3-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="208b3-115">S_FALSE</span></span>|<span data-ttu-id="208b3-116">`pceltFetched` n’est pas égal à `celt`.</span><span class="sxs-lookup"><span data-stu-id="208b3-116">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="208b3-117">Notes</span><span class="sxs-lookup"><span data-stu-id="208b3-117">Remarks</span></span>  
 <span data-ttu-id="208b3-118">Cette méthode fonctionne comme un énumérateur COM classique.</span><span class="sxs-lookup"><span data-stu-id="208b3-118">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="208b3-119">Les valeurs du tableau d’entrée doivent être au moins de la taille `celt`.</span><span class="sxs-lookup"><span data-stu-id="208b3-119">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="208b3-120">Le tableau sera rempli avec les valeurs de `celt` suivantes dans l’énumération ou avec toutes les valeurs restantes si moins de `celt` sont conservées.</span><span class="sxs-lookup"><span data-stu-id="208b3-120">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="208b3-121">Lorsque cette méthode est retournée, `pceltFetched` est rempli avec le nombre de valeurs qui ont été récupérées.</span><span class="sxs-lookup"><span data-stu-id="208b3-121">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="208b3-122">Si `values` contient des pointeurs non valides ou pointe vers une mémoire tampon inférieure à `celt`, ou si `pceltFetched` est un pointeur non valide, le résultat n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="208b3-122">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="208b3-123">Bien que la structure [CorDebugBlockingObject](cordebugblockingobject-structure.md) n’ait pas besoin d’être libérée, l’interface « ICorDebugValue » à l’intérieur de celle-ci doit être libérée.</span><span class="sxs-lookup"><span data-stu-id="208b3-123">Although the [CorDebugBlockingObject](cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="208b3-124">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="208b3-124">Requirements</span></span>  
 <span data-ttu-id="208b3-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="208b3-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="208b3-126">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="208b3-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="208b3-127">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="208b3-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="208b3-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="208b3-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="208b3-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="208b3-129">See also</span></span>

- [<span data-ttu-id="208b3-130">ICorDebugDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="208b3-130">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="208b3-131">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="208b3-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="208b3-132">Débogage</span><span class="sxs-lookup"><span data-stu-id="208b3-132">Debugging</span></span>](index.md)
