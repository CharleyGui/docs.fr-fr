---
title: ICorDebugILFrame::SetIP, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
ms.openlocfilehash: 466fe421f4ff3f8983159ccb38503b75551c87bd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788555"
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="847e4-102">ICorDebugILFrame::SetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="847e4-102">ICorDebugILFrame::SetIP Method</span></span>
<span data-ttu-id="847e4-103">Définit le pointeur d’instruction à l’emplacement de décalage spécifié dans le code MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="847e4-103">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="847e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="847e4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="847e4-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="847e4-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="847e4-106">Emplacement de décalage dans le code MSIL.</span><span class="sxs-lookup"><span data-stu-id="847e4-106">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="847e4-107">Notes</span><span class="sxs-lookup"><span data-stu-id="847e4-107">Remarks</span></span>  
 <span data-ttu-id="847e4-108">Les appels à `SetIP` invalident immédiatement tous les frames et chaînes pour le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="847e4-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="847e4-109">Si le débogueur a besoin d’informations de frame après un appel à `SetIP`, il doit effectuer une nouvelle trace de la pile.</span><span class="sxs-lookup"><span data-stu-id="847e4-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="847e4-110">[ICorDebug](icordebug-interface.md) tente de conserver le frame de pile dans un état valide.</span><span class="sxs-lookup"><span data-stu-id="847e4-110">[ICorDebug](icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="847e4-111">Toutefois, même si le frame est dans un état valide, il peut y avoir des problèmes tels que les variables locales non initialisées.</span><span class="sxs-lookup"><span data-stu-id="847e4-111">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="847e4-112">L’appelant est chargé de garantir la cohérence du programme en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="847e4-112">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="847e4-113">Sur les plateformes 64 bits, le pointeur d’instruction ne peut pas être déplacé hors d’un bloc `catch` ou `finally`.</span><span class="sxs-lookup"><span data-stu-id="847e4-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="847e4-114">Si `SetIP` est appelé pour effectuer ce déplacement sur une plateforme 64 bits, un HRESULT indiquant un échec est retourné.</span><span class="sxs-lookup"><span data-stu-id="847e4-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="847e4-115">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="847e4-115">Requirements</span></span>  
 <span data-ttu-id="847e4-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="847e4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="847e4-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="847e4-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="847e4-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="847e4-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="847e4-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="847e4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
