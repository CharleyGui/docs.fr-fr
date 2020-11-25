---
title: ICorDebugHeapValue::IsValid, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
ms.openlocfilehash: d9150d15ac183b65b87448424f265693ed7b7ab7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726572"
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="fa16d-102">ICorDebugHeapValue::IsValid, méthode</span><span class="sxs-lookup"><span data-stu-id="fa16d-102">ICorDebugHeapValue::IsValid Method</span></span>

<span data-ttu-id="fa16d-103">Obtient une valeur qui indique si l’objet représenté par cet ICorDebugHeapValue est valide.</span><span class="sxs-lookup"><span data-stu-id="fa16d-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="fa16d-104">Cette méthode est déconseillée dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fa16d-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa16d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa16d-105">Syntax</span></span>  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa16d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fa16d-106">Parameters</span></span>  

 `pbValid`  
 <span data-ttu-id="fa16d-107">à Pointeur vers une valeur booléenne qui indique si cette valeur sur le tas est valide.</span><span class="sxs-lookup"><span data-stu-id="fa16d-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa16d-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="fa16d-108">Remarks</span></span>  

 <span data-ttu-id="fa16d-109">La valeur n’est pas valide si elle a été récupérée par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="fa16d-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="fa16d-110">Cette méthode est dépréciée.</span><span class="sxs-lookup"><span data-stu-id="fa16d-110">This method has been deprecated.</span></span> <span data-ttu-id="fa16d-111">Dans la .NET Framework 2,0, toutes les valeurs sont valides jusqu’à ce que [ICorDebugController :: continue](icordebugcontroller-continue-method.md) soit appelé, auquel les valeurs sont invalidées.</span><span class="sxs-lookup"><span data-stu-id="fa16d-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa16d-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fa16d-112">Requirements</span></span>  

 <span data-ttu-id="fa16d-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa16d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa16d-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa16d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa16d-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa16d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa16d-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa16d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
