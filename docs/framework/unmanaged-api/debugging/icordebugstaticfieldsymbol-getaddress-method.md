---
title: ICorDebugStaticFieldSymbol::GetAddress, méthode
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
ms.openlocfilehash: be4d59fe668026c4b40be4c6d0afcf718c8157bd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791845"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="e53d4-102">ICorDebugStaticFieldSymbol::GetAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="e53d4-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="e53d4-103">Obtient l’adresse d’un champ static.</span><span class="sxs-lookup"><span data-stu-id="e53d4-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e53d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e53d4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e53d4-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="e53d4-105">Parameters</span></span>  
 <span data-ttu-id="e53d4-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="e53d4-106">pRVA</span></span>  
 <span data-ttu-id="e53d4-107">[out] Pointeur vers l'adresse virtuelle relative (RVA) du champ statique.</span><span class="sxs-lookup"><span data-stu-id="e53d4-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e53d4-108">Notes</span><span class="sxs-lookup"><span data-stu-id="e53d4-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e53d4-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e53d4-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e53d4-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e53d4-110">Requirements</span></span>  
 <span data-ttu-id="e53d4-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e53d4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e53d4-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e53d4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e53d4-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e53d4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e53d4-114">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e53d4-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e53d4-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e53d4-115">See also</span></span>

- [<span data-ttu-id="e53d4-116">ICorDebugStaticFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="e53d4-116">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="e53d4-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e53d4-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
