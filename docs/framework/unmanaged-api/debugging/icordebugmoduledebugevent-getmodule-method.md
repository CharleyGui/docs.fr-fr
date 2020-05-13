---
title: ICorDebugModuleDebugEvent::GetModule, méthode
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: 1df71ddbf1ee76cc8202d8f9e263b9d95b4aaa09
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213359"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="7874e-102">ICorDebugModuleDebugEvent::GetModule, méthode</span><span class="sxs-lookup"><span data-stu-id="7874e-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="7874e-103">Obtient le module fusionné qui vient d’être chargé ou déchargé.</span><span class="sxs-lookup"><span data-stu-id="7874e-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7874e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7874e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7874e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7874e-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="7874e-106">[out] Pointeur vers l'adresse d'un objet ICorDebugModule représentant le module fusionné qui vient d'être chargé ou déchargé.</span><span class="sxs-lookup"><span data-stu-id="7874e-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7874e-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="7874e-107">Remarks</span></span>  
 <span data-ttu-id="7874e-108">Vous pouvez appeler la méthode [GetEventKind](icordebugdebugevent-geteventkind-method.md) pour déterminer si le module a été chargé ou déchargé.</span><span class="sxs-lookup"><span data-stu-id="7874e-108">You can call the [GetEventKind](icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7874e-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7874e-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7874e-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7874e-110">Requirements</span></span>  
 <span data-ttu-id="7874e-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7874e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7874e-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7874e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7874e-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7874e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7874e-114">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7874e-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7874e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7874e-115">See also</span></span>

- [<span data-ttu-id="7874e-116">ICorDebugModuleDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="7874e-116">ICorDebugModuleDebugEvent Interface</span></span>](icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="7874e-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="7874e-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
