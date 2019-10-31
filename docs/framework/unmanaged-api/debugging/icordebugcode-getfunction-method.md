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
ms.openlocfilehash: 217ca0a850926e5f697340cece264c6ed442a9bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125642"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="417b2-102">ICorDebugCode::GetFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="417b2-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="417b2-103">Obtient le « ICorDebugFunction » associé à ce « ICorDebugCode ».</span><span class="sxs-lookup"><span data-stu-id="417b2-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="417b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="417b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="417b2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="417b2-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="417b2-106">à Pointeur vers l’adresse de la fonction.</span><span class="sxs-lookup"><span data-stu-id="417b2-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="417b2-107">Notes</span><span class="sxs-lookup"><span data-stu-id="417b2-107">Remarks</span></span>  
 <span data-ttu-id="417b2-108">`ICorDebugCode` et `ICorDebugFunction` gérer une relation un-à-un.</span><span class="sxs-lookup"><span data-stu-id="417b2-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="417b2-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="417b2-109">Requirements</span></span>  
 <span data-ttu-id="417b2-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="417b2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="417b2-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="417b2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="417b2-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="417b2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="417b2-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="417b2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
