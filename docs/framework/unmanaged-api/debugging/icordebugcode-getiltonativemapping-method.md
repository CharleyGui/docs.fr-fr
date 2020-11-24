---
title: ICorDebugCode::GetILToNativeMapping, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetILToNativeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type:
- apiref
ms.openlocfilehash: 0adb9e58ca2c6b5b430a0413fa11ba59d79a0539
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688105"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="5283f-102">ICorDebugCode::GetILToNativeMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="5283f-102">ICorDebugCode::GetILToNativeMapping Method</span></span>

<span data-ttu-id="5283f-103">Obtient un tableau d’instances de « COR_DEBUG_IL_TO_NATIVE_MAP » qui représentent des mappages de décalages MSIL (Microsoft Intermediate Language) aux offsets natifs.</span><span class="sxs-lookup"><span data-stu-id="5283f-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5283f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5283f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5283f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5283f-105">Parameters</span></span>  

 `cMap`  
 <span data-ttu-id="5283f-106">[in] Taille du tableau `map`.</span><span class="sxs-lookup"><span data-stu-id="5283f-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="5283f-107">à Pointeur vers le nombre réel d’éléments retournés dans le `map` tableau.</span><span class="sxs-lookup"><span data-stu-id="5283f-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="5283f-108">à Tableau de `COR_DEBUG_IL_TO_NATIVE_MAP` structures, chacune représentant un mappage d’un offset MSIL à un offset natif.</span><span class="sxs-lookup"><span data-stu-id="5283f-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="5283f-109">Il n’y a aucun classement pour le tableau d’éléments retournés.</span><span class="sxs-lookup"><span data-stu-id="5283f-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5283f-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="5283f-110">Remarks</span></span>  

 <span data-ttu-id="5283f-111">La `GetILToNativeMapping` méthode retourne des résultats significatifs uniquement si cette instance « ICorDebugCode » représente du code natif qui était compilé juste-à-temps (JIT) à partir du code MSIL.</span><span class="sxs-lookup"><span data-stu-id="5283f-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5283f-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5283f-112">Requirements</span></span>  

 <span data-ttu-id="5283f-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5283f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5283f-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5283f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5283f-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5283f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5283f-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5283f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5283f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5283f-117">See also</span></span>

- [<span data-ttu-id="5283f-118">ICorDebugCode, interface</span><span class="sxs-lookup"><span data-stu-id="5283f-118">ICorDebugCode Interface</span></span>](icordebugcode-interface1.md)
