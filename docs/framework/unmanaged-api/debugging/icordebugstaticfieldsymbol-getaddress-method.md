---
title: ICorDebugStaticFieldSymbol::GetAddress, méthode
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d41b99d7410333cb6a22443271c1fcbc41c3594
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962698"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="95036-102">ICorDebugStaticFieldSymbol::GetAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="95036-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="95036-103">Obtient l’adresse d’un champ static.</span><span class="sxs-lookup"><span data-stu-id="95036-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95036-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95036-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95036-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="95036-105">Parameters</span></span>  
 <span data-ttu-id="95036-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="95036-106">pRVA</span></span>  
 <span data-ttu-id="95036-107">[out] Pointeur vers l'adresse virtuelle relative (RVA) du champ statique.</span><span class="sxs-lookup"><span data-stu-id="95036-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95036-108">Notes</span><span class="sxs-lookup"><span data-stu-id="95036-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95036-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="95036-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95036-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="95036-110">Requirements</span></span>  
 <span data-ttu-id="95036-111">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95036-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95036-112">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="95036-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95036-113">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95036-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95036-114">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95036-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95036-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95036-115">See also</span></span>

- [<span data-ttu-id="95036-116">ICorDebugStaticFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="95036-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="95036-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="95036-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
