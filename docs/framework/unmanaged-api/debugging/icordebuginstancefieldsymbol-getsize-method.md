---
title: ICorDebugInstanceFieldSymbol::GetSize, méthode
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
ms.openlocfilehash: eb70c441441954e2ffce6ca832c58369c606b128
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782283"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="bf5fa-102">ICorDebugInstanceFieldSymbol::GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="bf5fa-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="bf5fa-103">Obtient la taille en octets du champ d'instance.</span><span class="sxs-lookup"><span data-stu-id="bf5fa-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf5fa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf5fa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf5fa-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="bf5fa-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="bf5fa-106">[out] Pointeur vers la longueur du champ.</span><span class="sxs-lookup"><span data-stu-id="bf5fa-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf5fa-107">Notes</span><span class="sxs-lookup"><span data-stu-id="bf5fa-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf5fa-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bf5fa-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf5fa-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="bf5fa-109">Requirements</span></span>  
 <span data-ttu-id="bf5fa-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf5fa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf5fa-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf5fa-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf5fa-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf5fa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf5fa-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf5fa-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf5fa-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf5fa-114">See also</span></span>

- [<span data-ttu-id="bf5fa-115">ICorDebugInstanceFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="bf5fa-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="bf5fa-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="bf5fa-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
