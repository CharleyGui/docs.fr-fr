---
title: ICorDebugLoadedModule::GetBaseAddress, méthode
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
ms.openlocfilehash: 190c9114cffa537ba162b19abdf30d5a6aee87f8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788449"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="f6e83-102">ICorDebugLoadedModule::GetBaseAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="f6e83-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="f6e83-103">Obtient l'adresse de base du module chargé.</span><span class="sxs-lookup"><span data-stu-id="f6e83-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6e83-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6e83-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6e83-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="f6e83-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="f6e83-106">[out] Pointeur vers l'adresse de base du module chargé.</span><span class="sxs-lookup"><span data-stu-id="f6e83-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6e83-107">Notes</span><span class="sxs-lookup"><span data-stu-id="f6e83-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6e83-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f6e83-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6e83-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="f6e83-109">Requirements</span></span>  
 <span data-ttu-id="f6e83-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6e83-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6e83-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6e83-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6e83-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6e83-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6e83-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6e83-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6e83-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6e83-114">See also</span></span>

- [<span data-ttu-id="f6e83-115">ICorDebugLoadedModule, interface</span><span class="sxs-lookup"><span data-stu-id="f6e83-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="f6e83-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f6e83-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
