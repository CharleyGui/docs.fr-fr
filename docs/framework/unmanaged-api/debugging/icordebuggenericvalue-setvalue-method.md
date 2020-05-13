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
ms.openlocfilehash: 972a981188c36236b81f3da17c09abeeb1e32857
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212189"
---
# <a name="icordebuggenericvaluesetvalue-method"></a><span data-ttu-id="18de2-102">ICorDebugGenericValue::SetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="18de2-102">ICorDebugGenericValue::SetValue Method</span></span>
<span data-ttu-id="18de2-103">Copie une nouvelle valeur à partir de la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="18de2-103">Copies a new value from the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18de2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18de2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18de2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="18de2-105">Parameters</span></span>  
 `pFrom`  
 <span data-ttu-id="18de2-106">dans Pointeur vers la mémoire tampon à partir de laquelle la valeur doit être copiée.</span><span class="sxs-lookup"><span data-stu-id="18de2-106">[in] A pointer to the buffer from which to copy the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18de2-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="18de2-107">Remarks</span></span>  
 <span data-ttu-id="18de2-108">Pour les types de référence, la valeur est la référence, et non le contenu.</span><span class="sxs-lookup"><span data-stu-id="18de2-108">For reference types, the value is the reference, not the content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18de2-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="18de2-109">Requirements</span></span>  
 <span data-ttu-id="18de2-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18de2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18de2-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18de2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18de2-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18de2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18de2-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18de2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
