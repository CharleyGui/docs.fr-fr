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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a77e7f20aba1908a63d77b4ccada7fabacf55f7
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025852"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="b7594-102">ICorDebugComObjectValue::GetCachedInterfacePointers, méthode</span><span class="sxs-lookup"><span data-stu-id="b7594-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>
<span data-ttu-id="b7594-103">Obtient les pointeurs d’interface brut mis en cache sur le cours callable wrapper RCW (runtime).</span><span class="sxs-lookup"><span data-stu-id="b7594-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7594-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7594-104">Syntax</span></span>  
  
```  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7594-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b7594-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="b7594-106">[in] Une valeur qui indique si la méthode retourne uniquement les interfaces Windows Runtime (`IInspectable` interfaces) ou des interfaces COM qui sont mis en cache par le runtime callable wrapper RCW ().</span><span class="sxs-lookup"><span data-stu-id="b7594-106">[in] A value that indicates whether the method will return only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="b7594-107">[in] Le nombre d’objets dont les adresses doivent être récupérés.</span><span class="sxs-lookup"><span data-stu-id="b7594-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b7594-108">[out] Un pointeur vers le nombre de `CORDB_ADDRESS` valeurs réellement retournés dans `ptrs`.</span><span class="sxs-lookup"><span data-stu-id="b7594-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="b7594-109">Un pointeur vers l’adresse de départ d’un tableau de `CORDB_ADDRESS` les valeurs qui contiennent les adresses de mises en cache les objets d’interface.</span><span class="sxs-lookup"><span data-stu-id="b7594-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7594-110">Notes</span><span class="sxs-lookup"><span data-stu-id="b7594-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7594-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b7594-111">Requirements</span></span>  
 <span data-ttu-id="b7594-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7594-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7594-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7594-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7594-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7594-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7594-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7594-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7594-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7594-116">See also</span></span>

- [<span data-ttu-id="b7594-117">ICorDebugComObjectValue, interface</span><span class="sxs-lookup"><span data-stu-id="b7594-117">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="b7594-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="b7594-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
