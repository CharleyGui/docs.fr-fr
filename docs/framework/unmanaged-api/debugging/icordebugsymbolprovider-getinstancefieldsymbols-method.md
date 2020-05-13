---
title: ICorDebugSymbolProvider::GetInstanceFieldSymbols, méthode
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
ms.openlocfilehash: 9ecc61ed6cac73a519f33e00cbfbfecc20ac2ebe
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379641"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="5b455-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="5b455-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>
<span data-ttu-id="5b455-103">Obtient les symboles de champ d'instance qui correspondent à une signature typespec.</span><span class="sxs-lookup"><span data-stu-id="5b455-103">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b455-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b455-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b455-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5b455-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="5b455-106">[in] Nombre d'octets dans le tableau `typeSig`.</span><span class="sxs-lookup"><span data-stu-id="5b455-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="5b455-107">[in] Tableau d'octets contenant la signature `typespec`.</span><span class="sxs-lookup"><span data-stu-id="5b455-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="5b455-108">[in] Nombre de symboles demandés.</span><span class="sxs-lookup"><span data-stu-id="5b455-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="5b455-109">[out] Pointeur vers le nombre de symboles récupérés par la méthode.</span><span class="sxs-lookup"><span data-stu-id="5b455-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="5b455-110">à Pointeur vers un tableau [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) qui contient les symboles de champ d’instance demandés.</span><span class="sxs-lookup"><span data-stu-id="5b455-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b455-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="5b455-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b455-112">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5b455-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b455-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5b455-113">Requirements</span></span>  
 <span data-ttu-id="5b455-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b455-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b455-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b455-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b455-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b455-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b455-117">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b455-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b455-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b455-118">See also</span></span>

- [<span data-ttu-id="5b455-119">GetStaticFieldSymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="5b455-119">GetStaticFieldSymbols Method</span></span>](icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [<span data-ttu-id="5b455-120">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="5b455-120">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="5b455-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5b455-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
