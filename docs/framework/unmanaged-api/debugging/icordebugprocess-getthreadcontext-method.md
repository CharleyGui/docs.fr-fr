---
title: ICorDebugProcess::GetThreadContext, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type:
- apiref
ms.openlocfilehash: 2bdbf373144e2fb49074cfd035e7b0ffe3c8c291
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212884"
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="d8ea7-102">ICorDebugProcess::GetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="d8ea7-102">ICorDebugProcess::GetThreadContext Method</span></span>
<span data-ttu-id="d8ea7-103">Obtient le contexte du thread donné dans ce processus.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-103">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8ea7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8ea7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8ea7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d8ea7-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="d8ea7-106">dans ID du thread pour lequel récupérer le contexte.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-106">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="d8ea7-107">[in] Taille du tableau `context`.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="d8ea7-108">[in, out] Tableau d’octets qui décrivent le contexte du thread.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-108">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="d8ea7-109">Le contexte spécifie l’architecture du processeur sur lequel le thread s’exécute.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8ea7-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="d8ea7-110">Remarks</span></span>  
 <span data-ttu-id="d8ea7-111">Le débogueur doit appeler cette méthode plutôt que la `GetThreadContext` méthode Win32, car le thread peut être dans un État « détourné », dans lequel son contexte a été modifié temporairement.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-111">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="d8ea7-112">Cette méthode doit être utilisée uniquement quand un thread est en code natif.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="d8ea7-113">Utilisez [ICorDebugRegisterSet](icordebugregisterset-interface.md) pour les threads dans le code managé.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-113">Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="d8ea7-114">Les données retournées sont une structure de contexte pour la plateforme actuelle.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-114">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="d8ea7-115">À l’instar de la `GetThreadContext` méthode Win32, l’appelant doit initialiser le `context` paramètre avant d’appeler cette méthode.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-115">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8ea7-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d8ea7-116">Requirements</span></span>  
 <span data-ttu-id="d8ea7-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8ea7-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8ea7-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8ea7-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8ea7-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8ea7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8ea7-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8ea7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
