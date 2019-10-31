---
title: ICorDebugFrameEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum::Next
helpviewer_keywords:
- ICorDebugFrameEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: 0bc96acb-6179-4328-a447-cda562ce9e98
topic_type:
- apiref
ms.openlocfilehash: ff74a9849b74b8a8e6b8c03f1fc4e7c7eee1ec14
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124060"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="0379f-102">ICorDebugFrameEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="0379f-102">ICorDebugFrameEnum::Next Method</span></span>
<span data-ttu-id="0379f-103">Obtient le nombre spécifié d’instances de ICorDebugFrame, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="0379f-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0379f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0379f-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0379f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0379f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="0379f-106">dans Nombre d’instances de `ICorDebugFrame` à récupérer.</span><span class="sxs-lookup"><span data-stu-id="0379f-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="0379f-107">à Tableau de pointeurs, chacun pointant vers un objet `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="0379f-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="0379f-108">à Pointeur vers le nombre d’instances `ICorDebugFrame` réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="0379f-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="0379f-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="0379f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0379f-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="0379f-110">Requirements</span></span>  
 <span data-ttu-id="0379f-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0379f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0379f-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0379f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0379f-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0379f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0379f-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0379f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
