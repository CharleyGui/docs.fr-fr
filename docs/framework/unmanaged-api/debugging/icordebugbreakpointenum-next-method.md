---
title: ICorDebugBreakpointEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBreakpointEnum interface [.NET Framework debugging]
- ICorDebugBreakpointEnum::Next method [.NET Framework debugging]
ms.assetid: 2e6bbaea-79ba-448c-a0e3-7c90fc7c2939
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87249dae0eff4ea4899a63c0d13e79c266df453a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745006"
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="ab613-102">ICorDebugBreakpointEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="ab613-102">ICorDebugBreakpointEnum::Next Method</span></span>
<span data-ttu-id="ab613-103">Obtient le nombre spécifié d’instances de ICorDebugBreakpoint à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="ab613-103">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab613-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab613-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab613-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ab613-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ab613-106">[in] Le nombre de `ICorDebugBreakpoint` instances à récupérer.</span><span class="sxs-lookup"><span data-stu-id="ab613-106">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="ab613-107">[out] Un tableau de pointeurs, chacun d’eux pointe vers un `ICorDebugBreakpoint` objet qui représente un point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="ab613-107">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ab613-108">[out] Un pointeur vers le nombre de `ICorDebugBreakpoint` instances réellement retournés.</span><span class="sxs-lookup"><span data-stu-id="ab613-108">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="ab613-109">Cette valeur peut être null si `celt` fait partie.</span><span class="sxs-lookup"><span data-stu-id="ab613-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab613-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ab613-110">Requirements</span></span>  
 <span data-ttu-id="ab613-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab613-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab613-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab613-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab613-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab613-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab613-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab613-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
