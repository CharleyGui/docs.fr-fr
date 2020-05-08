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
ms.openlocfilehash: fa2be894af6e44d09c25a736f45acba56052f9fa
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895039"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a><span data-ttu-id="72674-102">ICorDebugArrayValue::GetDimensions, méthode</span><span class="sxs-lookup"><span data-stu-id="72674-102">ICorDebugArrayValue::GetDimensions Method</span></span>
<span data-ttu-id="72674-103">Obtient le nombre d’éléments dans chaque dimension de ce tableau.</span><span class="sxs-lookup"><span data-stu-id="72674-103">Gets the number of elements in each dimension of this array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72674-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72674-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72674-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="72674-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="72674-106">dans Nombre de dimensions de cet objet ICorDebugArrayValue.</span><span class="sxs-lookup"><span data-stu-id="72674-106">[in] The number of dimensions of this ICorDebugArrayValue object.</span></span>  
  
 <span data-ttu-id="72674-107">Cette valeur est également la taille du `dims` tableau, car sa taille est égale au nombre de dimensions de l' `ICorDebugArrayValue` objet.</span><span class="sxs-lookup"><span data-stu-id="72674-107">This value is also the size of the `dims` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `dims`  
 <span data-ttu-id="72674-108">à Tableau d’entiers, chacun spécifiant le nombre d’éléments d’une dimension dans cet `ICorDebugArrayValue` objet.</span><span class="sxs-lookup"><span data-stu-id="72674-108">[out] An array of integers, each of which specifies the number of elements in a dimension in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72674-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="72674-109">Requirements</span></span>  
 <span data-ttu-id="72674-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72674-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72674-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72674-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72674-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72674-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72674-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72674-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
