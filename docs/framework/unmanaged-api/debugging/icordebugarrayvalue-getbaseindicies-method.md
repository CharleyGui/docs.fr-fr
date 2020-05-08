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
ms.openlocfilehash: 9aadbe7c6f18c6b15350267d1f9ecaa3a23cdd20
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895069"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="45dec-102">ICorDebugArrayValue::GetBaseIndicies, méthode</span><span class="sxs-lookup"><span data-stu-id="45dec-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>
<span data-ttu-id="45dec-103">Obtient l’index de base de chaque dimension du tableau.</span><span class="sxs-lookup"><span data-stu-id="45dec-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45dec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45dec-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45dec-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="45dec-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="45dec-106">dans Nombre de dimensions de cet `ICorDebugArrayValue` objet.</span><span class="sxs-lookup"><span data-stu-id="45dec-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="45dec-107">Cette valeur est également la taille du `indicies` tableau, car sa taille est égale au nombre de dimensions de l' `ICorDebugArrayValue` objet.</span><span class="sxs-lookup"><span data-stu-id="45dec-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="45dec-108">à Tableau d’entiers, chacun d’eux étant l’index de base (autrement dit, l’index de départ) d’une dimension de `ICorDebugArrayValue` cet objet.</span><span class="sxs-lookup"><span data-stu-id="45dec-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45dec-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="45dec-109">Requirements</span></span>  
 <span data-ttu-id="45dec-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45dec-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45dec-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45dec-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45dec-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45dec-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45dec-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45dec-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
