---
title: ICorDebugEnum::GetCount, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::GetCount
helpviewer_keywords:
- ICorDebugEnum::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: d8a74304-1cb2-4977-a21d-e1af48c563ff
topic_type:
- apiref
ms.openlocfilehash: 208d5d2e3ca571a1c23a9322c05e784bd2238d61
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124695"
---
# <a name="icordebugenumgetcount-method"></a><span data-ttu-id="910ef-102">ICorDebugEnum::GetCount, méthode</span><span class="sxs-lookup"><span data-stu-id="910ef-102">ICorDebugEnum::GetCount Method</span></span>
<span data-ttu-id="910ef-103">Obtient le nombre d’éléments dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="910ef-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="910ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="910ef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="910ef-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="910ef-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="910ef-106">à Pointeur vers le nombre d’éléments dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="910ef-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="910ef-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="910ef-107">Requirements</span></span>  
 <span data-ttu-id="910ef-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="910ef-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="910ef-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="910ef-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="910ef-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="910ef-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="910ef-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="910ef-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
