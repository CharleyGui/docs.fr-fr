---
title: ICorDebugSymbolProvider::GetMethodLocalSymbols, méthode
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
ms.openlocfilehash: 7e9aa01a3fa1c90b0ab4f85970c4eb294b9a4904
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379611"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a><span data-ttu-id="02992-102">ICorDebugSymbolProvider::GetMethodLocalSymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="02992-102">ICorDebugSymbolProvider::GetMethodLocalSymbols Method</span></span>
<span data-ttu-id="02992-103">Obtient les symboles locaux d'une méthode selon l'adresse virtuelle relative (RVA) de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="02992-103">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02992-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02992-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02992-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="02992-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="02992-106">[in] Adresse virtuelle relative native de la méthode.</span><span class="sxs-lookup"><span data-stu-id="02992-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="02992-107">[in] Nombre de symboles locaux demandés.</span><span class="sxs-lookup"><span data-stu-id="02992-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="02992-108">[out] Pointeur vers le nombre de symboles récupérés par la méthode.</span><span class="sxs-lookup"><span data-stu-id="02992-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="02992-109">à Pointeur vers un tableau [méthode icordebugvariablesymbol](icordebugvariablesymbol-interface.md) qui contient les symboles locaux de la méthode.</span><span class="sxs-lookup"><span data-stu-id="02992-109">[out] A pointer to an [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02992-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="02992-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02992-111">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="02992-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02992-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="02992-112">Requirements</span></span>  
 <span data-ttu-id="02992-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02992-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02992-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02992-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02992-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02992-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02992-116">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02992-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02992-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02992-117">See also</span></span>

- [<span data-ttu-id="02992-118">GetMethodParameterSymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="02992-118">GetMethodParameterSymbols Method</span></span>](icordebugsymbolprovider-getmethodparametersymbols-method.md)
- [<span data-ttu-id="02992-119">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="02992-119">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="02992-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="02992-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
