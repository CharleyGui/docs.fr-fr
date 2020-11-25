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
ms.openlocfilehash: 0b6b6f46c7fff8f1d4c2ad555c93423f9ca8ac09
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698141"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="991d1-102">ICorDebugArrayValue::GetElement, méthode</span><span class="sxs-lookup"><span data-stu-id="991d1-102">ICorDebugArrayValue::GetElement Method</span></span>

<span data-ttu-id="991d1-103">Obtient la valeur de l’élément de tableau donné.</span><span class="sxs-lookup"><span data-stu-id="991d1-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="991d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="991d1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="991d1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="991d1-105">Parameters</span></span>  

 `cdim`  
 <span data-ttu-id="991d1-106">dans Nombre de dimensions de cet `ICorDebugArrayValue` objet.</span><span class="sxs-lookup"><span data-stu-id="991d1-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="991d1-107">Cette valeur est également la taille du `indices` tableau, car sa taille est égale au nombre de dimensions de l' `ICorDebugArrayValue` objet.</span><span class="sxs-lookup"><span data-stu-id="991d1-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="991d1-108">dans Tableau de valeurs d’index, chacune spécifiant une position dans une dimension de l' `ICorDebugArrayValue` objet.</span><span class="sxs-lookup"><span data-stu-id="991d1-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="991d1-109">Cette valeur ne doit pas être Null.</span><span class="sxs-lookup"><span data-stu-id="991d1-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="991d1-110">à Pointeur vers l’adresse d’un objet ICorDebugValue qui représente la valeur de l’élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="991d1-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="991d1-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="991d1-111">Requirements</span></span>  

 <span data-ttu-id="991d1-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="991d1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="991d1-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="991d1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="991d1-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="991d1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="991d1-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="991d1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
