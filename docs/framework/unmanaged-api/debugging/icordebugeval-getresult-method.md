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
ms.openlocfilehash: 86c017f581c7b980b8b0cb8bd7bdc1b0aa439afe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705819"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="ae69e-102">ICorDebugEval::GetResult, méthode</span><span class="sxs-lookup"><span data-stu-id="ae69e-102">ICorDebugEval::GetResult Method</span></span>

<span data-ttu-id="ae69e-103">Obtient les résultats de cette évaluation.</span><span class="sxs-lookup"><span data-stu-id="ae69e-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae69e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae69e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae69e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ae69e-105">Parameters</span></span>  

 `ppResult`  
 <span data-ttu-id="ae69e-106">à Pointeur vers l’adresse d’un objet ICorDebugValue qui représente les résultats de cette évaluation, si l’évaluation se termine normalement.</span><span class="sxs-lookup"><span data-stu-id="ae69e-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae69e-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="ae69e-107">Remarks</span></span>  

 <span data-ttu-id="ae69e-108">La `GetResult` méthode est valide uniquement une fois l’évaluation terminée.</span><span class="sxs-lookup"><span data-stu-id="ae69e-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="ae69e-109">Si l’évaluation se termine normalement, `ppResult` spécifie les résultats.</span><span class="sxs-lookup"><span data-stu-id="ae69e-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="ae69e-110">Si elle se termine avec une exception, le résultat est l’exception levée.</span><span class="sxs-lookup"><span data-stu-id="ae69e-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="ae69e-111">Si l’évaluation s’est produite pour un nouvel objet, le résultat est la référence au nouvel objet.</span><span class="sxs-lookup"><span data-stu-id="ae69e-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae69e-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ae69e-112">Requirements</span></span>  

 <span data-ttu-id="ae69e-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae69e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae69e-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae69e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae69e-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae69e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae69e-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae69e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
