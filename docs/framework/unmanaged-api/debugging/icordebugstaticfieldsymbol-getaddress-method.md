---
title: ICorDebugStaticFieldSymbol::GetAddress, méthode
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
ms.openlocfilehash: e9404b429ad4507acb5132a86af5f287dbcf07b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677282"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="3d65c-102">ICorDebugStaticFieldSymbol::GetAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="3d65c-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>

<span data-ttu-id="3d65c-103">Obtient l’adresse d’un champ static.</span><span class="sxs-lookup"><span data-stu-id="3d65c-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d65c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d65c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d65c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3d65c-105">Parameters</span></span>  

 <span data-ttu-id="3d65c-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="3d65c-106">pRVA</span></span>  
 <span data-ttu-id="3d65c-107">[out] Pointeur vers l'adresse virtuelle relative (RVA) du champ statique.</span><span class="sxs-lookup"><span data-stu-id="3d65c-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d65c-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="3d65c-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d65c-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3d65c-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d65c-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3d65c-110">Requirements</span></span>  

 <span data-ttu-id="3d65c-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d65c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d65c-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d65c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d65c-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d65c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d65c-114">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d65c-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d65c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d65c-115">See also</span></span>

- [<span data-ttu-id="3d65c-116">ICorDebugStaticFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="3d65c-116">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="3d65c-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="3d65c-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
