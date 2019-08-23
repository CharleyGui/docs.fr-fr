---
title: ICorDebugInstanceFieldSymbol::GetName, méthode
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b1b3cc489c504942806b043fa2e3b76d5415d84
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936931"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="8a8e6-102">ICorDebugInstanceFieldSymbol::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="8a8e6-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="8a8e6-103">Obtient le nom du champ d'instance.</span><span class="sxs-lookup"><span data-stu-id="8a8e6-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a8e6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a8e6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a8e6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8a8e6-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="8a8e6-106">[in] Nombre de caractères dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="8a8e6-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="8a8e6-107">[out] Pointeur vers le nombre de caractères réellement écrits dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="8a8e6-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="8a8e6-108">[out] Tableau de caractères qui stocke le nom retourné.</span><span class="sxs-lookup"><span data-stu-id="8a8e6-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a8e6-109">Notes</span><span class="sxs-lookup"><span data-stu-id="8a8e6-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a8e6-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8a8e6-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a8e6-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8a8e6-111">Requirements</span></span>  
 <span data-ttu-id="8a8e6-112">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a8e6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a8e6-113">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8a8e6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a8e6-114">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a8e6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a8e6-115">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a8e6-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a8e6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a8e6-116">See also</span></span>

- [<span data-ttu-id="8a8e6-117">ICorDebugInstanceFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="8a8e6-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="8a8e6-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="8a8e6-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
