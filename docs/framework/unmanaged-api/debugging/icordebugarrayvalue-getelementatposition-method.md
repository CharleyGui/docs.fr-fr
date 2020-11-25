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
ms.openlocfilehash: a6e5ecee9a89da98a73dfb20935c5ec594d5958f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732929"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="74a3e-102">ICorDebugArrayValue::GetElementAtPosition, méthode</span><span class="sxs-lookup"><span data-stu-id="74a3e-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>

<span data-ttu-id="74a3e-103">Obtient l’élément à la position donnée, en traitant le tableau comme un tableau unidimensionnel de base zéro.</span><span class="sxs-lookup"><span data-stu-id="74a3e-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74a3e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74a3e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74a3e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="74a3e-105">Parameters</span></span>  

 `nPosition`  
 <span data-ttu-id="74a3e-106">dans Position de l’élément à récupérer.</span><span class="sxs-lookup"><span data-stu-id="74a3e-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="74a3e-107">à Pointeur vers l’adresse d’un objet ICorDebugValue qui représente la valeur de l’élément.</span><span class="sxs-lookup"><span data-stu-id="74a3e-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74a3e-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="74a3e-108">Remarks</span></span>  

 <span data-ttu-id="74a3e-109">La disposition d’un tableau à plusieurs dimensions suit le style C++ de la disposition du tableau.</span><span class="sxs-lookup"><span data-stu-id="74a3e-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74a3e-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="74a3e-110">Requirements</span></span>  

 <span data-ttu-id="74a3e-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74a3e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74a3e-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74a3e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74a3e-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74a3e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74a3e-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74a3e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
