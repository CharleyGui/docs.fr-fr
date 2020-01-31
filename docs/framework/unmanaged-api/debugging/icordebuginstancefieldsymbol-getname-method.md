---
title: ICorDebugInstanceFieldSymbol::GetName, méthode
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
ms.openlocfilehash: 05914863dfbc2aca608a5d74f298f81c64345fe8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782386"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="f7299-102">ICorDebugInstanceFieldSymbol::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="f7299-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="f7299-103">Obtient le nom du champ d'instance.</span><span class="sxs-lookup"><span data-stu-id="f7299-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7299-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7299-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7299-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="f7299-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="f7299-106">[in] Nombre de caractères dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="f7299-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f7299-107">[out] Pointeur vers le nombre de caractères réellement écrits dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="f7299-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="f7299-108">[out] Tableau de caractères qui stocke le nom retourné.</span><span class="sxs-lookup"><span data-stu-id="f7299-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7299-109">Notes</span><span class="sxs-lookup"><span data-stu-id="f7299-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7299-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f7299-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7299-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="f7299-111">Requirements</span></span>  
 <span data-ttu-id="f7299-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7299-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7299-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7299-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7299-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7299-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7299-115">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7299-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7299-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7299-116">See also</span></span>

- [<span data-ttu-id="f7299-117">ICorDebugInstanceFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="f7299-117">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="f7299-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f7299-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
