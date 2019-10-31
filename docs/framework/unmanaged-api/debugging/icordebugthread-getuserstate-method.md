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
ms.openlocfilehash: f3511ff5ee9b9221037c64a5e17d61f6bf52e5f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133407"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="ca683-102">ICorDebugThread::GetUserState, méthode</span><span class="sxs-lookup"><span data-stu-id="ca683-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="ca683-103">Obtient l’état utilisateur actuel de ce ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="ca683-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca683-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca683-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca683-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ca683-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="ca683-106">à Pointeur vers une combinaison d’opérations de bits de valeurs d’énumération CorDebugUserState, qui décrivent l’état utilisateur actuel de ce thread.</span><span class="sxs-lookup"><span data-stu-id="ca683-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca683-107">Notes</span><span class="sxs-lookup"><span data-stu-id="ca683-107">Remarks</span></span>  
 <span data-ttu-id="ca683-108">L’état utilisateur du thread est l’état du thread lorsqu’il est examiné par le programme en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="ca683-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="ca683-109">Un thread peut avoir plusieurs bits d’État définis.</span><span class="sxs-lookup"><span data-stu-id="ca683-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca683-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="ca683-110">Requirements</span></span>  
 <span data-ttu-id="ca683-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca683-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca683-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca683-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca683-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca683-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca683-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca683-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
