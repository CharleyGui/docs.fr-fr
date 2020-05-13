---
title: ICorDebugStaticFieldSymbol::GetAddress, méthode
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
ms.openlocfilehash: 7b8072234df172eeafd77db90287ea3319c08ec7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378766"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="e0fb6-102">ICorDebugStaticFieldSymbol::GetAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="e0fb6-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="e0fb6-103">Obtient l’adresse d’un champ static.</span><span class="sxs-lookup"><span data-stu-id="e0fb6-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0fb6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0fb6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0fb6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e0fb6-105">Parameters</span></span>  
 <span data-ttu-id="e0fb6-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="e0fb6-106">pRVA</span></span>  
 <span data-ttu-id="e0fb6-107">[out] Pointeur vers l'adresse virtuelle relative (RVA) du champ statique.</span><span class="sxs-lookup"><span data-stu-id="e0fb6-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0fb6-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="e0fb6-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0fb6-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e0fb6-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0fb6-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e0fb6-110">Requirements</span></span>  
 <span data-ttu-id="e0fb6-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0fb6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0fb6-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0fb6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0fb6-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0fb6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0fb6-114">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0fb6-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0fb6-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0fb6-115">See also</span></span>

- [<span data-ttu-id="e0fb6-116">ICorDebugStaticFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="e0fb6-116">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="e0fb6-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e0fb6-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
