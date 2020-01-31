---
title: ICorDebugStaticFieldSymbol::GetName, méthode
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: 0e4c52ff1ae6113ee2c3990a9d91682e10141902
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791828"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="bb8f6-102">ICorDebugStaticFieldSymbol::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="bb8f6-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="bb8f6-103">Obtient le nom du champ static.</span><span class="sxs-lookup"><span data-stu-id="bb8f6-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb8f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb8f6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb8f6-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="bb8f6-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="bb8f6-106">[in] Nombre de caractères dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="bb8f6-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="bb8f6-107">[out] Pointeur vers le nombre de caractères réellement écrits dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="bb8f6-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="bb8f6-108">[out] Tableau de caractères qui stocke le nom retourné.</span><span class="sxs-lookup"><span data-stu-id="bb8f6-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb8f6-109">Notes</span><span class="sxs-lookup"><span data-stu-id="bb8f6-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bb8f6-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bb8f6-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb8f6-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="bb8f6-111">Requirements</span></span>  
 <span data-ttu-id="bb8f6-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb8f6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb8f6-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb8f6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb8f6-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb8f6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb8f6-115">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb8f6-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb8f6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb8f6-116">See also</span></span>

- [<span data-ttu-id="bb8f6-117">ICorDebugStaticFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="bb8f6-117">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="bb8f6-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="bb8f6-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
