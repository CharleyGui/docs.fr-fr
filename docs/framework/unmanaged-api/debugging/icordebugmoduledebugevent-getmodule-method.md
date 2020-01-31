---
title: ICorDebugModuleDebugEvent::GetModule, méthode
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: 4d9eea8fb5c42002763a0ae52a186bf2c1e6d2ee
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792902"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="4bebf-102">ICorDebugModuleDebugEvent::GetModule, méthode</span><span class="sxs-lookup"><span data-stu-id="4bebf-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="4bebf-103">Obtient le module fusionné qui vient d’être chargé ou déchargé.</span><span class="sxs-lookup"><span data-stu-id="4bebf-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bebf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bebf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bebf-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="4bebf-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="4bebf-106">[out] Pointeur vers l'adresse d'un objet ICorDebugModule représentant le module fusionné qui vient d'être chargé ou déchargé.</span><span class="sxs-lookup"><span data-stu-id="4bebf-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bebf-107">Notes</span><span class="sxs-lookup"><span data-stu-id="4bebf-107">Remarks</span></span>  
 <span data-ttu-id="4bebf-108">Vous pouvez appeler la méthode [GetEventKind](icordebugdebugevent-geteventkind-method.md) pour déterminer si le module a été chargé ou déchargé.</span><span class="sxs-lookup"><span data-stu-id="4bebf-108">You can call the [GetEventKind](icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4bebf-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4bebf-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bebf-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="4bebf-110">Requirements</span></span>  
 <span data-ttu-id="4bebf-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bebf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bebf-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4bebf-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4bebf-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4bebf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4bebf-114">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bebf-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bebf-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bebf-115">See also</span></span>

- [<span data-ttu-id="4bebf-116">ICorDebugModuleDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="4bebf-116">ICorDebugModuleDebugEvent Interface</span></span>](icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="4bebf-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="4bebf-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
