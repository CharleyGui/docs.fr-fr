---
title: ICorDebugReferenceValue::IsNull, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.IsNull
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type:
- apiref
ms.openlocfilehash: e8b778c0880040f5ffd639a445fd5663ce493219
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379083"
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="3dfb7-102">ICorDebugReferenceValue::IsNull, méthode</span><span class="sxs-lookup"><span data-stu-id="3dfb7-102">ICorDebugReferenceValue::IsNull Method</span></span>
<span data-ttu-id="3dfb7-103">Obtient une valeur qui indique si ce ICorDebugReferenceValue est une valeur null, auquel cas le `ICorDebugReferenceValue` ne pointe pas vers un objet.</span><span class="sxs-lookup"><span data-stu-id="3dfb7-103">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dfb7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3dfb7-104">Syntax</span></span>  
  
```cpp  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dfb7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3dfb7-105">Parameters</span></span>  
 `pbNull`  
 <span data-ttu-id="3dfb7-106">à Pointeur vers une valeur booléenne qui est `true` si cet `ICorDebugReferenceValue` objet est NULL ; sinon, `pbNull` est `false` .</span><span class="sxs-lookup"><span data-stu-id="3dfb7-106">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dfb7-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3dfb7-107">Requirements</span></span>  
 <span data-ttu-id="3dfb7-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dfb7-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dfb7-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3dfb7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3dfb7-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3dfb7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dfb7-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dfb7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
