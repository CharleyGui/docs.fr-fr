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
ms.openlocfilehash: 7b637889986425767fd7e1166c73df3301075422
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695281"
---
# <a name="icordebugobjectvalueisvalueclass-method"></a><span data-ttu-id="ca626-102">ICorDebugObjectValue::IsValueClass, méthode</span><span class="sxs-lookup"><span data-stu-id="ca626-102">ICorDebugObjectValue::IsValueClass Method</span></span>

<span data-ttu-id="ca626-103">Obtient une valeur qui indique si la valeur de cet objet est un type valeur.</span><span class="sxs-lookup"><span data-stu-id="ca626-103">Gets a value that indicates whether this object value is a value type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca626-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca626-104">Syntax</span></span>  
  
```cpp  
HRESULT IsValueClass (  
    [out] BOOL               *pbIsValueClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca626-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ca626-105">Parameters</span></span>  

 `pbIsValueClass`  
 <span data-ttu-id="ca626-106">à Pointeur vers une valeur booléenne qui est `true` si la valeur de l’objet, représentée par « ICorDebugObjectValue », est un type valeur plutôt qu’un type référence ; sinon, `pbIsValueClass` est `false` .</span><span class="sxs-lookup"><span data-stu-id="ca626-106">[out] A pointer to a Boolean value that is `true` if the object value, represented by this "ICorDebugObjectValue", is a value type rather than a reference type; otherwise, `pbIsValueClass` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca626-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ca626-107">Requirements</span></span>  

 <span data-ttu-id="ca626-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca626-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca626-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca626-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca626-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca626-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca626-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca626-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca626-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca626-112">See also</span></span>
