---
title: ICorDebugFunctionBreakpoint::GetOffset, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint::GetOffset
helpviewer_keywords:
- ICorDebugFunctionBreakpoint::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: e619eae4-3ac3-4c37-bba4-55e59989b9cb
topic_type:
- apiref
ms.openlocfilehash: e0e4bfb3f7adb0242456dfc3a4703ca56f118476
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138167"
---
# <a name="icordebugfunctionbreakpointgetoffset-method"></a><span data-ttu-id="c0a59-102">ICorDebugFunctionBreakpoint::GetOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="c0a59-102">ICorDebugFunctionBreakpoint::GetOffset Method</span></span>
<span data-ttu-id="c0a59-103">Gets the offset of the breakpoint within the function.</span><span class="sxs-lookup"><span data-stu-id="c0a59-103">Gets the offset of the breakpoint within the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0a59-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0a59-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset (  
    [out] ULONG32  *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0a59-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c0a59-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="c0a59-106">[out] A pointer to the offset of the breakpoint.</span><span class="sxs-lookup"><span data-stu-id="c0a59-106">[out] A pointer to the offset of the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0a59-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="c0a59-107">Requirements</span></span>  
 <span data-ttu-id="c0a59-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0a59-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0a59-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0a59-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0a59-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0a59-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0a59-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0a59-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
