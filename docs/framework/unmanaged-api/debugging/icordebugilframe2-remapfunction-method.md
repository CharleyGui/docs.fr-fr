---
title: ICorDebugILFrame2::RemapFunction, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.RemapFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75004f646c01897ef3e3016b073220ad33a0d925
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967576"
---
# <a name="icordebugilframe2remapfunction-method"></a><span data-ttu-id="54a4c-102">ICorDebugILFrame2::RemapFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="54a4c-102">ICorDebugILFrame2::RemapFunction Method</span></span>
<span data-ttu-id="54a4c-103">Remappe une fonction modifiée en spécifiant le nouvel offset MSIL (Microsoft Intermediate Language)</span><span class="sxs-lookup"><span data-stu-id="54a4c-103">Remaps an edited function by specifying the new Microsoft intermediate language (MSIL) offset</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54a4c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54a4c-104">Syntax</span></span>  
  
```cpp  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54a4c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="54a4c-105">Parameters</span></span>  
 `newILOffset`  
 <span data-ttu-id="54a4c-106">dans Nouvel offset MSIL du frame de pile auquel le pointeur d’instruction doit être placé.</span><span class="sxs-lookup"><span data-stu-id="54a4c-106">[in] The stack frame's new MSIL offset at which the instruction pointer should be placed.</span></span> <span data-ttu-id="54a4c-107">Cette valeur doit être un point de séquence.</span><span class="sxs-lookup"><span data-stu-id="54a4c-107">This value must be a sequence point.</span></span>  
  
 <span data-ttu-id="54a4c-108">Il incombe à l’appelant de garantir la validité de cette valeur.</span><span class="sxs-lookup"><span data-stu-id="54a4c-108">It is the caller’s responsibility to ensure the validity of this value.</span></span> <span data-ttu-id="54a4c-109">Par exemple, l’offset MSIL n’est pas valide s’il est en dehors des limites de la fonction.</span><span class="sxs-lookup"><span data-stu-id="54a4c-109">For example, the MSIL offset is not valid if it is outside the bounds of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54a4c-110">Notes</span><span class="sxs-lookup"><span data-stu-id="54a4c-110">Remarks</span></span>  
 <span data-ttu-id="54a4c-111">Quand la fonction d’un frame a été modifiée, le débogueur peut appeler `RemapFunction` la méthode pour échanger la version la plus récente de la fonction du frame afin de pouvoir l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="54a4c-111">When a frame’s function has been edited, the debugger can call the `RemapFunction` method to swap in the latest version of the frame's function so it can be executed.</span></span> <span data-ttu-id="54a4c-112">L’exécution du code commence à l’offset MSIL donné.</span><span class="sxs-lookup"><span data-stu-id="54a4c-112">The code execution will begin at the given MSIL offset.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54a4c-113">Appeler `RemapFunction`, comme appeler [ICorDebugILFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), invalidera immédiatement toutes les interfaces de débogage liées à la génération d’une trace de la pile pour le thread.</span><span class="sxs-lookup"><span data-stu-id="54a4c-113">Calling `RemapFunction`, like calling [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), will immediately invalidate all debugging interfaces that are related to generating a stack trace for the thread.</span></span> <span data-ttu-id="54a4c-114">Ces interfaces incluent [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame et ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="54a4c-114">These interfaces include [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame, and ICorDebugNativeFrame.</span></span>  
  
 <span data-ttu-id="54a4c-115">La `RemapFunction` méthode peut être appelée uniquement dans le contexte du frame actuel, et uniquement dans l’un des cas suivants:</span><span class="sxs-lookup"><span data-stu-id="54a4c-115">The `RemapFunction` method can be called only in the context of the current frame, and only in one of the following cases:</span></span>  
  
- <span data-ttu-id="54a4c-116">Après réception d’un rappel [ICorDebugManagedCallback2:: FunctionRemapOpportunity,](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) qui n’a pas encore été poursuivi.</span><span class="sxs-lookup"><span data-stu-id="54a4c-116">After receipt of a [ICorDebugManagedCallback2::FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) callback that has not yet been continued.</span></span>  
  
- <span data-ttu-id="54a4c-117">Pendant l’arrêt de l’exécution du code en raison d’un événement [ICorDebugManagedCallback:: EditAndContinueRemap,](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) pour ce frame.</span><span class="sxs-lookup"><span data-stu-id="54a4c-117">While code execution is stopped because of an [ICorDebugManagedCallback::EditAndContinueRemap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) event for this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54a4c-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="54a4c-118">Requirements</span></span>  
 <span data-ttu-id="54a4c-119">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54a4c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54a4c-120">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="54a4c-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54a4c-121">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54a4c-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54a4c-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54a4c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
