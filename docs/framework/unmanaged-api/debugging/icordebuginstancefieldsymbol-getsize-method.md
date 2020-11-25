---
title: ICorDebugInstanceFieldSymbol::GetSize, méthode
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
ms.openlocfilehash: c4b193b45e30b0eba3367f18cb1e4c2b4e108fa8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724908"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="007ac-102">ICorDebugInstanceFieldSymbol::GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="007ac-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>

<span data-ttu-id="007ac-103">Obtient la taille en octets du champ d'instance.</span><span class="sxs-lookup"><span data-stu-id="007ac-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="007ac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="007ac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="007ac-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="007ac-105">Parameters</span></span>  

 `pcbSize`  
 <span data-ttu-id="007ac-106">[out] Pointeur vers la longueur du champ.</span><span class="sxs-lookup"><span data-stu-id="007ac-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="007ac-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="007ac-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="007ac-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="007ac-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="007ac-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="007ac-109">Requirements</span></span>  

 <span data-ttu-id="007ac-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="007ac-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="007ac-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="007ac-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="007ac-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="007ac-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="007ac-113">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="007ac-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="007ac-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="007ac-114">See also</span></span>

- [<span data-ttu-id="007ac-115">ICorDebugInstanceFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="007ac-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="007ac-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="007ac-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
