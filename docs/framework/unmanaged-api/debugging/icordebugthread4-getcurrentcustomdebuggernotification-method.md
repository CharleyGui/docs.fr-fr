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
ms.openlocfilehash: 76ad1c0ac421f05cf30f6d3d1f3e65848796a0c7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378694"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="c51fc-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification, méthode</span><span class="sxs-lookup"><span data-stu-id="c51fc-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>

<span data-ttu-id="c51fc-103">Obtient l’objet [ICorDebugManagedCallback3 :: CustomNotification,](icordebugmanagedcallback3-customnotification-method.md) actuel sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="c51fc-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>

## <a name="syntax"></a><span data-ttu-id="c51fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c51fc-104">Syntax</span></span>

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a><span data-ttu-id="c51fc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c51fc-105">Parameters</span></span>

`ppNotificationObject`\
<span data-ttu-id="c51fc-106">à Pointeur vers l’objet actuel `ICorDebugManagedCallback3::CustomNotification` sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="c51fc-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>

## <a name="remarks"></a><span data-ttu-id="c51fc-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="c51fc-107">Remarks</span></span>

<span data-ttu-id="c51fc-108">La valeur de `ppNotificationObject` est null si la méthode n’est pas appelée à partir d’un `ICorDebugManagedCallback3::CustomNotification` rappel, ou si aucun objet de notification en cours n’existe.</span><span class="sxs-lookup"><span data-stu-id="c51fc-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>

## <a name="requirements"></a><span data-ttu-id="c51fc-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c51fc-109">Requirements</span></span>

<span data-ttu-id="c51fc-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c51fc-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="c51fc-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c51fc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="c51fc-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c51fc-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="c51fc-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c51fc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c51fc-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c51fc-114">See also</span></span>

- [<span data-ttu-id="c51fc-115">ICorDebugThread4, interface</span><span class="sxs-lookup"><span data-stu-id="c51fc-115">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="c51fc-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c51fc-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c51fc-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="c51fc-117">Debugging</span></span>](index.md)
