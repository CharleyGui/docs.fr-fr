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
ms.openlocfilehash: c3676cb32ceaf6f241672751f0feafbd3cb83e05
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968874"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="6e6cf-102">ICorDebugAppDomain3, interface</span><span class="sxs-lookup"><span data-stu-id="6e6cf-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="6e6cf-103">Fournit des méthodes pour récupérer des informations sur les représentations managées des types de Windows Runtime actuellement chargés dans un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="6e6cf-103">Provides methods to retrieve information about the managed representations of Windows Runtime types currently loaded in an application domain.</span></span> <span data-ttu-id="6e6cf-104">Cette interface est une extension des interfaces ICorDebugAppDomain et ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="6e6cf-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e6cf-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6e6cf-105">Methods</span></span>  
  
|<span data-ttu-id="6e6cf-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="6e6cf-106">Method</span></span>|<span data-ttu-id="6e6cf-107">Description</span><span class="sxs-lookup"><span data-stu-id="6e6cf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e6cf-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="6e6cf-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="6e6cf-109">Obtient un énumérateur pour tous les types de Windows Runtime mis en cache.</span><span class="sxs-lookup"><span data-stu-id="6e6cf-109">Gets an enumerator for all cached Windows Runtime types.</span></span>|  
|[<span data-ttu-id="6e6cf-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="6e6cf-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="6e6cf-111">Obtient un énumérateur pour les types de Windows Runtime mis en cache dans un domaine d’application en fonction de leurs identificateurs d’interface.</span><span class="sxs-lookup"><span data-stu-id="6e6cf-111">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e6cf-112">Notes</span><span class="sxs-lookup"><span data-stu-id="6e6cf-112">Remarks</span></span>  
 <span data-ttu-id="6e6cf-113">Cette interface est destinée à être utilisée par un débogueur conjointement à un appel d’évaluation de fonction `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`à.</span><span class="sxs-lookup"><span data-stu-id="6e6cf-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="6e6cf-114">Quand la méthode récupère les identificateurs d’interface pris en charge par un objet Windows Runtime Server, le débogueur peut utiliser les méthodes définies dans cette interface pour les mapper aux types managés qui correspondent à ces interfaces.</span><span class="sxs-lookup"><span data-stu-id="6e6cf-114">When the method retrieves the interface identifiers supported by a Windows Runtime server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="6e6cf-115">Pour récupérer une instance de cette interface, exécutez `QueryInterface` sur une instance de l’interface ICorDebugAppDomain ou ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="6e6cf-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e6cf-116">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="6e6cf-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e6cf-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6e6cf-117">Requirements</span></span>  
 <span data-ttu-id="6e6cf-118">**Plateformes** Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="6e6cf-118">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="6e6cf-119">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6e6cf-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e6cf-120">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e6cf-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e6cf-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e6cf-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e6cf-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e6cf-122">See also</span></span>

- [<span data-ttu-id="6e6cf-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="6e6cf-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
