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
ms.openlocfilehash: a8a377074ca1005ad8089dfd8e2a6a464bb86f60
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791365"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="9c1be-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification, méthode</span><span class="sxs-lookup"><span data-stu-id="9c1be-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>

<span data-ttu-id="9c1be-103">Obtient l’objet [ICorDebugManagedCallback3 :: CustomNotification,](icordebugmanagedcallback3-customnotification-method.md) actuel sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="9c1be-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>

## <a name="syntax"></a><span data-ttu-id="9c1be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c1be-104">Syntax</span></span>

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a><span data-ttu-id="9c1be-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="9c1be-105">Parameters</span></span>

`ppNotificationObject`\
<span data-ttu-id="9c1be-106">à Pointeur vers l’objet de `ICorDebugManagedCallback3::CustomNotification` actuel sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="9c1be-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>

## <a name="remarks"></a><span data-ttu-id="9c1be-107">Notes</span><span class="sxs-lookup"><span data-stu-id="9c1be-107">Remarks</span></span>

<span data-ttu-id="9c1be-108">La valeur de `ppNotificationObject` est null si la méthode n’est pas appelée à partir d’un rappel `ICorDebugManagedCallback3::CustomNotification`, ou si aucun objet de notification en cours n’existe.</span><span class="sxs-lookup"><span data-stu-id="9c1be-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>

## <a name="requirements"></a><span data-ttu-id="9c1be-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="9c1be-109">Requirements</span></span>

<span data-ttu-id="9c1be-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c1be-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="9c1be-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c1be-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="9c1be-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c1be-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="9c1be-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c1be-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9c1be-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c1be-114">See also</span></span>

- [<span data-ttu-id="9c1be-115">ICorDebugThread4, interface</span><span class="sxs-lookup"><span data-stu-id="9c1be-115">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="9c1be-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9c1be-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9c1be-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="9c1be-117">Debugging</span></span>](index.md)
