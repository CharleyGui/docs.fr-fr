---
title: ICorDebugGenericValue::SetValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::SetValue
helpviewer_keywords:
- ICorDebugGenericValue::SetValue method [.NET Framework debugging]
- SetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: ed4c6458-0435-44fc-8e78-8ba00be362f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b6907cdf78fc70c75ddd711cd8593427857b172
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756895"
---
# <a name="icordebuggenericvaluesetvalue-method"></a><span data-ttu-id="6c83e-102">ICorDebugGenericValue::SetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="6c83e-102">ICorDebugGenericValue::SetValue Method</span></span>
<span data-ttu-id="6c83e-103">Copie une nouvelle valeur à partir de la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6c83e-103">Copies a new value from the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c83e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c83e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c83e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6c83e-105">Parameters</span></span>  
 `pFrom`  
 <span data-ttu-id="6c83e-106">[in] Pointeur vers la mémoire tampon à partir duquel copier la valeur.</span><span class="sxs-lookup"><span data-stu-id="6c83e-106">[in] A pointer to the buffer from which to copy the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c83e-107">Notes</span><span class="sxs-lookup"><span data-stu-id="6c83e-107">Remarks</span></span>  
 <span data-ttu-id="6c83e-108">Pour les types référence, la valeur est la référence, pas le contenu.</span><span class="sxs-lookup"><span data-stu-id="6c83e-108">For reference types, the value is the reference, not the content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c83e-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6c83e-109">Requirements</span></span>  
 <span data-ttu-id="6c83e-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c83e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c83e-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c83e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c83e-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c83e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c83e-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c83e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
