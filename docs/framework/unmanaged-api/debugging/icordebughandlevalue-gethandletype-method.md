---
title: ICorDebugHandleValue::GetHandleType, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue.GetHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::GetHandleType
helpviewer_keywords:
- GetHandleType method [.NET Framework debugging]
- ICorDebugHandleValue::GetHandleType method [.NET Framework debugging]
ms.assetid: d5e7b12d-835a-4e86-ae2f-d658d4f1c67c
topic_type:
- apiref
ms.openlocfilehash: 72ef9a0fe4cd08ce67594600375953c249243d4f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734151"
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="f152e-102">ICorDebugHandleValue::GetHandleType, méthode</span><span class="sxs-lookup"><span data-stu-id="f152e-102">ICorDebugHandleValue::GetHandleType Method</span></span>

<span data-ttu-id="f152e-103">Obtient une valeur qui indique le genre de handle référencé par cet objet ICorDebugHandleValue.</span><span class="sxs-lookup"><span data-stu-id="f152e-103">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f152e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f152e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f152e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f152e-105">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="f152e-106">à Pointeur vers une valeur de l’énumération CorDebugHandleType, qui indique le type de ce handle.</span><span class="sxs-lookup"><span data-stu-id="f152e-106">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f152e-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f152e-107">Requirements</span></span>  

 <span data-ttu-id="f152e-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f152e-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f152e-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f152e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f152e-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f152e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f152e-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f152e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
