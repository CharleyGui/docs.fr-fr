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
ms.openlocfilehash: 73ed86ee12b02d292dc6dfc1d652459a679f81ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679934"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="376f1-102">ICorDebugController::IsRunning, méthode</span><span class="sxs-lookup"><span data-stu-id="376f1-102">ICorDebugController::IsRunning Method</span></span>

<span data-ttu-id="376f1-103">Obtient une valeur qui indique si les threads du processus sont en cours d’exécution librement.</span><span class="sxs-lookup"><span data-stu-id="376f1-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="376f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="376f1-104">Syntax</span></span>  
  
```cpp  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="376f1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="376f1-105">Parameters</span></span>  

 `pbRunning`  
 <span data-ttu-id="376f1-106">à Pointeur vers une valeur qui est `true` si les threads dans le processus s’exécutent librement ; sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="376f1-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="376f1-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="376f1-107">Requirements</span></span>  

 <span data-ttu-id="376f1-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="376f1-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="376f1-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="376f1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="376f1-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="376f1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="376f1-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="376f1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="376f1-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="376f1-112">See also</span></span>
