---
title: 'ICorDebugVariableHome :: GetSlotIndex, méthode'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
ms.openlocfilehash: 542bfa05c55ef224d1b9111f9af6c069e9e23542
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790969"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="4fae6-102">ICorDebugVariableHome :: GetSlotIndex, méthode</span><span class="sxs-lookup"><span data-stu-id="4fae6-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="4fae6-103">Obtient l’index d’emplacement managé d’une variable locale.</span><span class="sxs-lookup"><span data-stu-id="4fae6-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fae6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fae6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fae6-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="4fae6-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="4fae6-106">à Pointeur vers l’index d’emplacement d’une variable locale.</span><span class="sxs-lookup"><span data-stu-id="4fae6-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4fae6-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4fae6-107">Return Value</span></span>  
 <span data-ttu-id="4fae6-108">La méthode retourne les valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="4fae6-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="4fae6-109">Value</span><span class="sxs-lookup"><span data-stu-id="4fae6-109">Value</span></span>|<span data-ttu-id="4fae6-110">Description</span><span class="sxs-lookup"><span data-stu-id="4fae6-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="4fae6-111">L’appel de méthode a retourné une valeur d’index d’emplacement dans `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="4fae6-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="4fae6-112">L’instance [ICorDebugVariableHome](icordebugvariablehome-interface.md) actuelle représente un argument de fonction.</span><span class="sxs-lookup"><span data-stu-id="4fae6-112">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fae6-113">Notes</span><span class="sxs-lookup"><span data-stu-id="4fae6-113">Remarks</span></span>  
 <span data-ttu-id="4fae6-114">L’index d’emplacement peut être utilisé pour récupérer les métadonnées de cette variable locale.</span><span class="sxs-lookup"><span data-stu-id="4fae6-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fae6-115">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="4fae6-115">Requirements</span></span>  
 <span data-ttu-id="4fae6-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fae6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fae6-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4fae6-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4fae6-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fae6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fae6-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fae6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fae6-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fae6-120">See also</span></span>

- [<span data-ttu-id="4fae6-121">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="4fae6-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
