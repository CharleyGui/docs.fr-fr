---
title: ICorDebugValue::GetType, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type:
- apiref
ms.openlocfilehash: a3cd62384ad87d072cd715d23d0e9ee9dac23270
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396741"
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="60a1e-102">ICorDebugValue::GetType, méthode</span><span class="sxs-lookup"><span data-stu-id="60a1e-102">ICorDebugValue::GetType Method</span></span>
<span data-ttu-id="60a1e-103">Obtient le type primitif de cet objet « ICorDebugValue ».</span><span class="sxs-lookup"><span data-stu-id="60a1e-103">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60a1e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60a1e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60a1e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="60a1e-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="60a1e-106">à Pointeur vers une valeur de l’énumération "CorElementType" qui indique le type de la valeur.</span><span class="sxs-lookup"><span data-stu-id="60a1e-106">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60a1e-107">Notes</span><span class="sxs-lookup"><span data-stu-id="60a1e-107">Remarks</span></span>  
 <span data-ttu-id="60a1e-108">Si l’objet est un type au moment de l’exécution complexe, ce type peut être examiné par le biais des sous-classes appropriées de l' `ICorDebugValue` interface.</span><span class="sxs-lookup"><span data-stu-id="60a1e-108">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="60a1e-109">Par exemple, « ICorDebugObjectValue », qui hérite de `ICorDebugValue` , représente un type complexe.</span><span class="sxs-lookup"><span data-stu-id="60a1e-109">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="60a1e-110">Les `GetType` méthodes et [ICorDebugObjectValue :: GetClass](icordebugobjectvalue-getclass-method.md) retournent toutes les informations relatives au type d’une valeur.</span><span class="sxs-lookup"><span data-stu-id="60a1e-110">The `GetType` and [ICorDebugObjectValue::GetClass](icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="60a1e-111">Elles sont remplacées par la méthode [ICorDebugValue2 :: GetExactType,](icordebugvalue2-getexacttype-method.md) qui prend en charge les génériques.</span><span class="sxs-lookup"><span data-stu-id="60a1e-111">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60a1e-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="60a1e-112">Requirements</span></span>  
 <span data-ttu-id="60a1e-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60a1e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60a1e-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60a1e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60a1e-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60a1e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60a1e-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60a1e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60a1e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60a1e-117">See also</span></span>
