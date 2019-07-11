---
title: ICorDebugObjectValue::IsValueClass, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.IsValueClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::IsValueClass
helpviewer_keywords:
- ICorDebugObjectValue::IsValueClass method [.NET Framework debugging]
- IsValueClass method [.NET Framework debugging]
ms.assetid: 13d89a4a-5d9d-4a79-9600-5e2a98c3d166
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b08937182797c8e94048d734d65473fad21b85cc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766300"
---
# <a name="icordebugobjectvalueisvalueclass-method"></a><span data-ttu-id="4ec6f-102">ICorDebugObjectValue::IsValueClass, méthode</span><span class="sxs-lookup"><span data-stu-id="4ec6f-102">ICorDebugObjectValue::IsValueClass Method</span></span>
<span data-ttu-id="4ec6f-103">Obtient une valeur qui indique si cette valeur de l’objet est un type valeur.</span><span class="sxs-lookup"><span data-stu-id="4ec6f-103">Gets a value that indicates whether this object value is a value type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ec6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ec6f-104">Syntax</span></span>  
  
```cpp  
HRESULT IsValueClass (  
    [out] BOOL               *pbIsValueClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ec6f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4ec6f-105">Parameters</span></span>  
 `pbIsValueClass`  
 <span data-ttu-id="4ec6f-106">[out] Un pointeur vers une valeur booléenne qui est `true` si la valeur de l’objet, représentée par « ICorDebugObjectValue », est un type de valeur plutôt qu’un type référence ; sinon, `pbIsValueClass` est `false`.</span><span class="sxs-lookup"><span data-stu-id="4ec6f-106">[out] A pointer to a Boolean value that is `true` if the object value, represented by this "ICorDebugObjectValue", is a value type rather than a reference type; otherwise, `pbIsValueClass` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ec6f-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4ec6f-107">Requirements</span></span>  
 <span data-ttu-id="4ec6f-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ec6f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ec6f-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4ec6f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ec6f-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ec6f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ec6f-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ec6f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ec6f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ec6f-112">See also</span></span>
