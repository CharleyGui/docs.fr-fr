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
ms.openlocfilehash: 0f6fe5d7eb5926d48809bb6490ba75df9d4a5033
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213149"
---
# <a name="icordebugfunctionbreakpointgetoffset-method"></a><span data-ttu-id="0e87b-102">ICorDebugFunctionBreakpoint::GetOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="0e87b-102">ICorDebugFunctionBreakpoint::GetOffset Method</span></span>
<span data-ttu-id="0e87b-103">Obtient l’offset du point d’arrêt dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="0e87b-103">Gets the offset of the breakpoint within the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e87b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e87b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset (  
    [out] ULONG32  *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e87b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0e87b-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="0e87b-106">à Pointeur vers l’offset du point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="0e87b-106">[out] A pointer to the offset of the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e87b-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0e87b-107">Requirements</span></span>  
 <span data-ttu-id="0e87b-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e87b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e87b-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e87b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e87b-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e87b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e87b-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e87b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
