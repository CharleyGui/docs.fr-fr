---
title: ICorDebugAssembly3, interface
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca77360c36ff2cdce7ee47d5c3883dd824c6cef8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959326"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="3ea44-102">ICorDebugAssembly3, interface</span><span class="sxs-lookup"><span data-stu-id="3ea44-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="3ea44-103">Étend logiquement l’interface ICorDebugAssembly pour assurer la prise en charge des assemblys de conteneur et de leurs assemblys contenus.</span><span class="sxs-lookup"><span data-stu-id="3ea44-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3ea44-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3ea44-104">Methods</span></span>  
  
|<span data-ttu-id="3ea44-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="3ea44-105">Method</span></span>|<span data-ttu-id="3ea44-106">Description</span><span class="sxs-lookup"><span data-stu-id="3ea44-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3ea44-107">EnumerateContainedAssemblies, méthode</span><span class="sxs-lookup"><span data-stu-id="3ea44-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="3ea44-108">Obtient un énumérateur pour les assemblys contenus dans cet assembly.</span><span class="sxs-lookup"><span data-stu-id="3ea44-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="3ea44-109">GetContainerAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="3ea44-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="3ea44-110">Retourne l'assembly conteneur de cet objet `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="3ea44-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ea44-111">Notes</span><span class="sxs-lookup"><span data-stu-id="3ea44-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ea44-112">L'interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3ea44-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="3ea44-113">Une tentative d'appel à `QueryInterface` pour récupérer un pointeur d'interface retourne `E_NOINTERFACE` pour les scénarios ICorDebug en dehors de .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3ea44-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ea44-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3ea44-114">Requirements</span></span>  
 <span data-ttu-id="3ea44-115">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ea44-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ea44-116">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3ea44-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ea44-117">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ea44-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ea44-118">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ea44-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ea44-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ea44-119">See also</span></span>

- [<span data-ttu-id="3ea44-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="3ea44-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3ea44-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="3ea44-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
