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
ms.openlocfilehash: af90886390b59932d3ae146a70fc2901ec1c378d
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894667"
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="bf4de-102">ICorDebugBreakpointEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="bf4de-102">ICorDebugBreakpointEnum::Next Method</span></span>
<span data-ttu-id="bf4de-103">Obtient le nombre spécifié d’instances de ICorDebugBreakpoint à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="bf4de-103">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf4de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf4de-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf4de-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bf4de-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="bf4de-106">dans Nombre d' `ICorDebugBreakpoint` instances à récupérer.</span><span class="sxs-lookup"><span data-stu-id="bf4de-106">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="bf4de-107">à Tableau de pointeurs, chacun pointant vers un `ICorDebugBreakpoint` objet qui représente un point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="bf4de-107">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="bf4de-108">à Pointeur vers le nombre d' `ICorDebugBreakpoint` instances réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="bf4de-108">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="bf4de-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="bf4de-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf4de-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bf4de-110">Requirements</span></span>  
 <span data-ttu-id="bf4de-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf4de-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf4de-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf4de-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf4de-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf4de-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf4de-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf4de-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
