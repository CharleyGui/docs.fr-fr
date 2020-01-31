---
title: ICorDebugAssembly3, interface
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: deb300ced2ff7a116bd443c9a7b10dcc0b7955ac
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784528"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="acc32-102">ICorDebugAssembly3, interface</span><span class="sxs-lookup"><span data-stu-id="acc32-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="acc32-103">Étend logiquement l'interface ICorDebugAssembly pour prendre en charge les assemblys conteneurs et les assemblys qu'ils contiennent.</span><span class="sxs-lookup"><span data-stu-id="acc32-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="acc32-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="acc32-104">Methods</span></span>  
  
|<span data-ttu-id="acc32-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="acc32-105">Method</span></span>|<span data-ttu-id="acc32-106">Description</span><span class="sxs-lookup"><span data-stu-id="acc32-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="acc32-107">EnumerateContainedAssemblies, méthode</span><span class="sxs-lookup"><span data-stu-id="acc32-107">EnumerateContainedAssemblies Method</span></span>](icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="acc32-108">Obtient un énumérateur pour les assemblys contenus dans cet assembly.</span><span class="sxs-lookup"><span data-stu-id="acc32-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="acc32-109">GetContainerAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="acc32-109">GetContainerAssembly Method</span></span>](icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="acc32-110">Retourne l'assembly conteneur de cet objet `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="acc32-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acc32-111">Notes</span><span class="sxs-lookup"><span data-stu-id="acc32-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="acc32-112">L'interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="acc32-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="acc32-113">Une tentative d'appel à `QueryInterface` pour récupérer un pointeur d'interface retourne `E_NOINTERFACE` pour les scénarios ICorDebug en dehors de .NET Native.</span><span class="sxs-lookup"><span data-stu-id="acc32-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acc32-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="acc32-114">Requirements</span></span>  
 <span data-ttu-id="acc32-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acc32-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acc32-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="acc32-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="acc32-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="acc32-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acc32-118">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acc32-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acc32-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acc32-119">See also</span></span>

- [<span data-ttu-id="acc32-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="acc32-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="acc32-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="acc32-121">Debugging</span></span>](index.md)
