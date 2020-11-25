---
title: ICorDebugAssembly, interface
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly
helpviewer_keywords:
- ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type:
- apiref
ms.openlocfilehash: 821eae8ea5b4147408e9fe60d1e5b70c7936959e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696243"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="665ac-102">ICorDebugAssembly, interface</span><span class="sxs-lookup"><span data-stu-id="665ac-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="665ac-103">Représente un assembly.</span><span class="sxs-lookup"><span data-stu-id="665ac-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="665ac-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="665ac-104">Methods</span></span>  
  
|<span data-ttu-id="665ac-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="665ac-105">Method</span></span>|<span data-ttu-id="665ac-106">Description</span><span class="sxs-lookup"><span data-stu-id="665ac-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="665ac-107">EnumerateModules, méthode</span><span class="sxs-lookup"><span data-stu-id="665ac-107">EnumerateModules Method</span></span>](icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="665ac-108">Obtient un énumérateur pour les modules contenus dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="665ac-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="665ac-109">GetAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="665ac-109">GetAppDomain Method</span></span>](icordebugassembly-getappdomain-method.md)|<span data-ttu-id="665ac-110">Obtient un pointeur d’interface vers le domaine d’application qui contient cette `ICorDebugAssembly` instance.</span><span class="sxs-lookup"><span data-stu-id="665ac-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="665ac-111">GetCodeBase, méthode</span><span class="sxs-lookup"><span data-stu-id="665ac-111">GetCodeBase Method</span></span>](icordebugassembly-getcodebase-method.md)|<span data-ttu-id="665ac-112">Non implémenté dans la version actuelle du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="665ac-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="665ac-113">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="665ac-113">GetName Method</span></span>](icordebugassembly-getname-method.md)|<span data-ttu-id="665ac-114">Obtient le nom de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="665ac-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="665ac-115">GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="665ac-115">GetProcess Method</span></span>](icordebugassembly-getprocess-method.md)|<span data-ttu-id="665ac-116">Obtient l’instance ICorDebugProcess dans laquelle l’assembly est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="665ac-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="665ac-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="665ac-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="665ac-118">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="665ac-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="665ac-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="665ac-119">Requirements</span></span>  

 <span data-ttu-id="665ac-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="665ac-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="665ac-121">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="665ac-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="665ac-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="665ac-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="665ac-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="665ac-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="665ac-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="665ac-124">See also</span></span>

- [<span data-ttu-id="665ac-125">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="665ac-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
