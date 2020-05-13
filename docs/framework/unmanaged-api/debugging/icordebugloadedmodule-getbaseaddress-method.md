---
title: ICorDebugLoadedModule::GetBaseAddress (méthode)
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
ms.openlocfilehash: d8c91c10577efd6a76af778cd01002de006df43a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209875"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="e2a8e-102">ICorDebugLoadedModule::GetBaseAddress (méthode)</span><span class="sxs-lookup"><span data-stu-id="e2a8e-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="e2a8e-103">Obtient l'adresse de base du module chargé.</span><span class="sxs-lookup"><span data-stu-id="e2a8e-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2a8e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2a8e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2a8e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e2a8e-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="e2a8e-106">[out] Pointeur vers l'adresse de base du module chargé.</span><span class="sxs-lookup"><span data-stu-id="e2a8e-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2a8e-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="e2a8e-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2a8e-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e2a8e-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2a8e-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e2a8e-109">Requirements</span></span>  
 <span data-ttu-id="e2a8e-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2a8e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2a8e-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e2a8e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2a8e-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2a8e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2a8e-113">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2a8e-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2a8e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2a8e-114">See also</span></span>

- [<span data-ttu-id="e2a8e-115">ICorDebugLoadedModule (interface)</span><span class="sxs-lookup"><span data-stu-id="e2a8e-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="e2a8e-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e2a8e-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
