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
ms.openlocfilehash: 5eb6299526d69624056961cfb7f0387ff8f873cf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725025"
---
# <a name="icordebugilframe2remapfunction-method"></a><span data-ttu-id="417bb-102">ICorDebugILFrame2::RemapFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="417bb-102">ICorDebugILFrame2::RemapFunction Method</span></span>

<span data-ttu-id="417bb-103">Remappe une fonction modifiée en spécifiant le nouvel offset MSIL (Microsoft Intermediate Language)</span><span class="sxs-lookup"><span data-stu-id="417bb-103">Remaps an edited function by specifying the new Microsoft intermediate language (MSIL) offset</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="417bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="417bb-104">Syntax</span></span>  
  
```cpp  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="417bb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="417bb-105">Parameters</span></span>  

 `newILOffset`  
 <span data-ttu-id="417bb-106">dans Nouvel offset MSIL du frame de pile auquel le pointeur d’instruction doit être placé.</span><span class="sxs-lookup"><span data-stu-id="417bb-106">[in] The stack frame's new MSIL offset at which the instruction pointer should be placed.</span></span> <span data-ttu-id="417bb-107">Cette valeur doit être un point de séquence.</span><span class="sxs-lookup"><span data-stu-id="417bb-107">This value must be a sequence point.</span></span>  
  
 <span data-ttu-id="417bb-108">Il incombe à l’appelant de garantir la validité de cette valeur.</span><span class="sxs-lookup"><span data-stu-id="417bb-108">It is the caller’s responsibility to ensure the validity of this value.</span></span> <span data-ttu-id="417bb-109">Par exemple, l’offset MSIL n’est pas valide s’il est en dehors des limites de la fonction.</span><span class="sxs-lookup"><span data-stu-id="417bb-109">For example, the MSIL offset is not valid if it is outside the bounds of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="417bb-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="417bb-110">Remarks</span></span>  

 <span data-ttu-id="417bb-111">Quand la fonction d’un frame a été modifiée, le débogueur peut appeler la `RemapFunction` méthode pour échanger la version la plus récente de la fonction du frame afin de pouvoir l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="417bb-111">When a frame’s function has been edited, the debugger can call the `RemapFunction` method to swap in the latest version of the frame's function so it can be executed.</span></span> <span data-ttu-id="417bb-112">L’exécution du code commence à l’offset MSIL donné.</span><span class="sxs-lookup"><span data-stu-id="417bb-112">The code execution will begin at the given MSIL offset.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="417bb-113">Appeler `RemapFunction` , comme appeler [ICorDebugILFrame :: SetIP](icordebugilframe-setip-method.md), invalidera immédiatement toutes les interfaces de débogage liées à la génération d’une trace de la pile pour le thread.</span><span class="sxs-lookup"><span data-stu-id="417bb-113">Calling `RemapFunction`, like calling [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md), will immediately invalidate all debugging interfaces that are related to generating a stack trace for the thread.</span></span> <span data-ttu-id="417bb-114">Ces interfaces incluent [ICorDebugChain](icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame et ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="417bb-114">These interfaces include [ICorDebugChain](icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame, and ICorDebugNativeFrame.</span></span>  
  
 <span data-ttu-id="417bb-115">La `RemapFunction` méthode peut être appelée uniquement dans le contexte du frame actuel, et uniquement dans l’un des cas suivants :</span><span class="sxs-lookup"><span data-stu-id="417bb-115">The `RemapFunction` method can be called only in the context of the current frame, and only in one of the following cases:</span></span>  
  
- <span data-ttu-id="417bb-116">Après réception d’un rappel [ICorDebugManagedCallback2 :: FunctionRemapOpportunity,](icordebugmanagedcallback2-functionremapopportunity-method.md) qui n’a pas encore été poursuivi.</span><span class="sxs-lookup"><span data-stu-id="417bb-116">After receipt of a [ICorDebugManagedCallback2::FunctionRemapOpportunity](icordebugmanagedcallback2-functionremapopportunity-method.md) callback that has not yet been continued.</span></span>  
  
- <span data-ttu-id="417bb-117">Pendant l’arrêt de l’exécution du code en raison d’un événement [ICorDebugManagedCallback :: EditAndContinueRemap,](icordebugmanagedcallback-editandcontinueremap-method.md) pour ce frame.</span><span class="sxs-lookup"><span data-stu-id="417bb-117">While code execution is stopped because of an [ICorDebugManagedCallback::EditAndContinueRemap](icordebugmanagedcallback-editandcontinueremap-method.md) event for this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="417bb-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="417bb-118">Requirements</span></span>  

 <span data-ttu-id="417bb-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="417bb-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="417bb-120">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="417bb-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="417bb-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="417bb-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="417bb-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="417bb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
