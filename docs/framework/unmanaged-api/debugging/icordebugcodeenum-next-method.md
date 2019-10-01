---
title: ICorDebugCodeEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 076b5d628dfe83decdbbe2f5e74c50e08262c580
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700692"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="d738d-102">ICorDebugCodeEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="d738d-102">ICorDebugCodeEnum::Next Method</span></span>

<span data-ttu-id="d738d-103">Obtient le nombre spécifié d’instances « ICorDebugCode » de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="d738d-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>

## <a name="syntax"></a><span data-ttu-id="d738d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d738d-104">Syntax</span></span>

```cpp
HRESULT Next (
    [in] ULONG  celt,
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorDebugCode *values[],
    [out] ULONG *pceltFetched
);
```

## <a name="parameters"></a><span data-ttu-id="d738d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d738d-105">Parameters</span></span>

 `celt`  
 <span data-ttu-id="d738d-106">dans Nombre d’instances `ICorDebugCode` à récupérer.</span><span class="sxs-lookup"><span data-stu-id="d738d-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>

 `values`  
 <span data-ttu-id="d738d-107">à Tableau de pointeurs, chacun pointant vers un objet `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="d738d-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>

 `pceltFetched`  
 <span data-ttu-id="d738d-108">à Pointeur vers le nombre d’instances `ICorDebugCode` réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="d738d-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="d738d-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="d738d-109">This value may be null if `celt` is one.</span></span>

## <a name="requirements"></a><span data-ttu-id="d738d-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d738d-110">Requirements</span></span>

 <span data-ttu-id="d738d-111">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d738d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="d738d-112">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d738d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="d738d-113">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d738d-113">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="d738d-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d738d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
 
