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
ms.openlocfilehash: 0bffd2db0a4a061a8629ff50a03a319feec6d836
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396550"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="e25f1-102">ICorDebugVariableHome :: GetSlotIndex, méthode</span><span class="sxs-lookup"><span data-stu-id="e25f1-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="e25f1-103">Obtient l’index d’emplacement managé d’une variable locale.</span><span class="sxs-lookup"><span data-stu-id="e25f1-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e25f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e25f1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e25f1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e25f1-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="e25f1-106">à Pointeur vers l’index d’emplacement d’une variable locale.</span><span class="sxs-lookup"><span data-stu-id="e25f1-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e25f1-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e25f1-107">Return Value</span></span>  
 <span data-ttu-id="e25f1-108">La méthode retourne les valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="e25f1-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="e25f1-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="e25f1-109">Value</span></span>|<span data-ttu-id="e25f1-110">Description</span><span class="sxs-lookup"><span data-stu-id="e25f1-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="e25f1-111">L’appel de méthode a retourné une valeur d’index d’emplacement dans `pSlotIndex` .</span><span class="sxs-lookup"><span data-stu-id="e25f1-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="e25f1-112">L’instance [ICorDebugVariableHome](icordebugvariablehome-interface.md) actuelle représente un argument de fonction.</span><span class="sxs-lookup"><span data-stu-id="e25f1-112">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e25f1-113">Notes</span><span class="sxs-lookup"><span data-stu-id="e25f1-113">Remarks</span></span>  
 <span data-ttu-id="e25f1-114">L’index d’emplacement peut être utilisé pour récupérer les métadonnées de cette variable locale.</span><span class="sxs-lookup"><span data-stu-id="e25f1-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e25f1-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e25f1-115">Requirements</span></span>  
 <span data-ttu-id="e25f1-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e25f1-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e25f1-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e25f1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e25f1-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e25f1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e25f1-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e25f1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e25f1-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e25f1-120">See also</span></span>

- [<span data-ttu-id="e25f1-121">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="e25f1-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
