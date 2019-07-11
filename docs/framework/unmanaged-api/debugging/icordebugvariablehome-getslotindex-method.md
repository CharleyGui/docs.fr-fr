---
title: ICorDebugVariableHome::GetSlotIndex (méthode)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 199c3ba5d5b9588db4c665070b4dec6266cefc2e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760344"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="26e10-102">ICorDebugVariableHome::GetSlotIndex (méthode)</span><span class="sxs-lookup"><span data-stu-id="26e10-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="26e10-103">Obtient l’index emplacement managé d’une variable locale.</span><span class="sxs-lookup"><span data-stu-id="26e10-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26e10-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26e10-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26e10-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="26e10-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="26e10-106">[out] Pointeur vers l’index d’emplacement d’une variable locale.</span><span class="sxs-lookup"><span data-stu-id="26e10-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26e10-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="26e10-107">Return Value</span></span>  
 <span data-ttu-id="26e10-108">La méthode retourne les valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="26e10-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="26e10-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="26e10-109">Value</span></span>|<span data-ttu-id="26e10-110">Description</span><span class="sxs-lookup"><span data-stu-id="26e10-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="26e10-111">L’appel de méthode a retourné une valeur d’index de l’emplacement dans `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="26e10-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="26e10-112">Actuel [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance représente un argument de fonction.</span><span class="sxs-lookup"><span data-stu-id="26e10-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26e10-113">Notes</span><span class="sxs-lookup"><span data-stu-id="26e10-113">Remarks</span></span>  
 <span data-ttu-id="26e10-114">L’index de l’emplacement peut être utilisé pour récupérer les métadonnées pour cette variable locale.</span><span class="sxs-lookup"><span data-stu-id="26e10-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26e10-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="26e10-115">Requirements</span></span>  
 <span data-ttu-id="26e10-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26e10-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26e10-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26e10-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26e10-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26e10-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26e10-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26e10-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26e10-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26e10-120">See also</span></span>

- [<span data-ttu-id="26e10-121">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="26e10-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
