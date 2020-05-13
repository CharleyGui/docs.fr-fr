---
title: ICorDebugProcess4 ::P méthode rocessStateChanged
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4::ProcessStateChanged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4::ProcessStateChanged
helpviewer_keywords:
- ICorDebugProcess4::ProcessStateChanged method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 910c411d2c63ce2c6cf262e28e08546657dc2a4c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213567"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="fa6df-102">ICorDebugProcess4 ::P méthode rocessStateChanged</span><span class="sxs-lookup"><span data-stu-id="fa6df-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="fa6df-103">Notifie le pipeline ICorDebug que le débogueur hors processus poursuit l’exécution du débogueur.</span><span class="sxs-lookup"><span data-stu-id="fa6df-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="fa6df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa6df-104">Syntax</span></span>

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="fa6df-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fa6df-105">Parameters</span></span>

 `eChange`\
<span data-ttu-id="fa6df-106">dans Membre de l' [énumération cordebugstatechange,](cordebugstatechange-enumeration.md) décrivant une modification de l’état d’exécution du processus.</span><span class="sxs-lookup"><span data-stu-id="fa6df-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="fa6df-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="fa6df-107">Remarks</span></span>

<span data-ttu-id="fa6df-108">La méthode fournie fait partie de l' `ICorDebugProcess4` interface et correspond au quatrième emplacement de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="fa6df-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="fa6df-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fa6df-109">Requirements</span></span>

 <span data-ttu-id="fa6df-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa6df-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="fa6df-111">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="fa6df-111">**Header:** None</span></span>

 <span data-ttu-id="fa6df-112">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="fa6df-112">**Library:** None</span></span>

 <span data-ttu-id="fa6df-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa6df-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="fa6df-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa6df-114">See also</span></span>

- [<span data-ttu-id="fa6df-115">ICorDebugProcess4, interface</span><span class="sxs-lookup"><span data-stu-id="fa6df-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="fa6df-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="fa6df-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="fa6df-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="fa6df-117">Debugging</span></span>](index.md)
