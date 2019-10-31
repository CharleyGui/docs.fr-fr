---
title: ICorDebugGenericValue::SetValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::SetValue
helpviewer_keywords:
- ICorDebugGenericValue::SetValue method [.NET Framework debugging]
- SetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: ed4c6458-0435-44fc-8e78-8ba00be362f2
topic_type:
- apiref
ms.openlocfilehash: 4cd03895b4e33c3e42c71acca12eaf950fc9a145
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138560"
---
# <a name="icordebuggenericvaluesetvalue-method"></a><span data-ttu-id="d1eed-102">ICorDebugGenericValue::SetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="d1eed-102">ICorDebugGenericValue::SetValue Method</span></span>
<span data-ttu-id="d1eed-103">Copie une nouvelle valeur à partir de la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d1eed-103">Copies a new value from the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1eed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1eed-104">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1eed-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d1eed-105">Parameters</span></span>  
 `pFrom`  
 <span data-ttu-id="d1eed-106">dans Pointeur vers la mémoire tampon à partir de laquelle la valeur doit être copiée.</span><span class="sxs-lookup"><span data-stu-id="d1eed-106">[in] A pointer to the buffer from which to copy the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1eed-107">Notes</span><span class="sxs-lookup"><span data-stu-id="d1eed-107">Remarks</span></span>  
 <span data-ttu-id="d1eed-108">Pour les types de référence, la valeur est la référence, et non le contenu.</span><span class="sxs-lookup"><span data-stu-id="d1eed-108">For reference types, the value is the reference, not the content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1eed-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="d1eed-109">Requirements</span></span>  
 <span data-ttu-id="d1eed-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1eed-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1eed-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1eed-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1eed-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1eed-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1eed-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1eed-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
