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
ms.openlocfilehash: 89ea9f221ad55063e4186cc27cc8038334d800d4
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892875"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="ed0b3-102">ICorDebugController::IsRunning, méthode</span><span class="sxs-lookup"><span data-stu-id="ed0b3-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="ed0b3-103">Obtient une valeur qui indique si les threads du processus sont en cours d’exécution librement.</span><span class="sxs-lookup"><span data-stu-id="ed0b3-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed0b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed0b3-104">Syntax</span></span>  
  
```cpp  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed0b3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ed0b3-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="ed0b3-106">à Pointeur vers une valeur qui est `true` si les threads du processus s’exécutent librement ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="ed0b3-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed0b3-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ed0b3-107">Requirements</span></span>  
 <span data-ttu-id="ed0b3-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed0b3-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed0b3-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ed0b3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed0b3-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed0b3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed0b3-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed0b3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed0b3-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed0b3-112">See also</span></span>
