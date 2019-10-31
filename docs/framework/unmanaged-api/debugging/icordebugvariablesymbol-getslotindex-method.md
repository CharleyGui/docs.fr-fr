---
title: 'Méthode icordebugvariablesymbol :: GetSlotIndex, méthode'
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: a7a7ecf7d3e3d0d2125b03d3604c44138a2be0cc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120969"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="b7675-102">Méthode icordebugvariablesymbol :: GetSlotIndex, méthode</span><span class="sxs-lookup"><span data-stu-id="b7675-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="b7675-103">Obtient l'index d'emplacement géré d'une variable locale.</span><span class="sxs-lookup"><span data-stu-id="b7675-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7675-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7675-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7675-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b7675-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="b7675-106">[out] Pointeur vers l'index d'emplacement de la variable locale.</span><span class="sxs-lookup"><span data-stu-id="b7675-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7675-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b7675-107">Return Value</span></span>  
 <span data-ttu-id="b7675-108">`S_OK` si l'opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="b7675-108">`S_OK` if successful.</span></span> <span data-ttu-id="b7675-109">`E_FAIL` si la variable est un argument de fonction.</span><span class="sxs-lookup"><span data-stu-id="b7675-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7675-110">Notes</span><span class="sxs-lookup"><span data-stu-id="b7675-110">Remarks</span></span>  
 <span data-ttu-id="b7675-111">L'index emplacement managé d'une variable locale peut être utilisé pour récupérer des informations de métadonnées de la variable.</span><span class="sxs-lookup"><span data-stu-id="b7675-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7675-112">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b7675-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7675-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="b7675-113">Requirements</span></span>  
 <span data-ttu-id="b7675-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7675-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7675-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7675-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7675-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7675-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7675-117">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7675-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7675-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7675-118">See also</span></span>

- [<span data-ttu-id="b7675-119">ICorDebugVariableSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="b7675-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="b7675-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="b7675-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
