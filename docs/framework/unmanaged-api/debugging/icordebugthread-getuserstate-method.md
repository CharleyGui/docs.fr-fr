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
ms.openlocfilehash: dd3936656ce1c9482b7f07a5780fcf651356b4be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727963"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="a0a48-102">ICorDebugThread::GetUserState, méthode</span><span class="sxs-lookup"><span data-stu-id="a0a48-102">ICorDebugThread::GetUserState Method</span></span>

<span data-ttu-id="a0a48-103">Obtient l’état utilisateur actuel de ce ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="a0a48-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0a48-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0a48-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0a48-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a0a48-105">Parameters</span></span>  

 `pState`  
 <span data-ttu-id="a0a48-106">à Pointeur vers une combinaison d’opérations de bits de valeurs d’énumération CorDebugUserState, qui décrivent l’état utilisateur actuel de ce thread.</span><span class="sxs-lookup"><span data-stu-id="a0a48-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0a48-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="a0a48-107">Remarks</span></span>  

 <span data-ttu-id="a0a48-108">L’état utilisateur du thread est l’état du thread lorsqu’il est examiné par le programme en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="a0a48-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="a0a48-109">Un thread peut avoir plusieurs bits d’État définis.</span><span class="sxs-lookup"><span data-stu-id="a0a48-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0a48-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a0a48-110">Requirements</span></span>  

 <span data-ttu-id="a0a48-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0a48-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0a48-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0a48-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0a48-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0a48-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0a48-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0a48-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
