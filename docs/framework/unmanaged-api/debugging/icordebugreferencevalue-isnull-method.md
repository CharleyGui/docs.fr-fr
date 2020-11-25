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
ms.openlocfilehash: bcd4c8ba4b81821ae7dd9deaf0f76a76d335aff8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728392"
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="2e61e-102">ICorDebugReferenceValue::IsNull, méthode</span><span class="sxs-lookup"><span data-stu-id="2e61e-102">ICorDebugReferenceValue::IsNull Method</span></span>

<span data-ttu-id="2e61e-103">Obtient une valeur qui indique si ce ICorDebugReferenceValue est une valeur null, auquel cas le `ICorDebugReferenceValue` ne pointe pas vers un objet.</span><span class="sxs-lookup"><span data-stu-id="2e61e-103">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e61e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e61e-104">Syntax</span></span>  
  
```cpp  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e61e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2e61e-105">Parameters</span></span>  

 `pbNull`  
 <span data-ttu-id="2e61e-106">à Pointeur vers une valeur booléenne qui est `true` si cet `ICorDebugReferenceValue` objet est NULL ; sinon, `pbNull` est `false` .</span><span class="sxs-lookup"><span data-stu-id="2e61e-106">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e61e-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2e61e-107">Requirements</span></span>  

 <span data-ttu-id="2e61e-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e61e-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e61e-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e61e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e61e-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e61e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e61e-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e61e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
