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
ms.openlocfilehash: 10584442d7e0bd61e6decaf2b494dfe39f339d6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088417"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="dbba7-102">ICorDebugArrayValue::GetElementAtPosition, méthode</span><span class="sxs-lookup"><span data-stu-id="dbba7-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>
<span data-ttu-id="dbba7-103">Obtient l’élément à la position donnée, en traitant le tableau comme un tableau unidimensionnel de base zéro.</span><span class="sxs-lookup"><span data-stu-id="dbba7-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbba7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbba7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbba7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dbba7-105">Parameters</span></span>  
 `nPosition`  
 <span data-ttu-id="dbba7-106">dans Position de l’élément à récupérer.</span><span class="sxs-lookup"><span data-stu-id="dbba7-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="dbba7-107">à Pointeur vers l’adresse d’un objet ICorDebugValue qui représente la valeur de l’élément.</span><span class="sxs-lookup"><span data-stu-id="dbba7-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbba7-108">Notes</span><span class="sxs-lookup"><span data-stu-id="dbba7-108">Remarks</span></span>  
 <span data-ttu-id="dbba7-109">La disposition d’un tableau à plusieurs dimensions suit le C++ style de disposition du tableau.</span><span class="sxs-lookup"><span data-stu-id="dbba7-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbba7-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="dbba7-110">Requirements</span></span>  
 <span data-ttu-id="dbba7-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbba7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbba7-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dbba7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dbba7-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbba7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbba7-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbba7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
