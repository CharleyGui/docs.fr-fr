---
title: ICorDebugObjectValue::GetClass, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetClass
helpviewer_keywords:
- ICorDebugObjectValue::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 5be25292-8357-445f-a09b-f997c0de761c
topic_type:
- apiref
ms.openlocfilehash: 4719f155957f04471d4ad2b8d71bec9c0f0d30c0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096088"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="b0786-102">ICorDebugObjectValue::GetClass, méthode</span><span class="sxs-lookup"><span data-stu-id="b0786-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="b0786-103">Obtient la classe de cette valeur d’objet.</span><span class="sxs-lookup"><span data-stu-id="b0786-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0786-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0786-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0786-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b0786-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="b0786-106">à Pointeur vers l’adresse d’un objet « ICorDebugClass » qui représente la classe de la valeur de l’objet représentée par cet objet « ICorDebugObjectValue ».</span><span class="sxs-lookup"><span data-stu-id="b0786-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0786-107">Notes</span><span class="sxs-lookup"><span data-stu-id="b0786-107">Remarks</span></span>  
 <span data-ttu-id="b0786-108">Les méthodes `GetClass` et [ICorDebugValue :: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) retournent chacune des informations sur le type d’une valeur ; ils sont tous deux remplacés par le [ICorDebugValue2 :: GetExactType,](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="b0786-108">The `GetClass` and [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0786-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="b0786-109">Requirements</span></span>  
 <span data-ttu-id="b0786-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0786-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0786-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0786-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0786-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0786-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0786-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0786-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0786-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0786-114">See also</span></span>
