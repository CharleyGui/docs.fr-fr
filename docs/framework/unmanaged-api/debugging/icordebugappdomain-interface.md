---
title: ICorDebugAppDomain, interface
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
ms.openlocfilehash: da7c0fb472df89d94fa702a13eff968a4c7e68e3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785039"
---
# <a name="icordebugappdomain-interface"></a><span data-ttu-id="a7307-102">ICorDebugAppDomain, interface</span><span class="sxs-lookup"><span data-stu-id="a7307-102">ICorDebugAppDomain Interface</span></span>

<span data-ttu-id="a7307-103">Fournit des méthodes pour le débogage de domaines d'application.</span><span class="sxs-lookup"><span data-stu-id="a7307-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="a7307-104">Cette interface est une sous-classe de ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="a7307-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a7307-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a7307-105">Methods</span></span>  
  
|<span data-ttu-id="a7307-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="a7307-106">Method</span></span>|<span data-ttu-id="a7307-107">Description</span><span class="sxs-lookup"><span data-stu-id="a7307-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a7307-108">Attach, méthode</span><span class="sxs-lookup"><span data-stu-id="a7307-108">Attach Method</span></span>](icordebugappdomain-attach-method.md)|<span data-ttu-id="a7307-109">Attache le débogueur au domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="a7307-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="a7307-110">EnumerateAssemblies, méthode</span><span class="sxs-lookup"><span data-stu-id="a7307-110">EnumerateAssemblies Method</span></span>](icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="a7307-111">Obtient un énumérateur pour les assemblys dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="a7307-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="a7307-112">EnumerateBreakpoints, méthode</span><span class="sxs-lookup"><span data-stu-id="a7307-112">EnumerateBreakpoints Method</span></span>](icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="a7307-113">Obtient un énumérateur pour tous les points d’arrêt actifs dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="a7307-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="a7307-114">EnumerateSteppers, méthode</span><span class="sxs-lookup"><span data-stu-id="a7307-114">EnumerateSteppers Method</span></span>](icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="a7307-115">Obtient un énumérateur pour toutes les exécutions pas à pas actives dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="a7307-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="a7307-116">GetID, méthode</span><span class="sxs-lookup"><span data-stu-id="a7307-116">GetId Method</span></span>](icordebugappdomain-getid-method.md)|<span data-ttu-id="a7307-117">Obtient l’ID unique du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="a7307-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="a7307-118">GetModuleFromMetaDataInterface, méthode</span><span class="sxs-lookup"><span data-stu-id="a7307-118">GetModuleFromMetaDataInterface Method</span></span>](icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="a7307-119">Obtient l’objet ICorDebugModule avec l’interface de métadonnées donnée.</span><span class="sxs-lookup"><span data-stu-id="a7307-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="a7307-120">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="a7307-120">GetName Method</span></span>](icordebugappdomain-getname-method.md)|<span data-ttu-id="a7307-121">Obtient le nom du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="a7307-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="a7307-122">GetObject, méthode</span><span class="sxs-lookup"><span data-stu-id="a7307-122">GetObject Method</span></span>](icordebugappdomain-getobject-method.md)|<span data-ttu-id="a7307-123">Obtient un pointeur d’interface vers le domaine d’application common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="a7307-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="a7307-124">GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="a7307-124">GetProcess Method</span></span>](icordebugappdomain-getprocess-method.md)|<span data-ttu-id="a7307-125">Obtient le processus qui contient le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="a7307-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="a7307-126">IsAttached, méthode</span><span class="sxs-lookup"><span data-stu-id="a7307-126">IsAttached Method</span></span>](icordebugappdomain-isattached-method.md)|<span data-ttu-id="a7307-127">Détermine si le débogueur est attaché au domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="a7307-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7307-128">Notes</span><span class="sxs-lookup"><span data-stu-id="a7307-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7307-129">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="a7307-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7307-130">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="a7307-130">Requirements</span></span>  
 <span data-ttu-id="a7307-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7307-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7307-132">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7307-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7307-133">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7307-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7307-134">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7307-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7307-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7307-135">See also</span></span>

- [<span data-ttu-id="a7307-136">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="a7307-136">Debugging Interfaces</span></span>](debugging-interfaces.md)
