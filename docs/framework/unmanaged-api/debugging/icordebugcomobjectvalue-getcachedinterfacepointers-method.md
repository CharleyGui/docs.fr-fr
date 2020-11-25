---
title: ICorDebugComObjectValue::GetCachedInterfacePointers, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfacePointers
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type:
- apiref
ms.openlocfilehash: c3120a0dd859f581e6356fc260043cb83250ae9e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724830"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="73683-102">ICorDebugComObjectValue::GetCachedInterfacePointers, méthode</span><span class="sxs-lookup"><span data-stu-id="73683-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>

<span data-ttu-id="73683-103">Obtient les pointeurs d’interface bruts mis en cache sur le wrapper RCW (Runtime Callable Wrapper) actuel.</span><span class="sxs-lookup"><span data-stu-id="73683-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73683-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73683-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73683-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="73683-105">Parameters</span></span>  

 `bIInspectableOnly`  
 <span data-ttu-id="73683-106">dans Valeur qui indique si la méthode retourne uniquement Windows Runtime interfaces ( `IInspectable` interfaces) ou toutes les interfaces com mises en cache par le wrapper RCW (Runtime Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="73683-106">[in] A value that indicates whether the method will return only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="73683-107">dans Nombre d’objets dont les adresses doivent être récupérées.</span><span class="sxs-lookup"><span data-stu-id="73683-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="73683-108">à Pointeur vers le nombre de `CORDB_ADDRESS` valeurs réellement retournées dans `ptrs` .</span><span class="sxs-lookup"><span data-stu-id="73683-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="73683-109">Pointeur vers l’adresse de début d’un tableau de `CORDB_ADDRESS` valeurs qui contiennent les adresses des objets d’interface mis en cache.</span><span class="sxs-lookup"><span data-stu-id="73683-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73683-110">Notes</span><span class="sxs-lookup"><span data-stu-id="73683-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73683-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="73683-111">Requirements</span></span>  

 <span data-ttu-id="73683-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73683-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73683-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73683-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73683-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73683-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73683-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73683-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73683-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73683-116">See also</span></span>

- [<span data-ttu-id="73683-117">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="73683-117">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="73683-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="73683-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
