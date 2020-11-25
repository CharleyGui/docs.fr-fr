---
title: ICorDebugModuleDebugEvent::GetModule, méthode
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: ec23cda02ff689a3365fe96fb5280054a9795caa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709503"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="0aa7a-102">ICorDebugModuleDebugEvent::GetModule, méthode</span><span class="sxs-lookup"><span data-stu-id="0aa7a-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>

<span data-ttu-id="0aa7a-103">Obtient le module fusionné qui vient d’être chargé ou déchargé.</span><span class="sxs-lookup"><span data-stu-id="0aa7a-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aa7a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0aa7a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0aa7a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0aa7a-105">Parameters</span></span>  

 `ppModule`  
 <span data-ttu-id="0aa7a-106">[out] Pointeur vers l'adresse d'un objet ICorDebugModule représentant le module fusionné qui vient d'être chargé ou déchargé.</span><span class="sxs-lookup"><span data-stu-id="0aa7a-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0aa7a-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="0aa7a-107">Remarks</span></span>  

 <span data-ttu-id="0aa7a-108">Vous pouvez appeler la méthode [GetEventKind](icordebugdebugevent-geteventkind-method.md) pour déterminer si le module a été chargé ou déchargé.</span><span class="sxs-lookup"><span data-stu-id="0aa7a-108">You can call the [GetEventKind](icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0aa7a-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0aa7a-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aa7a-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0aa7a-110">Requirements</span></span>  

 <span data-ttu-id="0aa7a-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0aa7a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aa7a-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0aa7a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0aa7a-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0aa7a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0aa7a-114">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0aa7a-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aa7a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0aa7a-115">See also</span></span>

- [<span data-ttu-id="0aa7a-116">ICorDebugModuleDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="0aa7a-116">ICorDebugModuleDebugEvent Interface</span></span>](icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="0aa7a-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0aa7a-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
