---
title: ICorDebugSymbolProvider::GetStaticFieldSymbols, méthode
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
ms.openlocfilehash: 2428521b9b08060fd147a7c9b9054239bf957f69
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379373"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="8665f-102">ICorDebugSymbolProvider::GetStaticFieldSymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="8665f-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="8665f-103">Obtient les symboles de champ statique qui correspondent à une signature typespec.</span><span class="sxs-lookup"><span data-stu-id="8665f-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8665f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8665f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8665f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8665f-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="8665f-106">[in] Nombre d'octets dans le tableau `typeSig`.</span><span class="sxs-lookup"><span data-stu-id="8665f-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="8665f-107">[in] Tableau d'octets contenant la signature `typespec`.</span><span class="sxs-lookup"><span data-stu-id="8665f-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="8665f-108">[in] Nombre de symboles demandés.</span><span class="sxs-lookup"><span data-stu-id="8665f-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="8665f-109">[out] Pointeur vers le nombre de symboles récupérés par la méthode.</span><span class="sxs-lookup"><span data-stu-id="8665f-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="8665f-110">à Pointeur vers un tableau [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) qui contient les symboles de champ statique demandés.</span><span class="sxs-lookup"><span data-stu-id="8665f-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8665f-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="8665f-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8665f-112">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8665f-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8665f-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8665f-113">Requirements</span></span>  
 <span data-ttu-id="8665f-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8665f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8665f-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8665f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8665f-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8665f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8665f-117">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8665f-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8665f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8665f-118">See also</span></span>

- [<span data-ttu-id="8665f-119">GetInstanceFieldSymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="8665f-119">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="8665f-120">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="8665f-120">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="8665f-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="8665f-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
