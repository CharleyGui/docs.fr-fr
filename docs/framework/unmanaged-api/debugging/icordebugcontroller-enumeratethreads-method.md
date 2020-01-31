---
title: ICorDebugController::EnumerateThreads, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugController.EnumerateThreads
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type:
- apiref
ms.openlocfilehash: 815dc63a2dedecc613506b0f98702f58d6e7bd04
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783788"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="95be0-102">ICorDebugController::EnumerateThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="95be0-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="95be0-103">Obtient un énumérateur pour les threads managés actifs dans le processus.</span><span class="sxs-lookup"><span data-stu-id="95be0-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95be0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95be0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95be0-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="95be0-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="95be0-106">à Pointeur vers l’adresse d’un objet « ICorDebugThreadEnum » qui représente un énumérateur pour tous les threads managés qui sont actifs dans le processus.</span><span class="sxs-lookup"><span data-stu-id="95be0-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95be0-107">Notes</span><span class="sxs-lookup"><span data-stu-id="95be0-107">Remarks</span></span>  
 <span data-ttu-id="95be0-108">Un thread est considéré comme actif après la distribution du rappel [ICorDebugManagedCallback :: CreateThread](icordebugmanagedcallback-createthread-method.md) et avant la distribution du rappel [ICorDebugManagedCallback :: ExitThread](icordebugmanagedcallback-exitthread-method.md) .</span><span class="sxs-lookup"><span data-stu-id="95be0-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="95be0-109">Un thread managé ne peut pas nécessairement avoir des frames managés sur sa pile.</span><span class="sxs-lookup"><span data-stu-id="95be0-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="95be0-110">Les threads peuvent être énumérés avant même le rappel [ICorDebugManagedCallback :: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="95be0-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="95be0-111">L’énumération est naturellement vide.</span><span class="sxs-lookup"><span data-stu-id="95be0-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95be0-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="95be0-112">Requirements</span></span>  
 <span data-ttu-id="95be0-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95be0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95be0-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95be0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95be0-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95be0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95be0-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95be0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95be0-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95be0-117">See also</span></span>
