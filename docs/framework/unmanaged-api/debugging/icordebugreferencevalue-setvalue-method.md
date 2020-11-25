---
title: ICorDebugReferenceValue::SetValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::SetValue
helpviewer_keywords:
- SetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::SetValue method [.NET Framework debugging]
ms.assetid: 3d3f6eec-d772-401f-a028-1a2ecdc31e95
topic_type:
- apiref
ms.openlocfilehash: 3fdd3180a01e4609ac40fd358879c0d2569234ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728379"
---
# <a name="icordebugreferencevaluesetvalue-method"></a><span data-ttu-id="bf257-102">ICorDebugReferenceValue::SetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="bf257-102">ICorDebugReferenceValue::SetValue Method</span></span>

<span data-ttu-id="bf257-103">Définit l’adresse mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bf257-103">Sets the specified memory address.</span></span> <span data-ttu-id="bf257-104">Autrement dit, cette méthode définit ce ICorDebugReferenceValue pour pointer vers un objet.</span><span class="sxs-lookup"><span data-stu-id="bf257-104">That is, this method sets this ICorDebugReferenceValue to point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf257-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf257-105">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf257-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bf257-106">Parameters</span></span>  

 `value`  
 <span data-ttu-id="bf257-107">dans `CORDB_ADDRESS` Valeur qui spécifie l’adresse de l’objet vers lequel ce `ICorDebugReferenceValue` pointe.</span><span class="sxs-lookup"><span data-stu-id="bf257-107">[in] A `CORDB_ADDRESS` value that specifies the address of the object to which this `ICorDebugReferenceValue` points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf257-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bf257-108">Requirements</span></span>  

 <span data-ttu-id="bf257-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf257-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf257-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf257-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf257-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf257-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf257-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf257-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
