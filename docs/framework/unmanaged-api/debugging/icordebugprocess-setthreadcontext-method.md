---
title: ICorDebugProcess::SetThreadContext, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
ms.openlocfilehash: 5b4052485a6d420eb83578d135ce51f8a918aab0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724518"
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="d876b-102">ICorDebugProcess::SetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="d876b-102">ICorDebugProcess::SetThreadContext Method</span></span>

<span data-ttu-id="d876b-103">Définit le contexte du thread donné dans ce processus.</span><span class="sxs-lookup"><span data-stu-id="d876b-103">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d876b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d876b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d876b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d876b-105">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="d876b-106">dans ID du thread pour lequel définir le contexte.</span><span class="sxs-lookup"><span data-stu-id="d876b-106">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="d876b-107">[in] Taille du tableau `context`.</span><span class="sxs-lookup"><span data-stu-id="d876b-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="d876b-108">dans Tableau d’octets qui décrivent le contexte du thread.</span><span class="sxs-lookup"><span data-stu-id="d876b-108">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="d876b-109">Le contexte spécifie l’architecture du processeur sur lequel le thread s’exécute.</span><span class="sxs-lookup"><span data-stu-id="d876b-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d876b-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="d876b-110">Remarks</span></span>  

 <span data-ttu-id="d876b-111">Le débogueur doit appeler cette méthode plutôt que la `SetThreadContext` fonction Win32, car le thread peut être dans un État « détourné », dans lequel son contexte a été modifié temporairement.</span><span class="sxs-lookup"><span data-stu-id="d876b-111">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="d876b-112">Cette méthode doit être utilisée uniquement quand un thread est en code natif.</span><span class="sxs-lookup"><span data-stu-id="d876b-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="d876b-113">Utilisez [ICorDebugRegisterSet](icordebugregisterset-interface.md) pour les threads dans le code managé.</span><span class="sxs-lookup"><span data-stu-id="d876b-113">Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="d876b-114">Vous ne devez jamais modifier le contexte d’un thread pendant un événement de débogage hors bande (OOB).</span><span class="sxs-lookup"><span data-stu-id="d876b-114">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="d876b-115">Les données passées doivent être une structure de contexte pour la plateforme actuelle.</span><span class="sxs-lookup"><span data-stu-id="d876b-115">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="d876b-116">Cette méthode peut endommager le runtime si elle est utilisée de manière incorrecte.</span><span class="sxs-lookup"><span data-stu-id="d876b-116">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d876b-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d876b-117">Requirements</span></span>  

 <span data-ttu-id="d876b-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d876b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d876b-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d876b-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d876b-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d876b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d876b-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d876b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
