---
title: ICorDebugModuleDebugEvent::GetModule, méthode
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e68fab11a881854ae4c3fe073f73150694d31ae5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965108"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="f632f-102">ICorDebugModuleDebugEvent::GetModule, méthode</span><span class="sxs-lookup"><span data-stu-id="f632f-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="f632f-103">Obtient le module fusionné qui vient d’être chargé ou déchargé.</span><span class="sxs-lookup"><span data-stu-id="f632f-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f632f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f632f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f632f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f632f-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="f632f-106">à Pointeur vers l’adresse d’un objet ICorDebugModule qui représente le module fusionné qui vient d’être chargé ou déchargé.</span><span class="sxs-lookup"><span data-stu-id="f632f-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f632f-107">Notes</span><span class="sxs-lookup"><span data-stu-id="f632f-107">Remarks</span></span>  
 <span data-ttu-id="f632f-108">Vous pouvez appeler la méthode [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) pour déterminer si le module a été chargé ou déchargé.</span><span class="sxs-lookup"><span data-stu-id="f632f-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f632f-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f632f-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f632f-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f632f-110">Requirements</span></span>  
 <span data-ttu-id="f632f-111">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f632f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f632f-112">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f632f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f632f-113">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f632f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f632f-114">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f632f-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f632f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f632f-115">See also</span></span>

- [<span data-ttu-id="f632f-116">ICorDebugModuleDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="f632f-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="f632f-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f632f-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
