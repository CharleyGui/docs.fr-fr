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
ms.openlocfilehash: d1ff3427feb5dc8395bbb2fda78e3e93e1a1a8f0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378855"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="42de6-102">ICorDebugThread::GetUserState, méthode</span><span class="sxs-lookup"><span data-stu-id="42de6-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="42de6-103">Obtient l’état utilisateur actuel de ce ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="42de6-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42de6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42de6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42de6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="42de6-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="42de6-106">à Pointeur vers une combinaison d’opérations de bits de valeurs d’énumération CorDebugUserState, qui décrivent l’état utilisateur actuel de ce thread.</span><span class="sxs-lookup"><span data-stu-id="42de6-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42de6-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="42de6-107">Remarks</span></span>  
 <span data-ttu-id="42de6-108">L’état utilisateur du thread est l’état du thread lorsqu’il est examiné par le programme en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="42de6-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="42de6-109">Un thread peut avoir plusieurs bits d’État définis.</span><span class="sxs-lookup"><span data-stu-id="42de6-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42de6-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="42de6-110">Requirements</span></span>  
 <span data-ttu-id="42de6-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42de6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42de6-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42de6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42de6-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42de6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42de6-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42de6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
