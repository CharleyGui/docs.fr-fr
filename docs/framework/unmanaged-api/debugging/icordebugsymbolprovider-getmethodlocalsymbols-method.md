---
title: ICorDebugSymbolProvider::GetMethodLocalSymbols, méthode
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24671c371ae8a0a9f3c7ca650a71298c69e2fae1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955675"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a><span data-ttu-id="c48fe-102">ICorDebugSymbolProvider::GetMethodLocalSymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="c48fe-102">ICorDebugSymbolProvider::GetMethodLocalSymbols Method</span></span>
<span data-ttu-id="c48fe-103">Obtient les symboles locaux d'une méthode selon l'adresse virtuelle relative (RVA) de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="c48fe-103">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c48fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c48fe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c48fe-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c48fe-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="c48fe-106">[in] Adresse virtuelle relative native de la méthode.</span><span class="sxs-lookup"><span data-stu-id="c48fe-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="c48fe-107">[in] Nombre de symboles locaux demandés.</span><span class="sxs-lookup"><span data-stu-id="c48fe-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="c48fe-108">[out] Pointeur vers le nombre de symboles récupérés par la méthode.</span><span class="sxs-lookup"><span data-stu-id="c48fe-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="c48fe-109">à Pointeur vers un tableau [méthode icordebugvariablesymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) qui contient les symboles locaux de la méthode.</span><span class="sxs-lookup"><span data-stu-id="c48fe-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c48fe-110">Notes</span><span class="sxs-lookup"><span data-stu-id="c48fe-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c48fe-111">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c48fe-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c48fe-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c48fe-112">Requirements</span></span>  
 <span data-ttu-id="c48fe-113">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c48fe-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c48fe-114">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c48fe-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c48fe-115">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c48fe-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c48fe-116">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c48fe-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c48fe-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c48fe-117">See also</span></span>

- [<span data-ttu-id="c48fe-118">GetMethodParameterSymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="c48fe-118">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)
- [<span data-ttu-id="c48fe-119">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="c48fe-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="c48fe-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c48fe-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
