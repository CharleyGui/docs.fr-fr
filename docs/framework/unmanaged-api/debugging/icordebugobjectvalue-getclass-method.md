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
ms.openlocfilehash: d15938e94d647fd5fded23c72bdc200d198d21a7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792704"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="2be00-102">ICorDebugObjectValue::GetClass, méthode</span><span class="sxs-lookup"><span data-stu-id="2be00-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="2be00-103">Obtient la classe de cette valeur d’objet.</span><span class="sxs-lookup"><span data-stu-id="2be00-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2be00-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2be00-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2be00-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="2be00-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="2be00-106">à Pointeur vers l’adresse d’un objet « ICorDebugClass » qui représente la classe de la valeur de l’objet représentée par cet objet « ICorDebugObjectValue ».</span><span class="sxs-lookup"><span data-stu-id="2be00-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2be00-107">Notes</span><span class="sxs-lookup"><span data-stu-id="2be00-107">Remarks</span></span>  
 <span data-ttu-id="2be00-108">Les méthodes `GetClass` et [ICorDebugValue :: GetType](icordebugvalue-gettype-method.md) retournent chacune des informations sur le type d’une valeur ; ils sont tous deux remplacés par le [ICorDebugValue2 :: GetExactType,](icordebugvalue2-getexacttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="2be00-108">The `GetClass` and [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2be00-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="2be00-109">Requirements</span></span>  
 <span data-ttu-id="2be00-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2be00-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2be00-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2be00-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2be00-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2be00-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2be00-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2be00-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2be00-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2be00-114">See also</span></span>
