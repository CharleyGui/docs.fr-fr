---
title: ICorDebugArrayValue::GetBaseIndicies, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetBaseIndicies
helpviewer_keywords:
- ICorDebugArrayValue::GetBaseIndicies method [.NET Framework debugging]
- GetBaseIndicies method [.NET Framework debugging]
ms.assetid: 868b339b-acdb-4fe0-91c7-b85f4fba99eb
topic_type:
- apiref
ms.openlocfilehash: 7c6d1905cdbd12b960014e687034ea9d163b68d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179040"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="5233c-102">ICorDebugArrayValue::GetBaseIndicies, méthode</span><span class="sxs-lookup"><span data-stu-id="5233c-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>
<span data-ttu-id="5233c-103">Obtient l’index de base de chaque dimension dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="5233c-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5233c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5233c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5233c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5233c-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="5233c-106">[dans] Le nombre de `ICorDebugArrayValue` dimensions de cet objet.</span><span class="sxs-lookup"><span data-stu-id="5233c-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="5233c-107">Cette valeur est également `indicies` la taille de la gamme parce que `ICorDebugArrayValue` sa taille est égale au nombre de dimensions de l’objet.</span><span class="sxs-lookup"><span data-stu-id="5233c-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="5233c-108">[out] Un tableau d’intégrants, dont chacun est l’indice de base (c’est-à-dire l’indice de départ) d’une dimension de cet `ICorDebugArrayValue` objet.</span><span class="sxs-lookup"><span data-stu-id="5233c-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5233c-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5233c-109">Requirements</span></span>  
 <span data-ttu-id="5233c-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5233c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5233c-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5233c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5233c-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5233c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5233c-113">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5233c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
