---
title: ICorDebugInstanceFieldSymbol::GetSize, méthode
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
ms.openlocfilehash: 3d3c6881ecd54fc48be92e5ea0dc74a5cfdabd8f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209950"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="8ca81-102">ICorDebugInstanceFieldSymbol::GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="8ca81-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="8ca81-103">Obtient la taille en octets du champ d'instance.</span><span class="sxs-lookup"><span data-stu-id="8ca81-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ca81-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ca81-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ca81-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8ca81-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="8ca81-106">[out] Pointeur vers la longueur du champ.</span><span class="sxs-lookup"><span data-stu-id="8ca81-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ca81-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="8ca81-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ca81-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8ca81-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ca81-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8ca81-109">Requirements</span></span>  
 <span data-ttu-id="8ca81-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ca81-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ca81-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ca81-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ca81-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ca81-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ca81-113">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ca81-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ca81-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ca81-114">See also</span></span>

- [<span data-ttu-id="8ca81-115">ICorDebugInstanceFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="8ca81-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="8ca81-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="8ca81-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
