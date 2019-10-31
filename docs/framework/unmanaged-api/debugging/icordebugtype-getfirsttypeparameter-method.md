---
title: ICorDebugType::GetFirstTypeParameter, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetFirstTypeParameter
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type:
- apiref
ms.openlocfilehash: 4dbc042143e68dc962eb21b2bf741cbaefc1977e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122357"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a><span data-ttu-id="e503f-102">ICorDebugType::GetFirstTypeParameter, méthode</span><span class="sxs-lookup"><span data-stu-id="e503f-102">ICorDebugType::GetFirstTypeParameter Method</span></span>
<span data-ttu-id="e503f-103">Obtient un pointeur d’interface vers un ICorDebugType qui représente le premier paramètre <xref:System.Type> du type représenté par cet `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="e503f-103">Gets an interface pointer to an ICorDebugType that represents the first <xref:System.Type> parameter of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e503f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e503f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e503f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e503f-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="e503f-106">à Pointeur vers l’adresse d’un objet `ICorDebugType` qui représente le premier paramètre.</span><span class="sxs-lookup"><span data-stu-id="e503f-106">[out] A pointer to the address of an `ICorDebugType` object that represents the first parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e503f-107">Notes</span><span class="sxs-lookup"><span data-stu-id="e503f-107">Remarks</span></span>  
 <span data-ttu-id="e503f-108">`GetFirstTypeParameter` peut être appelé dans les cas où les informations supplémentaires sur le type impliquent, au plus, un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="e503f-108">`GetFirstTypeParameter` can be called in cases where the additional information about the type involves, at most, one type parameter.</span></span> <span data-ttu-id="e503f-109">En particulier, il peut être utilisé si le type est ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF ou ELEMENT_TYPE_PTR, comme indiqué par la méthode [ICorDebugType :: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e503f-109">In particular, it can be used if the type is an ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e503f-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="e503f-110">Requirements</span></span>  
 <span data-ttu-id="e503f-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e503f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e503f-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e503f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e503f-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e503f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e503f-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e503f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
