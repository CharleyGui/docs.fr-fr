---
title: ICorDebugProcess4::ProcessStateChanged Method
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
ms.openlocfilehash: a6f36f5b86b4fa58ce2a4ef4aa23d527f797a5a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178630"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="e48fc-102">ICorDebugProcess4::ProcessStateChanged Method</span><span class="sxs-lookup"><span data-stu-id="e48fc-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="e48fc-103">Informe le pipeline ICorDebug que le débbuggeur hors processus poursuit l’exécution du débbugee.</span><span class="sxs-lookup"><span data-stu-id="e48fc-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="e48fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e48fc-104">Syntax</span></span>

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="e48fc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e48fc-105">Parameters</span></span>

 `eChange`\
<span data-ttu-id="e48fc-106">[dans] Un membre du [recensement corDebugStateChange](cordebugstatechange-enumeration.md) décrivant un changement dans l’état d’exécution du processus.</span><span class="sxs-lookup"><span data-stu-id="e48fc-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="e48fc-107">Notes </span><span class="sxs-lookup"><span data-stu-id="e48fc-107">Remarks</span></span>

<span data-ttu-id="e48fc-108">La méthode fournie fait `ICorDebugProcess4` partie de l’interface et correspond à la quatrième fente de la table de méthode virtuelle.</span><span class="sxs-lookup"><span data-stu-id="e48fc-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="e48fc-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e48fc-109">Requirements</span></span>

 <span data-ttu-id="e48fc-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e48fc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="e48fc-111">**En-tête:** Aucun</span><span class="sxs-lookup"><span data-stu-id="e48fc-111">**Header:** None</span></span>

 <span data-ttu-id="e48fc-112">**Bibliothèque:** Aucun</span><span class="sxs-lookup"><span data-stu-id="e48fc-112">**Library:** None</span></span>

 <span data-ttu-id="e48fc-113">**.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e48fc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e48fc-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e48fc-114">See also</span></span>

- [<span data-ttu-id="e48fc-115">ICorDebugProcess4, interface</span><span class="sxs-lookup"><span data-stu-id="e48fc-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="e48fc-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e48fc-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e48fc-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="e48fc-117">Debugging</span></span>](index.md)
