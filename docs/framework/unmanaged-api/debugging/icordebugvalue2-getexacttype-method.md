---
title: ICorDebugValue2::GetExactType, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugValue2.GetExactType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type:
- apiref
ms.openlocfilehash: 6c5e5d1c9f734e097fc9e871d7a0cffdc9bb9138
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791124"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="10545-102">ICorDebugValue2::GetExactType, méthode</span><span class="sxs-lookup"><span data-stu-id="10545-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="10545-103">Obtient un pointeur d’interface vers un objet « ICorDebugType » qui représente le <xref:System.Type> de cette valeur.</span><span class="sxs-lookup"><span data-stu-id="10545-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10545-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10545-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10545-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="10545-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="10545-106">à Pointeur vers l’adresse d’un objet `ICorDebugType` qui représente le <xref:System.Type> de la valeur représentée par cet objet « ICorDebugValue2 ».</span><span class="sxs-lookup"><span data-stu-id="10545-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10545-107">Notes</span><span class="sxs-lookup"><span data-stu-id="10545-107">Remarks</span></span>  
 <span data-ttu-id="10545-108">La méthode `GetExactType` qui prend en charge les génériques remplace les méthodes [ICorDebugObjectValue :: GetClass](icordebugobjectvalue-getclass-method.md) et [ICorDebugValue :: GetType](icordebugvalue-gettype-method.md) , chacune d’elles retournant des informations sur le type d’une valeur.</span><span class="sxs-lookup"><span data-stu-id="10545-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10545-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="10545-109">Requirements</span></span>  
 <span data-ttu-id="10545-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10545-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10545-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10545-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10545-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10545-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10545-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10545-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10545-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10545-114">See also</span></span>
