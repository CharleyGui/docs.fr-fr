---
title: Méthode ICorDebugVariableSymbol::GetName
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23637055e493c008db36b23515001895450d6ab9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967905"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="aaffe-102">Méthode ICorDebugVariableSymbol::GetName</span><span class="sxs-lookup"><span data-stu-id="aaffe-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="aaffe-103">Obtient le nom d'une variable.</span><span class="sxs-lookup"><span data-stu-id="aaffe-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaffe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aaffe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aaffe-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aaffe-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="aaffe-106">[in] Nombre de caractères dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="aaffe-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="aaffe-107">[out] Pointeur vers le nombre de caractères réellement écrits dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="aaffe-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="aaffe-108">Pointeur vers un tableau de caractères qui contient le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="aaffe-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aaffe-109">Notes</span><span class="sxs-lookup"><span data-stu-id="aaffe-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aaffe-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="aaffe-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaffe-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="aaffe-111">Requirements</span></span>  
 <span data-ttu-id="aaffe-112">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aaffe-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaffe-113">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aaffe-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aaffe-114">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aaffe-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aaffe-115">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaffe-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaffe-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aaffe-116">See also</span></span>

- [<span data-ttu-id="aaffe-117">ICorDebugVariableSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="aaffe-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="aaffe-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="aaffe-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
