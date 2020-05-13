---
title: ICorDebugNativeFrame::SetIP, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type:
- apiref
ms.openlocfilehash: 786c0e7b38c74fd02dd6f7536af1899f295b0305
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206443"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="82bd2-102">ICorDebugNativeFrame::SetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="82bd2-102">ICorDebugNativeFrame::SetIP Method</span></span>
<span data-ttu-id="82bd2-103">Définit le pointeur d’instruction à l’emplacement d’offset spécifié en code natif.</span><span class="sxs-lookup"><span data-stu-id="82bd2-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82bd2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82bd2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82bd2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="82bd2-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="82bd2-106">dans Emplacement de décalage dans le code natif.</span><span class="sxs-lookup"><span data-stu-id="82bd2-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82bd2-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="82bd2-107">Remarks</span></span>  
 <span data-ttu-id="82bd2-108">Les appels à `SetIP` invalident immédiatement tous les frames et chaînes pour le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="82bd2-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="82bd2-109">Si le débogueur a besoin d’informations de frame après un appel à `SetIP` , il doit effectuer une nouvelle trace de la pile.</span><span class="sxs-lookup"><span data-stu-id="82bd2-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="82bd2-110">[ICorDebug](icordebug-interface.md) tente de conserver le frame de pile dans un état valide.</span><span class="sxs-lookup"><span data-stu-id="82bd2-110">[ICorDebug](icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="82bd2-111">Toutefois, même si le frame est dans un état valide, en ce qui concerne le runtime, il existe toujours des problèmes, tels que les variables locales non initialisées, etc.</span><span class="sxs-lookup"><span data-stu-id="82bd2-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="82bd2-112">L’appelant est chargé d’assurer la cohérence du programme en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="82bd2-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="82bd2-113">Sur les plateformes 64 bits, le pointeur d’instruction ne peut pas être déplacé hors d’un `catch` `finally` bloc ou.</span><span class="sxs-lookup"><span data-stu-id="82bd2-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="82bd2-114">Si `SetIP` est appelé pour effectuer ce déplacement sur une plateforme 64 bits, il retourne un HRESULT indiquant un échec.</span><span class="sxs-lookup"><span data-stu-id="82bd2-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82bd2-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="82bd2-115">Requirements</span></span>  
 <span data-ttu-id="82bd2-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82bd2-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82bd2-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82bd2-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82bd2-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82bd2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82bd2-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82bd2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82bd2-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82bd2-120">See also</span></span>
