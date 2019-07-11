---
title: ICorDebugThread::GetUserState, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetUserState
helpviewer_keywords:
- GetUserState method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetUserState method [.NET Framework debugging]
ms.assetid: ae0cfd73-8ead-4d36-9310-dccaac9db0bd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7d3325c8aee44849ff1fb7a6cc06a0ed7c2c6f8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769104"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="e1896-102">ICorDebugThread::GetUserState, méthode</span><span class="sxs-lookup"><span data-stu-id="e1896-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="e1896-103">Obtient l’état utilisateur actuel de ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="e1896-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1896-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1896-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1896-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e1896-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="e1896-106">[out] Pointeur vers une combinaison au niveau du bit des valeurs d’énumération CorDebugUserState qui décrivent l’état utilisateur actuel de ce thread.</span><span class="sxs-lookup"><span data-stu-id="e1896-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1896-107">Notes</span><span class="sxs-lookup"><span data-stu-id="e1896-107">Remarks</span></span>  
 <span data-ttu-id="e1896-108">L’état utilisateur du thread est l’état du thread lorsqu’il est examiné par le programme est en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="e1896-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="e1896-109">Un thread peut avoir plusieurs bits d’état à définir.</span><span class="sxs-lookup"><span data-stu-id="e1896-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1896-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e1896-110">Requirements</span></span>  
 <span data-ttu-id="e1896-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1896-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1896-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1896-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1896-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1896-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1896-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1896-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
