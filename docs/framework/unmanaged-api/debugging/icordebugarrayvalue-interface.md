---
title: ICorDebugArrayValue, interface
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
ms.openlocfilehash: e41bb5ca0fdd999692395239304f50a6f745a4f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088265"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="ce565-102">ICorDebugArrayValue, interface</span><span class="sxs-lookup"><span data-stu-id="ce565-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="ce565-103">Sous-classe de ICorDebugHeapValue qui représente un tableau unidimensionnel ou multidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="ce565-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ce565-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ce565-104">Methods</span></span>  
  
|<span data-ttu-id="ce565-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ce565-105">Method</span></span>|<span data-ttu-id="ce565-106">Description</span><span class="sxs-lookup"><span data-stu-id="ce565-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ce565-107">GetBaseIndicies, méthode</span><span class="sxs-lookup"><span data-stu-id="ce565-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="ce565-108">Obtient l’index de base de chaque dimension du tableau.</span><span class="sxs-lookup"><span data-stu-id="ce565-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="ce565-109">GetCount, méthode</span><span class="sxs-lookup"><span data-stu-id="ce565-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="ce565-110">Obtient le nombre total d’éléments dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="ce565-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="ce565-111">GetDimensions, méthode</span><span class="sxs-lookup"><span data-stu-id="ce565-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="ce565-112">Obtient les dimensions du tableau.</span><span class="sxs-lookup"><span data-stu-id="ce565-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="ce565-113">GetElement, méthode</span><span class="sxs-lookup"><span data-stu-id="ce565-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="ce565-114">Obtient une valeur représentant l’élément donné dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="ce565-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="ce565-115">GetElementAtPosition, méthode</span><span class="sxs-lookup"><span data-stu-id="ce565-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="ce565-116">Obtient l’élément à la position donnée, en traitant le tableau comme un tableau unidimensionnel de base zéro.</span><span class="sxs-lookup"><span data-stu-id="ce565-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="ce565-117">GetElementType, méthode</span><span class="sxs-lookup"><span data-stu-id="ce565-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="ce565-118">Obtient le type simple des éléments dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="ce565-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="ce565-119">GetRank, méthode</span><span class="sxs-lookup"><span data-stu-id="ce565-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="ce565-120">Obtient le nombre de dimensions dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="ce565-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="ce565-121">HasBaseIndicies, méthode</span><span class="sxs-lookup"><span data-stu-id="ce565-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="ce565-122">Détermine si le tableau a des index de base.</span><span class="sxs-lookup"><span data-stu-id="ce565-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce565-123">Notes</span><span class="sxs-lookup"><span data-stu-id="ce565-123">Remarks</span></span>  
 <span data-ttu-id="ce565-124">`ICorDebugArrayValue` prend en charge les tableaux unidimensionnels et multidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="ce565-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce565-125">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="ce565-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce565-126">spécifications</span><span class="sxs-lookup"><span data-stu-id="ce565-126">Requirements</span></span>  
 <span data-ttu-id="ce565-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce565-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce565-128">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce565-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce565-129">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce565-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce565-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce565-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce565-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce565-131">See also</span></span>

- [<span data-ttu-id="ce565-132">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ce565-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
