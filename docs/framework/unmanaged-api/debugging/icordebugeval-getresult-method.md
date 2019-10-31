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
ms.openlocfilehash: 52bfe669d3b078657916554255a11cecfc07d484
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085086"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="1d83d-102">ICorDebugEval::GetResult, méthode</span><span class="sxs-lookup"><span data-stu-id="1d83d-102">ICorDebugEval::GetResult Method</span></span>
<span data-ttu-id="1d83d-103">Obtient les résultats de cette évaluation.</span><span class="sxs-lookup"><span data-stu-id="1d83d-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d83d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d83d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d83d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1d83d-105">Parameters</span></span>  
 `ppResult`  
 <span data-ttu-id="1d83d-106">à Pointeur vers l’adresse d’un objet ICorDebugValue qui représente les résultats de cette évaluation, si l’évaluation se termine normalement.</span><span class="sxs-lookup"><span data-stu-id="1d83d-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d83d-107">Notes</span><span class="sxs-lookup"><span data-stu-id="1d83d-107">Remarks</span></span>  
 <span data-ttu-id="1d83d-108">La méthode `GetResult` est valide uniquement une fois l’évaluation terminée.</span><span class="sxs-lookup"><span data-stu-id="1d83d-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="1d83d-109">Si l’évaluation se termine normalement, `ppResult` spécifie les résultats.</span><span class="sxs-lookup"><span data-stu-id="1d83d-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="1d83d-110">Si elle se termine avec une exception, le résultat est l’exception levée.</span><span class="sxs-lookup"><span data-stu-id="1d83d-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="1d83d-111">Si l’évaluation s’est produite pour un nouvel objet, le résultat est la référence au nouvel objet.</span><span class="sxs-lookup"><span data-stu-id="1d83d-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d83d-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="1d83d-112">Requirements</span></span>  
 <span data-ttu-id="1d83d-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d83d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d83d-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d83d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d83d-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d83d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d83d-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d83d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
