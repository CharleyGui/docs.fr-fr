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
ms.openlocfilehash: 4b071bd8e9d96084848c1553385eec5f8beca624
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711726"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="1324a-102">ICorDebugVariableHome :: GetSlotIndex, méthode</span><span class="sxs-lookup"><span data-stu-id="1324a-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>

<span data-ttu-id="1324a-103">Obtient l’index d’emplacement managé d’une variable locale.</span><span class="sxs-lookup"><span data-stu-id="1324a-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1324a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1324a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1324a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1324a-105">Parameters</span></span>  

 `pSlotIndex`  
 <span data-ttu-id="1324a-106">à Pointeur vers l’index d’emplacement d’une variable locale.</span><span class="sxs-lookup"><span data-stu-id="1324a-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1324a-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="1324a-107">Return Value</span></span>  

 <span data-ttu-id="1324a-108">La méthode retourne les valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="1324a-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="1324a-109">Value</span><span class="sxs-lookup"><span data-stu-id="1324a-109">Value</span></span>|<span data-ttu-id="1324a-110">Description</span><span class="sxs-lookup"><span data-stu-id="1324a-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="1324a-111">L’appel de méthode a retourné une valeur d’index d’emplacement dans `pSlotIndex` .</span><span class="sxs-lookup"><span data-stu-id="1324a-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="1324a-112">L’instance [ICorDebugVariableHome](icordebugvariablehome-interface.md) actuelle représente un argument de fonction.</span><span class="sxs-lookup"><span data-stu-id="1324a-112">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1324a-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="1324a-113">Remarks</span></span>  

 <span data-ttu-id="1324a-114">L’index d’emplacement peut être utilisé pour récupérer les métadonnées de cette variable locale.</span><span class="sxs-lookup"><span data-stu-id="1324a-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1324a-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1324a-115">Requirements</span></span>  

 <span data-ttu-id="1324a-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1324a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1324a-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1324a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1324a-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1324a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1324a-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1324a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1324a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1324a-120">See also</span></span>

- [<span data-ttu-id="1324a-121">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="1324a-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
