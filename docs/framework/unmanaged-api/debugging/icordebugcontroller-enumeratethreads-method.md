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
ms.openlocfilehash: 4d69f13d4716b43c815148ff0fe4aa087b57c6e5
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892757"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="e02e7-102">ICorDebugController::EnumerateThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="e02e7-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="e02e7-103">Obtient un énumérateur pour les threads managés actifs dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e02e7-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e02e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e02e7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e02e7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e02e7-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="e02e7-106">à Pointeur vers l’adresse d’un objet « ICorDebugThreadEnum » qui représente un énumérateur pour tous les threads managés qui sont actifs dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e02e7-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e02e7-107">Notes </span><span class="sxs-lookup"><span data-stu-id="e02e7-107">Remarks</span></span>  
 <span data-ttu-id="e02e7-108">Un thread est considéré comme actif après la distribution du rappel [ICorDebugManagedCallback :: CreateThread](icordebugmanagedcallback-createthread-method.md) et avant la distribution du rappel [ICorDebugManagedCallback :: ExitThread](icordebugmanagedcallback-exitthread-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e02e7-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="e02e7-109">Un thread managé ne peut pas nécessairement avoir des frames managés sur sa pile.</span><span class="sxs-lookup"><span data-stu-id="e02e7-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="e02e7-110">Les threads peuvent être énumérés avant même le rappel [ICorDebugManagedCallback :: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e02e7-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="e02e7-111">L’énumération est naturellement vide.</span><span class="sxs-lookup"><span data-stu-id="e02e7-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e02e7-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e02e7-112">Requirements</span></span>  
 <span data-ttu-id="e02e7-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e02e7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e02e7-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e02e7-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e02e7-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e02e7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e02e7-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e02e7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e02e7-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e02e7-117">See also</span></span>
