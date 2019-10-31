---
title: ICorDebugAssembly3, interface
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: 930101f6cd4ebb9215d6420f774b8e066c54a4f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095366"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="d1f5f-102">ICorDebugAssembly3, interface</span><span class="sxs-lookup"><span data-stu-id="d1f5f-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="d1f5f-103">Étend logiquement l’interface ICorDebugAssembly pour assurer la prise en charge des assemblys de conteneur et de leurs assemblys contenus.</span><span class="sxs-lookup"><span data-stu-id="d1f5f-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d1f5f-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d1f5f-104">Methods</span></span>  
  
|<span data-ttu-id="d1f5f-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d1f5f-105">Method</span></span>|<span data-ttu-id="d1f5f-106">Description</span><span class="sxs-lookup"><span data-stu-id="d1f5f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d1f5f-107">EnumerateContainedAssemblies, méthode</span><span class="sxs-lookup"><span data-stu-id="d1f5f-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="d1f5f-108">Obtient un énumérateur pour les assemblys contenus dans cet assembly.</span><span class="sxs-lookup"><span data-stu-id="d1f5f-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="d1f5f-109">GetContainerAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="d1f5f-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="d1f5f-110">Retourne l'assembly conteneur de cet objet `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="d1f5f-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1f5f-111">Notes</span><span class="sxs-lookup"><span data-stu-id="d1f5f-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1f5f-112">L'interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d1f5f-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="d1f5f-113">Une tentative d'appel à `QueryInterface` pour récupérer un pointeur d'interface retourne `E_NOINTERFACE` pour les scénarios ICorDebug en dehors de .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d1f5f-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1f5f-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="d1f5f-114">Requirements</span></span>  
 <span data-ttu-id="d1f5f-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1f5f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1f5f-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1f5f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1f5f-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1f5f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1f5f-118">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1f5f-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1f5f-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1f5f-119">See also</span></span>

- [<span data-ttu-id="d1f5f-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d1f5f-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d1f5f-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="d1f5f-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
