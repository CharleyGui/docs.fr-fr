---
title: ICorDebugSymbolProvider::GetMethodParameterSymbols, méthode
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
ms.openlocfilehash: a940077e50ff251111ca6eedaee49401775644d3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791595"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="e29ec-102">ICorDebugSymbolProvider::GetMethodParameterSymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="e29ec-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>
<span data-ttu-id="e29ec-103">Obtient les symboles de paramètre d'une méthode en fonction de l'adresse virtuelle relative (RVA) de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="e29ec-103">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e29ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e29ec-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e29ec-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="e29ec-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="e29ec-106">[in] Adresse virtuelle relative native de la méthode.</span><span class="sxs-lookup"><span data-stu-id="e29ec-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="e29ec-107">[in] Nombre de symboles locaux demandés.</span><span class="sxs-lookup"><span data-stu-id="e29ec-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="e29ec-108">[out] Pointeur vers le nombre de symboles récupérés par la méthode.</span><span class="sxs-lookup"><span data-stu-id="e29ec-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="e29ec-109">à Pointeur vers un tableau [méthode icordebugvariablesymbol](icordebugvariablesymbol-interface.md) qui contient les symboles locaux de la méthode.</span><span class="sxs-lookup"><span data-stu-id="e29ec-109">[out] A pointer to an [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e29ec-110">Notes</span><span class="sxs-lookup"><span data-stu-id="e29ec-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e29ec-111">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e29ec-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e29ec-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e29ec-112">Requirements</span></span>  
 <span data-ttu-id="e29ec-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e29ec-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e29ec-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e29ec-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e29ec-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e29ec-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e29ec-116">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e29ec-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e29ec-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e29ec-117">See also</span></span>

- [<span data-ttu-id="e29ec-118">GetMethodLocalSymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="e29ec-118">GetMethodLocalSymbols Method</span></span>](icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [<span data-ttu-id="e29ec-119">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="e29ec-119">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="e29ec-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e29ec-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
