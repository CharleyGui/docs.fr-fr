---
title: ICorDebugStaticFieldSymbol::GetName, méthode
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: b1f5ca266f51df730dfb840c7bf003c47f31ece9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178512"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="ca9fa-102">ICorDebugStaticFieldSymbol::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="ca9fa-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="ca9fa-103">Obtient le nom du champ static.</span><span class="sxs-lookup"><span data-stu-id="ca9fa-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca9fa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca9fa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca9fa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ca9fa-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ca9fa-106">[in] Nombre de caractères dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="ca9fa-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ca9fa-107">[out] Pointeur vers le nombre de caractères réellement écrits dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="ca9fa-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="ca9fa-108">[out] Tableau de caractères qui stocke le nom retourné.</span><span class="sxs-lookup"><span data-stu-id="ca9fa-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca9fa-109">Notes </span><span class="sxs-lookup"><span data-stu-id="ca9fa-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca9fa-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ca9fa-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca9fa-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ca9fa-111">Requirements</span></span>  
 <span data-ttu-id="ca9fa-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca9fa-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca9fa-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca9fa-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca9fa-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca9fa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca9fa-115">**.NET Versions-cadre:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca9fa-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca9fa-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca9fa-116">See also</span></span>

- [<span data-ttu-id="ca9fa-117">ICorDebugStaticFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="ca9fa-117">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="ca9fa-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ca9fa-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
