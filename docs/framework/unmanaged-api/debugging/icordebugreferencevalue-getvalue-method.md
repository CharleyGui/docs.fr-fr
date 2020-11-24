---
title: ICorDebugReferenceValue::GetValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::GetValue method [.NET Framework debugging]
ms.assetid: 5da07f99-6c70-46ec-b997-5ab6fb7106cd
topic_type:
- apiref
ms.openlocfilehash: cbdba623b02ccc85c6d4784a9539adf14fd256e7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691199"
---
# <a name="icordebugreferencevaluegetvalue-method"></a><span data-ttu-id="1bd2a-102">ICorDebugReferenceValue::GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="1bd2a-102">ICorDebugReferenceValue::GetValue Method</span></span>

<span data-ttu-id="1bd2a-103">Obtient l’adresse mémoire actuelle de l’objet référencé.</span><span class="sxs-lookup"><span data-stu-id="1bd2a-103">Gets the current memory address of the referenced object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bd2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bd2a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] CORDB_ADDRESS   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bd2a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1bd2a-105">Parameters</span></span>  

 `pValue`  
 <span data-ttu-id="1bd2a-106">à Pointeur vers une `CORDB_ADDRESS` valeur qui spécifie l’adresse de l’objet vers lequel cet objet ICorDebugReferenceValue pointe.</span><span class="sxs-lookup"><span data-stu-id="1bd2a-106">[out] A pointer to a `CORDB_ADDRESS` value that specifies the address of the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bd2a-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1bd2a-107">Requirements</span></span>  

 <span data-ttu-id="1bd2a-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bd2a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bd2a-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1bd2a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1bd2a-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bd2a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bd2a-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bd2a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
