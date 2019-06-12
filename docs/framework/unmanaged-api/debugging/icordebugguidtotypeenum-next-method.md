---
title: ICorDebugGuidToTypeEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 160ddbf9be8eb9f3b99d159aa8b36a22b58a9f55
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025806"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="d98dd-102">ICorDebugGuidToTypeEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="d98dd-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="d98dd-103">Obtient le nombre spécifié de [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances qui mappent des GUID vers le type d’informations.</span><span class="sxs-lookup"><span data-stu-id="d98dd-103">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d98dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d98dd-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d98dd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d98dd-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="d98dd-106">[in] Le nombre d’objets de mappage de type-GUID à récupérer.</span><span class="sxs-lookup"><span data-stu-id="d98dd-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="d98dd-107">[out] Un tableau de pointeurs, chacun d’eux pointe vers un [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objet qui mappe un GUID d’exécution de Windows à son objet ICorDebugType correspondant.</span><span class="sxs-lookup"><span data-stu-id="d98dd-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) object that maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d98dd-108">[out] Un pointeur vers le nombre de [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) réellement retournés dans des objets `values`.</span><span class="sxs-lookup"><span data-stu-id="d98dd-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d98dd-109">Notes</span><span class="sxs-lookup"><span data-stu-id="d98dd-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d98dd-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d98dd-110">Requirements</span></span>  
 <span data-ttu-id="d98dd-111">**Plateformes :** Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="d98dd-111">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="d98dd-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d98dd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d98dd-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d98dd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d98dd-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d98dd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d98dd-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d98dd-115">See also</span></span>

- [<span data-ttu-id="d98dd-116">ICorDebugGuidToTypeEnum, interface</span><span class="sxs-lookup"><span data-stu-id="d98dd-116">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="d98dd-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d98dd-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
