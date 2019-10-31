---
title: 'ICorDebugSymbolProvider :: Getmergedassemblyrecords,, méthode'
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
ms.openlocfilehash: 6faf8960c06488c8fff5a076aae375529e1d0260
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138880"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="329a5-102">ICorDebugSymbolProvider :: Getmergedassemblyrecords,, méthode</span><span class="sxs-lookup"><span data-stu-id="329a5-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="329a5-103">Obtient les enregistrements de symbole de tous les assemblys fusionnés.</span><span class="sxs-lookup"><span data-stu-id="329a5-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="329a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="329a5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="329a5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="329a5-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="329a5-106">[in] Nombre d'enregistrements de symbole demandé.</span><span class="sxs-lookup"><span data-stu-id="329a5-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="329a5-107">[out] Pointeur vers le nombre d'enregistrements de symbole récupéré par la méthode.</span><span class="sxs-lookup"><span data-stu-id="329a5-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="329a5-108">Pointeur vers un tableau d’objets [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="329a5-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="329a5-109">Notes</span><span class="sxs-lookup"><span data-stu-id="329a5-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="329a5-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="329a5-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="329a5-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="329a5-111">Requirements</span></span>  
 <span data-ttu-id="329a5-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="329a5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="329a5-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="329a5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="329a5-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="329a5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="329a5-115">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="329a5-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="329a5-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="329a5-116">See also</span></span>

- [<span data-ttu-id="329a5-117">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="329a5-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="329a5-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="329a5-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
