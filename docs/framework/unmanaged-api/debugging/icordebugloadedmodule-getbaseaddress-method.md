---
title: ICorDebugLoadedModule::GetBaseAddress (méthode)
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
ms.openlocfilehash: 29153da86812583a0ea789da0c0816f08e0a6b43
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698076"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="21410-102">ICorDebugLoadedModule::GetBaseAddress (méthode)</span><span class="sxs-lookup"><span data-stu-id="21410-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>

<span data-ttu-id="21410-103">Obtient l'adresse de base du module chargé.</span><span class="sxs-lookup"><span data-stu-id="21410-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21410-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21410-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21410-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="21410-105">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="21410-106">[out] Pointeur vers l'adresse de base du module chargé.</span><span class="sxs-lookup"><span data-stu-id="21410-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21410-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="21410-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21410-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="21410-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21410-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="21410-109">Requirements</span></span>  

 <span data-ttu-id="21410-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21410-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21410-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21410-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21410-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21410-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21410-113">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21410-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21410-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21410-114">See also</span></span>

- [<span data-ttu-id="21410-115">ICorDebugLoadedModule (interface)</span><span class="sxs-lookup"><span data-stu-id="21410-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="21410-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="21410-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
