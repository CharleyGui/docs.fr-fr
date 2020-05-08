---
title: ICorDebugEval::Abort, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval.Abort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::Abort
helpviewer_keywords:
- Abort method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::Abort method [.NET Framework debugging]
ms.assetid: 7070b6d0-f2e0-44ff-b124-0944cd807e69
topic_type:
- apiref
ms.openlocfilehash: 98a9b285323bc3ad94b4f555e72a4b3242519801
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976289"
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="01b34-102">ICorDebugEval::Abort, méthode</span><span class="sxs-lookup"><span data-stu-id="01b34-102">ICorDebugEval::Abort Method</span></span>
<span data-ttu-id="01b34-103">Abandonne le calcul actuellement effectué par cet objet ICorDebugEval.</span><span class="sxs-lookup"><span data-stu-id="01b34-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01b34-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01b34-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="01b34-105">Notes </span><span class="sxs-lookup"><span data-stu-id="01b34-105">Remarks</span></span>  
 <span data-ttu-id="01b34-106">Si l’évaluation est imbriquée et qu’il ne s’agit pas de la version `Abort` la plus récente, la méthode peut échouer.</span><span class="sxs-lookup"><span data-stu-id="01b34-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01b34-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="01b34-107">Requirements</span></span>  
 <span data-ttu-id="01b34-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01b34-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01b34-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01b34-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01b34-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01b34-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01b34-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01b34-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
