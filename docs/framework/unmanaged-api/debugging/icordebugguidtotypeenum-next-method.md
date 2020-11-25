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
ms.openlocfilehash: 68f548705213da7d715ae569116abae0cd24129d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705655"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="e1d59-102">ICorDebugGuidToTypeEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="e1d59-102">ICorDebugGuidToTypeEnum::Next Method</span></span>

<span data-ttu-id="e1d59-103">Obtient le nombre spécifié d’instances [cordebugguidtotypemapping,](cordebugguidtotypemapping-structure.md) qui mappent les GUID aux informations de type.</span><span class="sxs-lookup"><span data-stu-id="e1d59-103">Gets the specified number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1d59-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1d59-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1d59-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e1d59-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="e1d59-106">dans Nombre d’objets de mappage GUID-à-type à récupérer.</span><span class="sxs-lookup"><span data-stu-id="e1d59-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="e1d59-107">à Tableau de pointeurs, chacun pointant vers un objet [cordebugguidtotypemapping,](cordebugguidtotypemapping-structure.md) qui mappe un GUID Windows Runtime à son objet ICorDebugType correspondant.</span><span class="sxs-lookup"><span data-stu-id="e1d59-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) object that maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e1d59-108">à Pointeur vers le nombre d’objets [cordebugguidtotypemapping,](cordebugguidtotypemapping-structure.md) réellement retournés dans `values` .</span><span class="sxs-lookup"><span data-stu-id="e1d59-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1d59-109">Notes</span><span class="sxs-lookup"><span data-stu-id="e1d59-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1d59-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e1d59-110">Requirements</span></span>  

 <span data-ttu-id="e1d59-111">**Plateformes :** Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="e1d59-111">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="e1d59-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1d59-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1d59-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1d59-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1d59-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1d59-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1d59-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1d59-115">See also</span></span>

- [<span data-ttu-id="e1d59-116">ICorDebugGuidToTypeEnum, interface</span><span class="sxs-lookup"><span data-stu-id="e1d59-116">ICorDebugGuidToTypeEnum Interface</span></span>](icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="e1d59-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e1d59-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
