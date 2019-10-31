---
title: ICorDebugThread4::GetCurrentCustomDebuggerNotification, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetCurrentCustomDebuggerNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetCurrentCustomDebuggerNotification
helpviewer_keywords:
- GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
- ICorDebugThread4::GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
ms.assetid: 57e0f2d2-5f0e-4e2d-99ec-3f26632eb693
topic_type:
- apiref
ms.openlocfilehash: ba4375511fe7f5aaee032c4e132de54808041111
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122447"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="3edfb-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification, méthode</span><span class="sxs-lookup"><span data-stu-id="3edfb-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>

<span data-ttu-id="3edfb-103">Obtient l’objet [ICorDebugManagedCallback3 :: CustomNotification,](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) actuel sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="3edfb-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>

## <a name="syntax"></a><span data-ttu-id="3edfb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3edfb-104">Syntax</span></span>

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a><span data-ttu-id="3edfb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3edfb-105">Parameters</span></span>

`ppNotificationObject`\
<span data-ttu-id="3edfb-106">à Pointeur vers l’objet de `ICorDebugManagedCallback3::CustomNotification` actuel sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="3edfb-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>

## <a name="remarks"></a><span data-ttu-id="3edfb-107">Notes</span><span class="sxs-lookup"><span data-stu-id="3edfb-107">Remarks</span></span>

<span data-ttu-id="3edfb-108">La valeur de `ppNotificationObject` est null si la méthode n’est pas appelée à partir d’un rappel `ICorDebugManagedCallback3::CustomNotification`, ou si aucun objet de notification en cours n’existe.</span><span class="sxs-lookup"><span data-stu-id="3edfb-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>

## <a name="requirements"></a><span data-ttu-id="3edfb-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="3edfb-109">Requirements</span></span>

<span data-ttu-id="3edfb-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3edfb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="3edfb-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3edfb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="3edfb-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3edfb-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="3edfb-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3edfb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3edfb-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3edfb-114">See also</span></span>

- [<span data-ttu-id="3edfb-115">ICorDebugThread4, interface</span><span class="sxs-lookup"><span data-stu-id="3edfb-115">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="3edfb-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="3edfb-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3edfb-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="3edfb-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
