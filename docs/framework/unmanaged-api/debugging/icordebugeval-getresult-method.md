---
title: ICorDebugEval::GetResult, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b12ba5ad5c85643d1f4c91585cf7abca210d22bd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752941"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="1e8e7-102">ICorDebugEval::GetResult, méthode</span><span class="sxs-lookup"><span data-stu-id="1e8e7-102">ICorDebugEval::GetResult Method</span></span>
<span data-ttu-id="1e8e7-103">Obtient les résultats de cette évaluation.</span><span class="sxs-lookup"><span data-stu-id="1e8e7-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e8e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e8e7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e8e7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1e8e7-105">Parameters</span></span>  
 `ppResult`  
 <span data-ttu-id="1e8e7-106">[out] Pointeur vers l’adresse d’un objet ICorDebugValue qui représente les résultats de cette évaluation, si l’évaluation se termine normalement.</span><span class="sxs-lookup"><span data-stu-id="1e8e7-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e8e7-107">Notes</span><span class="sxs-lookup"><span data-stu-id="1e8e7-107">Remarks</span></span>  
 <span data-ttu-id="1e8e7-108">Le `GetResult` méthode est valide uniquement lorsque la version d’évaluation est terminée.</span><span class="sxs-lookup"><span data-stu-id="1e8e7-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="1e8e7-109">Si la version d’évaluation se termine normalement, `ppResult` spécifie les résultats.</span><span class="sxs-lookup"><span data-stu-id="1e8e7-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="1e8e7-110">Si elle se termine par une exception, le résultat est l’exception levée.</span><span class="sxs-lookup"><span data-stu-id="1e8e7-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="1e8e7-111">Si l’évaluation a été d’un nouvel objet, le résultat est la référence au nouvel objet.</span><span class="sxs-lookup"><span data-stu-id="1e8e7-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e8e7-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1e8e7-112">Requirements</span></span>  
 <span data-ttu-id="1e8e7-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e8e7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e8e7-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1e8e7-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e8e7-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e8e7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e8e7-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e8e7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
