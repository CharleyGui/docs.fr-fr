---
title: ICorDebugAssemblyEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugAssemblyEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum
helpviewer_keywords:
- ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: 891ceb43-5161-421e-a0bf-299962fd7efd
topic_type:
- apiref
ms.openlocfilehash: dea5c0fd5d4ed1f830d9e75097d49c544dac2e57
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719241"
---
# <a name="icordebugassemblyenum-interface"></a><span data-ttu-id="97dcf-102">ICorDebugAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="97dcf-102">ICorDebugAssemblyEnum Interface</span></span>

<span data-ttu-id="97dcf-103">Implémente les méthodes ICorDebugEnum et énumère les tableaux ICorDebugAssembly.</span><span class="sxs-lookup"><span data-stu-id="97dcf-103">Implements ICorDebugEnum methods and enumerates ICorDebugAssembly arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97dcf-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="97dcf-104">Methods</span></span>  
  
|<span data-ttu-id="97dcf-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="97dcf-105">Method</span></span>|<span data-ttu-id="97dcf-106">Description</span><span class="sxs-lookup"><span data-stu-id="97dcf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97dcf-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="97dcf-107">Next Method</span></span>](icordebugassemblyenum-next-method.md)|<span data-ttu-id="97dcf-108">Obtient le nombre spécifié d' `ICorDebugAssembly` instances dans l’énumération, en démarrant à partir de la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="97dcf-108">Gets the specified number of `ICorDebugAssembly` instances in the enumeration, starting from the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97dcf-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="97dcf-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97dcf-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="97dcf-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97dcf-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="97dcf-111">Requirements</span></span>  

 <span data-ttu-id="97dcf-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97dcf-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97dcf-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97dcf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97dcf-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97dcf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97dcf-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97dcf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97dcf-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97dcf-116">See also</span></span>

- [<span data-ttu-id="97dcf-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="97dcf-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
