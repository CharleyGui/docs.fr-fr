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
ms.openlocfilehash: f4f73b99b4cb48690a2a8611dbf5a5420adab5d4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794351"
---
# <a name="icordebugilframe2remapfunction-method"></a><span data-ttu-id="39bd1-102">ICorDebugILFrame2::RemapFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="39bd1-102">ICorDebugILFrame2::RemapFunction Method</span></span>
<span data-ttu-id="39bd1-103">Remappe une fonction modifiée en spécifiant le nouvel offset MSIL (Microsoft Intermediate Language)</span><span class="sxs-lookup"><span data-stu-id="39bd1-103">Remaps an edited function by specifying the new Microsoft intermediate language (MSIL) offset</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39bd1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39bd1-104">Syntax</span></span>  
  
```cpp  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39bd1-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="39bd1-105">Parameters</span></span>  
 `newILOffset`  
 <span data-ttu-id="39bd1-106">dans Nouvel offset MSIL du frame de pile auquel le pointeur d’instruction doit être placé.</span><span class="sxs-lookup"><span data-stu-id="39bd1-106">[in] The stack frame's new MSIL offset at which the instruction pointer should be placed.</span></span> <span data-ttu-id="39bd1-107">Cette valeur doit être un point de séquence.</span><span class="sxs-lookup"><span data-stu-id="39bd1-107">This value must be a sequence point.</span></span>  
  
 <span data-ttu-id="39bd1-108">Il incombe à l’appelant de garantir la validité de cette valeur.</span><span class="sxs-lookup"><span data-stu-id="39bd1-108">It is the caller’s responsibility to ensure the validity of this value.</span></span> <span data-ttu-id="39bd1-109">Par exemple, l’offset MSIL n’est pas valide s’il est en dehors des limites de la fonction.</span><span class="sxs-lookup"><span data-stu-id="39bd1-109">For example, the MSIL offset is not valid if it is outside the bounds of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39bd1-110">Notes</span><span class="sxs-lookup"><span data-stu-id="39bd1-110">Remarks</span></span>  
 <span data-ttu-id="39bd1-111">Quand la fonction d’un frame a été modifiée, le débogueur peut appeler la méthode `RemapFunction` pour échanger la version la plus récente de la fonction du frame afin de pouvoir l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="39bd1-111">When a frame’s function has been edited, the debugger can call the `RemapFunction` method to swap in the latest version of the frame's function so it can be executed.</span></span> <span data-ttu-id="39bd1-112">L’exécution du code commence à l’offset MSIL donné.</span><span class="sxs-lookup"><span data-stu-id="39bd1-112">The code execution will begin at the given MSIL offset.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39bd1-113">L’appel de `RemapFunction`, comme appeler [ICorDebugILFrame :: SetIP](icordebugilframe-setip-method.md), invalidera immédiatement toutes les interfaces de débogage liées à la génération d’une trace de la pile pour le thread.</span><span class="sxs-lookup"><span data-stu-id="39bd1-113">Calling `RemapFunction`, like calling [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md), will immediately invalidate all debugging interfaces that are related to generating a stack trace for the thread.</span></span> <span data-ttu-id="39bd1-114">Ces interfaces incluent [ICorDebugChain](icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame et ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="39bd1-114">These interfaces include [ICorDebugChain](icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame, and ICorDebugNativeFrame.</span></span>  
  
 <span data-ttu-id="39bd1-115">La méthode `RemapFunction` peut être appelée uniquement dans le contexte du frame actuel, et uniquement dans l’un des cas suivants :</span><span class="sxs-lookup"><span data-stu-id="39bd1-115">The `RemapFunction` method can be called only in the context of the current frame, and only in one of the following cases:</span></span>  
  
- <span data-ttu-id="39bd1-116">Après réception d’un rappel [ICorDebugManagedCallback2 :: FunctionRemapOpportunity,](icordebugmanagedcallback2-functionremapopportunity-method.md) qui n’a pas encore été poursuivi.</span><span class="sxs-lookup"><span data-stu-id="39bd1-116">After receipt of a [ICorDebugManagedCallback2::FunctionRemapOpportunity](icordebugmanagedcallback2-functionremapopportunity-method.md) callback that has not yet been continued.</span></span>  
  
- <span data-ttu-id="39bd1-117">Pendant l’arrêt de l’exécution du code en raison d’un événement [ICorDebugManagedCallback :: EditAndContinueRemap,](icordebugmanagedcallback-editandcontinueremap-method.md) pour ce frame.</span><span class="sxs-lookup"><span data-stu-id="39bd1-117">While code execution is stopped because of an [ICorDebugManagedCallback::EditAndContinueRemap](icordebugmanagedcallback-editandcontinueremap-method.md) event for this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39bd1-118">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="39bd1-118">Requirements</span></span>  
 <span data-ttu-id="39bd1-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39bd1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39bd1-120">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39bd1-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39bd1-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39bd1-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39bd1-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39bd1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
