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
ms.openlocfilehash: 6e6ea5e42c5e1b1943a080ae02e1dbf6d702bebc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705850"
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="5784f-102">ICorDebugEval::Abort, méthode</span><span class="sxs-lookup"><span data-stu-id="5784f-102">ICorDebugEval::Abort Method</span></span>

<span data-ttu-id="5784f-103">Abandonne le calcul actuellement effectué par cet objet ICorDebugEval.</span><span class="sxs-lookup"><span data-stu-id="5784f-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5784f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5784f-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5784f-105">Notes</span><span class="sxs-lookup"><span data-stu-id="5784f-105">Remarks</span></span>  

 <span data-ttu-id="5784f-106">Si l’évaluation est imbriquée et qu’il ne s’agit pas de la version la plus récente, la `Abort` méthode peut échouer.</span><span class="sxs-lookup"><span data-stu-id="5784f-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5784f-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5784f-107">Requirements</span></span>  

 <span data-ttu-id="5784f-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5784f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5784f-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5784f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5784f-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5784f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5784f-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5784f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
