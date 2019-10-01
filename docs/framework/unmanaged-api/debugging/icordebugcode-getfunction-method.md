---
title: ICorDebugCode::GetFunction, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetFunction method [.NET Framework debugging]
ms.assetid: c568b737-fdb2-4816-accd-051f5ab760f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 825840536968562a53d9e05b8a4628a1df79407d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700831"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="c498c-102">ICorDebugCode::GetFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="c498c-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="c498c-103">Obtient le « ICorDebugFunction » associé à ce « ICorDebugCode ».</span><span class="sxs-lookup"><span data-stu-id="c498c-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c498c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c498c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c498c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c498c-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="c498c-106">à Pointeur vers l’adresse de la fonction.</span><span class="sxs-lookup"><span data-stu-id="c498c-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c498c-107">Notes</span><span class="sxs-lookup"><span data-stu-id="c498c-107">Remarks</span></span>  
 <span data-ttu-id="c498c-108">`ICorDebugCode` et `ICorDebugFunction` gèrent une relation un-à-un.</span><span class="sxs-lookup"><span data-stu-id="c498c-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c498c-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c498c-109">Requirements</span></span>  
 <span data-ttu-id="c498c-110">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c498c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c498c-111">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c498c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c498c-112">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c498c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c498c-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c498c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
