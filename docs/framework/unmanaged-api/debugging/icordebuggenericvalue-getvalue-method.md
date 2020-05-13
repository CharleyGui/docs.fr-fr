---
title: ICorDebugGenericValue::GetValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::GetValue
helpviewer_keywords:
- ICorDebugGenericValue::GetValue method [.NET Framework debugging]
- GetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: 4e95d7cb-144d-4ccf-8a69-d605f4744be2
topic_type:
- apiref
ms.openlocfilehash: 646b2661148e38f3c918fc18fce5c9cd0b1134a1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213021"
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="3e44f-102">ICorDebugGenericValue::GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="3e44f-102">ICorDebugGenericValue::GetValue Method</span></span>
<span data-ttu-id="3e44f-103">Copie la valeur de ce générique dans la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="3e44f-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e44f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e44f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e44f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3e44f-105">Parameters</span></span>  
 `pTo`  
 <span data-ttu-id="3e44f-106">à Pointeur vers la valeur représentée par cet objet ICorDebugGenericValue.</span><span class="sxs-lookup"><span data-stu-id="3e44f-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="3e44f-107">La valeur peut être un type simple ou un type référence (autrement dit, un pointeur).</span><span class="sxs-lookup"><span data-stu-id="3e44f-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e44f-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3e44f-108">Requirements</span></span>  
 <span data-ttu-id="3e44f-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e44f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e44f-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e44f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e44f-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e44f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e44f-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e44f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
