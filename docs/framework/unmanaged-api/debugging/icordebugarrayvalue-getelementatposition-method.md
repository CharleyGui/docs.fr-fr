---
title: ICorDebugArrayValue::GetElementAtPosition, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementAtPosition
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementAtPosition
helpviewer_keywords:
- GetElementAtPosition method [.NET Framework debugging]
- ICorDebugArrayValue::GetElementAtPosition method [.NET Framework debugging]
ms.assetid: 6fd5eaa4-1997-4910-82f5-3887480db764
topic_type:
- apiref
ms.openlocfilehash: 5644c20ec5df2606c7258131573691997f424e50
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895014"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="35862-102">ICorDebugArrayValue::GetElementAtPosition, méthode</span><span class="sxs-lookup"><span data-stu-id="35862-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>
<span data-ttu-id="35862-103">Obtient l’élément à la position donnée, en traitant le tableau comme un tableau unidimensionnel de base zéro.</span><span class="sxs-lookup"><span data-stu-id="35862-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35862-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35862-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35862-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="35862-105">Parameters</span></span>  
 `nPosition`  
 <span data-ttu-id="35862-106">dans Position de l’élément à récupérer.</span><span class="sxs-lookup"><span data-stu-id="35862-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="35862-107">à Pointeur vers l’adresse d’un objet ICorDebugValue qui représente la valeur de l’élément.</span><span class="sxs-lookup"><span data-stu-id="35862-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35862-108">Notes </span><span class="sxs-lookup"><span data-stu-id="35862-108">Remarks</span></span>  
 <span data-ttu-id="35862-109">La disposition d’un tableau à plusieurs dimensions suit le style C++ de la disposition du tableau.</span><span class="sxs-lookup"><span data-stu-id="35862-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35862-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="35862-110">Requirements</span></span>  
 <span data-ttu-id="35862-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35862-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35862-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35862-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35862-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35862-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35862-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35862-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
