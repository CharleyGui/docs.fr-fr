---
title: 'ICorDebugSymbolProvider :: Getmethodparametersymbols,, méthode'
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
ms.openlocfilehash: 1f7da156e5a164dc753e2283bc7ab24d18983173
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138841"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="67ec8-102">ICorDebugSymbolProvider :: Getmethodparametersymbols,, méthode</span><span class="sxs-lookup"><span data-stu-id="67ec8-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>
<span data-ttu-id="67ec8-103">Obtient les symboles de paramètre d'une méthode en fonction de l'adresse virtuelle relative (RVA) de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="67ec8-103">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67ec8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67ec8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67ec8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="67ec8-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="67ec8-106">[in] Adresse virtuelle relative native de la méthode.</span><span class="sxs-lookup"><span data-stu-id="67ec8-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="67ec8-107">[in] Nombre de symboles locaux demandés.</span><span class="sxs-lookup"><span data-stu-id="67ec8-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="67ec8-108">[out] Pointeur vers le nombre de symboles récupérés par la méthode.</span><span class="sxs-lookup"><span data-stu-id="67ec8-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="67ec8-109">à Pointeur vers un tableau [méthode icordebugvariablesymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) qui contient les symboles locaux de la méthode.</span><span class="sxs-lookup"><span data-stu-id="67ec8-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67ec8-110">Notes</span><span class="sxs-lookup"><span data-stu-id="67ec8-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="67ec8-111">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="67ec8-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67ec8-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="67ec8-112">Requirements</span></span>  
 <span data-ttu-id="67ec8-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67ec8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67ec8-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67ec8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67ec8-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67ec8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67ec8-116">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67ec8-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67ec8-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67ec8-117">See also</span></span>

- [<span data-ttu-id="67ec8-118">GetMethodLocalSymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="67ec8-118">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [<span data-ttu-id="67ec8-119">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="67ec8-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="67ec8-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="67ec8-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
