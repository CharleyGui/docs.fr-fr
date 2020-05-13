---
title: ICorDebugManagedCallback::Break, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Break
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type:
- apiref
ms.openlocfilehash: f70a88df00d15729a6bde06b49417b6439f7c0ec
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212462"
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="a6250-102">ICorDebugManagedCallback::Break, méthode</span><span class="sxs-lookup"><span data-stu-id="a6250-102">ICorDebugManagedCallback::Break Method</span></span>

<span data-ttu-id="a6250-103">Notifie le débogueur lorsqu’une <xref:System.Reflection.Emit.OpCodes.Break> instruction dans le flux de code est exécutée.</span><span class="sxs-lookup"><span data-stu-id="a6250-103">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="a6250-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6250-104">Syntax</span></span>

```cpp
HRESULT Break (
    [in] ICorDebugAppDomain *pAppDomain,
    [in] ICorDebugThread    *thread
);
```

## <a name="parameters"></a><span data-ttu-id="a6250-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a6250-105">Parameters</span></span>

`pAppDomain`\
<span data-ttu-id="a6250-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application qui contient l’instruction Break.</span><span class="sxs-lookup"><span data-stu-id="a6250-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>

`thread`\
<span data-ttu-id="a6250-107">dans Pointeur vers un objet ICorDebugThread qui représente le thread qui contient l’instruction Break.</span><span class="sxs-lookup"><span data-stu-id="a6250-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>

## <a name="requirements"></a><span data-ttu-id="a6250-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a6250-108">Requirements</span></span>

<span data-ttu-id="a6250-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6250-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="a6250-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6250-110">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="a6250-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6250-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a6250-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6250-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a6250-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6250-113">See also</span></span>

- [<span data-ttu-id="a6250-114">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="a6250-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
