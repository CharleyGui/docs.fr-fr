---
title: ICorDebugStaticFieldSymbol::GetName, méthode
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: 75f5324296f9b42406157d06351f7e680a749444
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378752"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="60258-102">ICorDebugStaticFieldSymbol::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="60258-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="60258-103">Obtient le nom du champ static.</span><span class="sxs-lookup"><span data-stu-id="60258-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60258-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60258-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60258-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="60258-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="60258-106">[in] Nombre de caractères dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="60258-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="60258-107">[out] Pointeur vers le nombre de caractères réellement écrits dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="60258-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="60258-108">[out] Tableau de caractères qui stocke le nom retourné.</span><span class="sxs-lookup"><span data-stu-id="60258-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60258-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="60258-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60258-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="60258-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60258-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="60258-111">Requirements</span></span>  
 <span data-ttu-id="60258-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60258-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60258-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60258-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60258-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60258-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60258-115">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60258-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60258-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60258-116">See also</span></span>

- [<span data-ttu-id="60258-117">ICorDebugStaticFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="60258-117">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="60258-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="60258-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
