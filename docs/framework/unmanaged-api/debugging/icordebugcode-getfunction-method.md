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
ms.openlocfilehash: 9f785eafa8925324e3bd269ca08a3b1367b74c44
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893585"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="7cadc-102">ICorDebugCode::GetFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="7cadc-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="7cadc-103">Obtient le « ICorDebugFunction » associé à ce « ICorDebugCode ».</span><span class="sxs-lookup"><span data-stu-id="7cadc-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cadc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7cadc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cadc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7cadc-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="7cadc-106">à Pointeur vers l’adresse de la fonction.</span><span class="sxs-lookup"><span data-stu-id="7cadc-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cadc-107">Notes </span><span class="sxs-lookup"><span data-stu-id="7cadc-107">Remarks</span></span>  
 <span data-ttu-id="7cadc-108">`ICorDebugCode`et `ICorDebugFunction` gèrent une relation un-à-un.</span><span class="sxs-lookup"><span data-stu-id="7cadc-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cadc-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7cadc-109">Requirements</span></span>  
 <span data-ttu-id="7cadc-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cadc-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cadc-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7cadc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7cadc-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cadc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cadc-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cadc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
