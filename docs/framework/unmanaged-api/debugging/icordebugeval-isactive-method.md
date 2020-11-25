---
title: ICorDebugEval::IsActive, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::IsActive method [.NET Framework debugging]
ms.assetid: bf2bba24-d278-43bd-b1c5-35680e748d3e
topic_type:
- apiref
ms.openlocfilehash: 5ac221b0b5837175b8073ab29f94c1f28078d3e4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729770"
---
# <a name="icordebugevalisactive-method"></a><span data-ttu-id="616f3-102">ICorDebugEval::IsActive, méthode</span><span class="sxs-lookup"><span data-stu-id="616f3-102">ICorDebugEval::IsActive Method</span></span>

<span data-ttu-id="616f3-103">Obtient une valeur qui indique si cet objet ICorDebugEval est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="616f3-103">Gets a value that indicates whether this ICorDebugEval object is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="616f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="616f3-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL              *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="616f3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="616f3-105">Parameters</span></span>  

 `pbActive`  
 <span data-ttu-id="616f3-106">à Pointeur vers une valeur qui indique si cette évaluation est active.</span><span class="sxs-lookup"><span data-stu-id="616f3-106">[out] Pointer to a value that indicates whether this evaluation is active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="616f3-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="616f3-107">Requirements</span></span>  

 <span data-ttu-id="616f3-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="616f3-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="616f3-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="616f3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="616f3-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="616f3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="616f3-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="616f3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
