---
title: Méthode ICorDebugVariableSymbol::GetName
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: 172eea452442aa94ea010e2c434908ab8d040a93
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790921"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="87d2a-102">Méthode ICorDebugVariableSymbol::GetName</span><span class="sxs-lookup"><span data-stu-id="87d2a-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="87d2a-103">Obtient le nom d'une variable.</span><span class="sxs-lookup"><span data-stu-id="87d2a-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87d2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87d2a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87d2a-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="87d2a-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="87d2a-106">[in] Nombre de caractères dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="87d2a-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="87d2a-107">[out] Pointeur vers le nombre de caractères réellement écrits dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="87d2a-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="87d2a-108">Pointeur vers un tableau de caractères qui contient le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="87d2a-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87d2a-109">Notes</span><span class="sxs-lookup"><span data-stu-id="87d2a-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87d2a-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="87d2a-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87d2a-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="87d2a-111">Requirements</span></span>  
 <span data-ttu-id="87d2a-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87d2a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87d2a-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87d2a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87d2a-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87d2a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87d2a-115">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87d2a-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87d2a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87d2a-116">See also</span></span>

- [<span data-ttu-id="87d2a-117">ICorDebugVariableSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="87d2a-117">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="87d2a-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="87d2a-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
