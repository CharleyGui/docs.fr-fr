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
ms.openlocfilehash: 3de85626be6ae8e4769ac261f4de1479461417ec
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893539"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="87887-102">ICorDebugCode::GetILToNativeMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="87887-102">ICorDebugCode::GetILToNativeMapping Method</span></span>
<span data-ttu-id="87887-103">Obtient un tableau d’instances de « COR_DEBUG_IL_TO_NATIVE_MAP » qui représentent des mappages de décalages MSIL (Microsoft Intermediate Language) aux offsets natifs.</span><span class="sxs-lookup"><span data-stu-id="87887-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87887-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87887-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87887-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="87887-105">Parameters</span></span>  
 `cMap`  
 <span data-ttu-id="87887-106">[in] Taille du tableau `map`.</span><span class="sxs-lookup"><span data-stu-id="87887-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="87887-107">à Pointeur vers le nombre réel d’éléments retournés dans `map` le tableau.</span><span class="sxs-lookup"><span data-stu-id="87887-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="87887-108">à Tableau de `COR_DEBUG_IL_TO_NATIVE_MAP` structures, chacune représentant un mappage d’un offset MSIL à un offset natif.</span><span class="sxs-lookup"><span data-stu-id="87887-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="87887-109">Il n’y a aucun classement pour le tableau d’éléments retournés.</span><span class="sxs-lookup"><span data-stu-id="87887-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87887-110">Notes </span><span class="sxs-lookup"><span data-stu-id="87887-110">Remarks</span></span>  
 <span data-ttu-id="87887-111">La `GetILToNativeMapping` méthode retourne des résultats significatifs uniquement si cette instance « ICorDebugCode » représente du code natif qui était compilé juste-à-temps (JIT) à partir du code MSIL.</span><span class="sxs-lookup"><span data-stu-id="87887-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87887-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="87887-112">Requirements</span></span>  
 <span data-ttu-id="87887-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87887-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87887-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87887-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87887-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87887-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87887-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87887-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87887-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87887-117">See also</span></span>

- [<span data-ttu-id="87887-118">ICorDebugCode, interface</span><span class="sxs-lookup"><span data-stu-id="87887-118">ICorDebugCode Interface</span></span>](icordebugcode-interface1.md)
