---
title: ICorDebugArrayValue::GetDimensions, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetDimensions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetDimensions
helpviewer_keywords:
- ICorDebugArrayValue::GetDimensions method [.NET Framework debugging]
- GetDimensions method [.NET Framework debugging]
ms.assetid: 6c116592-134b-4ef2-a319-680e92d013aa
topic_type:
- apiref
ms.openlocfilehash: 35e043c56977bf644efe1dd9cee1409f50cc877f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179027"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a><span data-ttu-id="78d13-102">ICorDebugArrayValue::GetDimensions, méthode</span><span class="sxs-lookup"><span data-stu-id="78d13-102">ICorDebugArrayValue::GetDimensions Method</span></span>
<span data-ttu-id="78d13-103">Obtient le nombre d’éléments dans chaque dimension de ce tableau.</span><span class="sxs-lookup"><span data-stu-id="78d13-103">Gets the number of elements in each dimension of this array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78d13-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78d13-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78d13-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="78d13-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="78d13-106">[dans] Le nombre de dimensions de cet objet ICorDebugArrayValue.</span><span class="sxs-lookup"><span data-stu-id="78d13-106">[in] The number of dimensions of this ICorDebugArrayValue object.</span></span>  
  
 <span data-ttu-id="78d13-107">Cette valeur est également `dims` la taille de la gamme parce que `ICorDebugArrayValue` sa taille est égale au nombre de dimensions de l’objet.</span><span class="sxs-lookup"><span data-stu-id="78d13-107">This value is also the size of the `dims` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `dims`  
 <span data-ttu-id="78d13-108">[out] Un tableau d’intégrations, chacun spécifique le nombre `ICorDebugArrayValue` d’éléments dans une dimension dans cet objet.</span><span class="sxs-lookup"><span data-stu-id="78d13-108">[out] An array of integers, each of which specifies the number of elements in a dimension in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78d13-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="78d13-109">Requirements</span></span>  
 <span data-ttu-id="78d13-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78d13-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78d13-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78d13-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78d13-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78d13-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78d13-113">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78d13-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
