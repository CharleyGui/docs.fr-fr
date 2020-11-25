---
title: ICorDebugEval::GetThread, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::GetThread method [.NET Framework debugging]
ms.assetid: 57163b0d-c8a7-44af-9078-e7a895d29f9a
topic_type:
- apiref
ms.openlocfilehash: 0680c47e4390e876c5df99ee7eb200e7d187f0ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722191"
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="d02a6-102">ICorDebugEval::GetThread, méthode</span><span class="sxs-lookup"><span data-stu-id="d02a6-102">ICorDebugEval::GetThread Method</span></span>

<span data-ttu-id="d02a6-103">Obtient le thread dans lequel cette évaluation est en cours d’exécution ou s’exécute.</span><span class="sxs-lookup"><span data-stu-id="d02a6-103">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d02a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d02a6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d02a6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d02a6-105">Parameters</span></span>  

 `ppThread`  
 <span data-ttu-id="d02a6-106">à Pointeur vers l’adresse d’un objet ICorDebugThread qui représente le thread.</span><span class="sxs-lookup"><span data-stu-id="d02a6-106">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d02a6-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d02a6-107">Requirements</span></span>  

 <span data-ttu-id="d02a6-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d02a6-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d02a6-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d02a6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d02a6-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d02a6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d02a6-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d02a6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
