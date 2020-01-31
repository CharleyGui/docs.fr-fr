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
ms.openlocfilehash: 98709c0ce7469db1d0365d71e10d2d021cd3b3f0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777887"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="20f75-102">ICorDebugCode::GetILToNativeMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="20f75-102">ICorDebugCode::GetILToNativeMapping Method</span></span>
<span data-ttu-id="20f75-103">Obtient un tableau d’instances de « COR_DEBUG_IL_TO_NATIVE_MAP » qui représentent des mappages de décalages MSIL (Microsoft Intermediate Language) aux offsets natifs.</span><span class="sxs-lookup"><span data-stu-id="20f75-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20f75-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20f75-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20f75-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="20f75-105">Parameters</span></span>  
 `cMap`  
 <span data-ttu-id="20f75-106">[in] Taille du tableau `map`.</span><span class="sxs-lookup"><span data-stu-id="20f75-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="20f75-107">à Pointeur vers le nombre réel d’éléments retournés dans le tableau de `map`.</span><span class="sxs-lookup"><span data-stu-id="20f75-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="20f75-108">à Tableau de `COR_DEBUG_IL_TO_NATIVE_MAP` structures, chacune représentant un mappage d’un offset MSIL à un offset natif.</span><span class="sxs-lookup"><span data-stu-id="20f75-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="20f75-109">Il n’y a aucun classement pour le tableau d’éléments retournés.</span><span class="sxs-lookup"><span data-stu-id="20f75-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20f75-110">Notes</span><span class="sxs-lookup"><span data-stu-id="20f75-110">Remarks</span></span>  
 <span data-ttu-id="20f75-111">La méthode `GetILToNativeMapping` retourne des résultats significatifs uniquement si cette instance « ICorDebugCode » représente du code natif qui était compilé juste-à-temps (JIT) à partir du code MSIL.</span><span class="sxs-lookup"><span data-stu-id="20f75-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20f75-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="20f75-112">Requirements</span></span>  
 <span data-ttu-id="20f75-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20f75-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20f75-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20f75-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20f75-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20f75-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20f75-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20f75-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20f75-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20f75-117">See also</span></span>

- [<span data-ttu-id="20f75-118">ICorDebugCode, interface</span><span class="sxs-lookup"><span data-stu-id="20f75-118">ICorDebugCode Interface</span></span>](icordebugcode-interface1.md)
