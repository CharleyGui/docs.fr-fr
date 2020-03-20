---
title: ICorDebugArrayValue::GetElement, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
ms.openlocfilehash: adcb7b5a27f3b8c63dbbb660a23b5c891f84ac46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179006"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="912ae-102">ICorDebugArrayValue::GetElement, méthode</span><span class="sxs-lookup"><span data-stu-id="912ae-102">ICorDebugArrayValue::GetElement Method</span></span>
<span data-ttu-id="912ae-103">Obtient la valeur de l’élément de tableau donné.</span><span class="sxs-lookup"><span data-stu-id="912ae-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="912ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="912ae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="912ae-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="912ae-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="912ae-106">[dans] Le nombre de `ICorDebugArrayValue` dimensions de cet objet.</span><span class="sxs-lookup"><span data-stu-id="912ae-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="912ae-107">Cette valeur est également `indices` la taille de la gamme parce que `ICorDebugArrayValue` sa taille est égale au nombre de dimensions de l’objet.</span><span class="sxs-lookup"><span data-stu-id="912ae-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="912ae-108">[dans] Un éventail de valeurs indicielles, chacune spécifie une position dans une dimension de l’objet. `ICorDebugArrayValue`</span><span class="sxs-lookup"><span data-stu-id="912ae-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="912ae-109">Cette valeur ne doit pas être nulle.</span><span class="sxs-lookup"><span data-stu-id="912ae-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="912ae-110">[out] Un pointeur à l’adresse d’un objet ICorDebugValue qui représente la valeur de l’élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="912ae-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="912ae-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="912ae-111">Requirements</span></span>  
 <span data-ttu-id="912ae-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="912ae-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="912ae-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="912ae-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="912ae-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="912ae-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="912ae-115">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="912ae-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
