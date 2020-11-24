---
title: ICorDebugAssembly3, interface
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: 0260267a05a880fbb3ac48325e55deff326f5f87
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688365"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="10dad-102">ICorDebugAssembly3, interface</span><span class="sxs-lookup"><span data-stu-id="10dad-102">ICorDebugAssembly3 Interface</span></span>

<span data-ttu-id="10dad-103">Étend logiquement l'interface ICorDebugAssembly pour prendre en charge les assemblys conteneurs et les assemblys qu'ils contiennent.</span><span class="sxs-lookup"><span data-stu-id="10dad-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="10dad-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="10dad-104">Methods</span></span>  
  
|<span data-ttu-id="10dad-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="10dad-105">Method</span></span>|<span data-ttu-id="10dad-106">Description</span><span class="sxs-lookup"><span data-stu-id="10dad-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="10dad-107">EnumerateContainedAssemblies, méthode</span><span class="sxs-lookup"><span data-stu-id="10dad-107">EnumerateContainedAssemblies Method</span></span>](icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="10dad-108">Obtient un énumérateur pour les assemblys contenus dans cet assembly.</span><span class="sxs-lookup"><span data-stu-id="10dad-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="10dad-109">GetContainerAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="10dad-109">GetContainerAssembly Method</span></span>](icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="10dad-110">Retourne l'assembly conteneur de cet objet `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="10dad-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10dad-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="10dad-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="10dad-112">L'interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="10dad-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="10dad-113">Une tentative d'appel à `QueryInterface` pour récupérer un pointeur d'interface retourne `E_NOINTERFACE` pour les scénarios ICorDebug en dehors de .NET Native.</span><span class="sxs-lookup"><span data-stu-id="10dad-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10dad-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="10dad-114">Requirements</span></span>  

 <span data-ttu-id="10dad-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10dad-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10dad-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10dad-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10dad-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10dad-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10dad-118">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10dad-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10dad-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10dad-119">See also</span></span>

- [<span data-ttu-id="10dad-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="10dad-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="10dad-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="10dad-121">Debugging</span></span>](index.md)
