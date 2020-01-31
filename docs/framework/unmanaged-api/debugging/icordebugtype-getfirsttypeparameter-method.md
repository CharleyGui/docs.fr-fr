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
ms.openlocfilehash: 1a02190b595fb01bdc2df46182bfa64bfe638db4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791286"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a><span data-ttu-id="d13f6-102">ICorDebugType::GetFirstTypeParameter, méthode</span><span class="sxs-lookup"><span data-stu-id="d13f6-102">ICorDebugType::GetFirstTypeParameter Method</span></span>
<span data-ttu-id="d13f6-103">Obtient un pointeur d’interface vers un ICorDebugType qui représente le premier paramètre <xref:System.Type> du type représenté par cet `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="d13f6-103">Gets an interface pointer to an ICorDebugType that represents the first <xref:System.Type> parameter of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d13f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d13f6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d13f6-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="d13f6-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="d13f6-106">à Pointeur vers l’adresse d’un objet `ICorDebugType` qui représente le premier paramètre.</span><span class="sxs-lookup"><span data-stu-id="d13f6-106">[out] A pointer to the address of an `ICorDebugType` object that represents the first parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d13f6-107">Notes</span><span class="sxs-lookup"><span data-stu-id="d13f6-107">Remarks</span></span>  
 <span data-ttu-id="d13f6-108">`GetFirstTypeParameter` peut être appelé dans les cas où les informations supplémentaires sur le type impliquent, au plus, un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="d13f6-108">`GetFirstTypeParameter` can be called in cases where the additional information about the type involves, at most, one type parameter.</span></span> <span data-ttu-id="d13f6-109">En particulier, il peut être utilisé si le type est un ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF ou ELEMENT_TYPE_PTR, comme indiqué par la méthode [ICorDebugType :: GetType](icordebugtype-gettype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d13f6-109">In particular, it can be used if the type is an ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR, as indicated by the [ICorDebugType::GetType](icordebugtype-gettype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d13f6-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d13f6-110">Requirements</span></span>  
 <span data-ttu-id="d13f6-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d13f6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d13f6-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d13f6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d13f6-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d13f6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d13f6-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d13f6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
