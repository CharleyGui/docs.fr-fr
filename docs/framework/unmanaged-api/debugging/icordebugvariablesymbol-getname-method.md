---
title: 'Méthode icordebugvariablesymbol :: GetName, méthode'
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: 9bc32d3372710b4c4e92aa89df5e6e7839ad3078
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121016"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="e5ddb-102">Méthode icordebugvariablesymbol :: GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="e5ddb-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="e5ddb-103">Obtient le nom d'une variable.</span><span class="sxs-lookup"><span data-stu-id="e5ddb-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5ddb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5ddb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5ddb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e5ddb-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="e5ddb-106">[in] Nombre de caractères dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="e5ddb-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e5ddb-107">[out] Pointeur vers le nombre de caractères réellement écrits dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="e5ddb-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="e5ddb-108">Pointeur vers un tableau de caractères qui contient le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="e5ddb-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5ddb-109">Notes</span><span class="sxs-lookup"><span data-stu-id="e5ddb-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5ddb-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e5ddb-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5ddb-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="e5ddb-111">Requirements</span></span>  
 <span data-ttu-id="e5ddb-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5ddb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5ddb-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5ddb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5ddb-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5ddb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5ddb-115">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5ddb-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5ddb-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5ddb-116">See also</span></span>

- [<span data-ttu-id="e5ddb-117">ICorDebugVariableSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="e5ddb-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="e5ddb-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e5ddb-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
