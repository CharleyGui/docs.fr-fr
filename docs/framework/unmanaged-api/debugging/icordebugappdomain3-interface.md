---
title: ICorDebugAppDomain3, interface
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3
helpviewer_keywords:
- ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 256fd900fa73948b4ca42ac6b6f21f145effc461
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025890"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="7db4c-102">ICorDebugAppDomain3, interface</span><span class="sxs-lookup"><span data-stu-id="7db4c-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="7db4c-103">Fournit des méthodes pour récupérer des informations sur les représentations managées des types Windows Runtime actuellement chargés dans un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="7db4c-103">Provides methods to retrieve information about the managed representations of Windows Runtime types currently loaded in an application domain.</span></span> <span data-ttu-id="7db4c-104">Cette interface est une extension des interfaces ICorDebugAppDomain et ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="7db4c-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7db4c-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="7db4c-105">Methods</span></span>  
  
|<span data-ttu-id="7db4c-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="7db4c-106">Method</span></span>|<span data-ttu-id="7db4c-107">Description</span><span class="sxs-lookup"><span data-stu-id="7db4c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7db4c-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="7db4c-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="7db4c-109">Obtient un énumérateur pour tous les types Windows Runtime mis en cache.</span><span class="sxs-lookup"><span data-stu-id="7db4c-109">Gets an enumerator for all cached Windows Runtime types.</span></span>|  
|[<span data-ttu-id="7db4c-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="7db4c-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="7db4c-111">Obtient un énumérateur pour les types Windows Runtime mis en cache dans un domaine d’application en fonction de leurs identificateurs de l’interface.</span><span class="sxs-lookup"><span data-stu-id="7db4c-111">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7db4c-112">Notes</span><span class="sxs-lookup"><span data-stu-id="7db4c-112">Remarks</span></span>  
 <span data-ttu-id="7db4c-113">Cette interface est destinée à être utilisée par un débogueur conjointement avec un appel à la fonction d’évaluation `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span><span class="sxs-lookup"><span data-stu-id="7db4c-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="7db4c-114">Lorsque la méthode récupère les identificateurs d’interface pris en charge par un objet de serveur Windows Runtime, le débogueur peut utiliser les méthodes définies dans cette interface pour le mappage des types managés qui correspondent à ces interfaces.</span><span class="sxs-lookup"><span data-stu-id="7db4c-114">When the method retrieves the interface identifiers supported by a Windows Runtime server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="7db4c-115">Pour récupérer une instance de cette interface, exécutez `QueryInterface` sur une instance de l’interface ICorDebugAppDomain ou ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="7db4c-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7db4c-116">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="7db4c-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7db4c-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7db4c-117">Requirements</span></span>  
 <span data-ttu-id="7db4c-118">**Plateformes :** Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="7db4c-118">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="7db4c-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7db4c-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7db4c-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7db4c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7db4c-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7db4c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7db4c-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7db4c-122">See also</span></span>

- [<span data-ttu-id="7db4c-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="7db4c-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
