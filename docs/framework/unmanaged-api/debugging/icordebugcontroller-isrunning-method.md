---
title: ICorDebugController::IsRunning, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugController.IsRunning
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::IsRunning
helpviewer_keywords:
- IsRunning method [.NET Framework debugging]
- ICorDebugController::IsRunning method [.NET Framework debugging]
ms.assetid: b33ff059-40c4-4dfe-9cb2-21bfed2de0b0
topic_type:
- apiref
ms.openlocfilehash: f24c07a654dc2345cb65226463573576a6fb3658
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125342"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="43944-102">ICorDebugController::IsRunning, méthode</span><span class="sxs-lookup"><span data-stu-id="43944-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="43944-103">Obtient une valeur qui indique si les threads du processus sont en cours d’exécution librement.</span><span class="sxs-lookup"><span data-stu-id="43944-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43944-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43944-104">Syntax</span></span>  
  
```cpp  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43944-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="43944-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="43944-106">à Pointeur vers une valeur `true` si les threads du processus s’exécutent librement ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="43944-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43944-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="43944-107">Requirements</span></span>  
 <span data-ttu-id="43944-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43944-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43944-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43944-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43944-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43944-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43944-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43944-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43944-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43944-112">See also</span></span>
