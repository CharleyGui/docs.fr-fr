---
title: ICorDebugArrayValue::GetCount, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetCount
helpviewer_keywords:
- ICorDebugArrayValue::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 44cd98cf-2127-4d46-8c6a-da4e857bb6b0
topic_type:
- apiref
ms.openlocfilehash: 82f282630a2e31b8c67d43fa0f0b30431a0d6ee4
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895058"
---
# <a name="icordebugarrayvaluegetcount-method"></a><span data-ttu-id="a4b43-102">ICorDebugArrayValue::GetCount, méthode</span><span class="sxs-lookup"><span data-stu-id="a4b43-102">ICorDebugArrayValue::GetCount Method</span></span>
<span data-ttu-id="a4b43-103">Obtient le nombre total d’éléments dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="a4b43-103">Gets the total number of elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4b43-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4b43-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG32 *pnCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4b43-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a4b43-105">Parameters</span></span>  
 `pnCount`  
 <span data-ttu-id="a4b43-106">à Pointeur vers le nombre total d’éléments dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="a4b43-106">[out] A pointer to the total number of elements in the array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4b43-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a4b43-107">Requirements</span></span>  
 <span data-ttu-id="a4b43-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4b43-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4b43-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a4b43-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4b43-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4b43-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4b43-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4b43-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
