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
ms.openlocfilehash: b0e8fd162ccc1cfc944fb870f493febfe2e5ef42
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207683"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="385af-102">ICorDebugObjectValue::GetClass, méthode</span><span class="sxs-lookup"><span data-stu-id="385af-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="385af-103">Obtient la classe de cette valeur d’objet.</span><span class="sxs-lookup"><span data-stu-id="385af-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="385af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="385af-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="385af-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="385af-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="385af-106">à Pointeur vers l’adresse d’un objet « ICorDebugClass » qui représente la classe de la valeur de l’objet représentée par cet objet « ICorDebugObjectValue ».</span><span class="sxs-lookup"><span data-stu-id="385af-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="385af-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="385af-107">Remarks</span></span>  
 <span data-ttu-id="385af-108">Les `GetClass` méthodes et [ICorDebugValue :: GetType](icordebugvalue-gettype-method.md) retournent toutes les informations sur le type d’une valeur ; elles sont toutes deux remplacées par le [ICorDebugValue2 :: GetExactType,](icordebugvalue2-getexacttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="385af-108">The `GetClass` and [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="385af-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="385af-109">Requirements</span></span>  
 <span data-ttu-id="385af-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="385af-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="385af-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="385af-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="385af-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="385af-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="385af-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="385af-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="385af-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="385af-114">See also</span></span>
