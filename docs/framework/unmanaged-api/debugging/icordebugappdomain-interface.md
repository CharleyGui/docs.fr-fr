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
ms.openlocfilehash: 140e67417f4fad552f972a93bc8c620b440b2370
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895172"
---
# <a name="icordebugappdomain-interface"></a><span data-ttu-id="130dd-102">ICorDebugAppDomain, interface</span><span class="sxs-lookup"><span data-stu-id="130dd-102">ICorDebugAppDomain Interface</span></span>

<span data-ttu-id="130dd-103">Fournit des méthodes pour le débogage de domaines d'application.</span><span class="sxs-lookup"><span data-stu-id="130dd-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="130dd-104">Cette interface est une sous-classe de ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="130dd-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="130dd-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="130dd-105">Methods</span></span>  
  
|<span data-ttu-id="130dd-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="130dd-106">Method</span></span>|<span data-ttu-id="130dd-107">Description</span><span class="sxs-lookup"><span data-stu-id="130dd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="130dd-108">Attach, méthode</span><span class="sxs-lookup"><span data-stu-id="130dd-108">Attach Method</span></span>](icordebugappdomain-attach-method.md)|<span data-ttu-id="130dd-109">Attache le débogueur au domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="130dd-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="130dd-110">EnumerateAssemblies, méthode</span><span class="sxs-lookup"><span data-stu-id="130dd-110">EnumerateAssemblies Method</span></span>](icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="130dd-111">Obtient un énumérateur pour les assemblys dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="130dd-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="130dd-112">EnumerateBreakpoints, méthode</span><span class="sxs-lookup"><span data-stu-id="130dd-112">EnumerateBreakpoints Method</span></span>](icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="130dd-113">Obtient un énumérateur pour tous les points d’arrêt actifs dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="130dd-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="130dd-114">EnumerateSteppers, méthode</span><span class="sxs-lookup"><span data-stu-id="130dd-114">EnumerateSteppers Method</span></span>](icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="130dd-115">Obtient un énumérateur pour toutes les exécutions pas à pas actives dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="130dd-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="130dd-116">GetId, méthode</span><span class="sxs-lookup"><span data-stu-id="130dd-116">GetId Method</span></span>](icordebugappdomain-getid-method.md)|<span data-ttu-id="130dd-117">Obtient l’ID unique du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="130dd-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="130dd-118">GetModuleFromMetaDataInterface, méthode</span><span class="sxs-lookup"><span data-stu-id="130dd-118">GetModuleFromMetaDataInterface Method</span></span>](icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="130dd-119">Obtient l’objet ICorDebugModule avec l’interface de métadonnées donnée.</span><span class="sxs-lookup"><span data-stu-id="130dd-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="130dd-120">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="130dd-120">GetName Method</span></span>](icordebugappdomain-getname-method.md)|<span data-ttu-id="130dd-121">Obtient le nom du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="130dd-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="130dd-122">GetObject, méthode</span><span class="sxs-lookup"><span data-stu-id="130dd-122">GetObject Method</span></span>](icordebugappdomain-getobject-method.md)|<span data-ttu-id="130dd-123">Obtient un pointeur d’interface vers le domaine d’application common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="130dd-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="130dd-124">GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="130dd-124">GetProcess Method</span></span>](icordebugappdomain-getprocess-method.md)|<span data-ttu-id="130dd-125">Obtient le processus qui contient le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="130dd-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="130dd-126">IsAttached, méthode</span><span class="sxs-lookup"><span data-stu-id="130dd-126">IsAttached Method</span></span>](icordebugappdomain-isattached-method.md)|<span data-ttu-id="130dd-127">Détermine si le débogueur est attaché au domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="130dd-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="130dd-128">Notes </span><span class="sxs-lookup"><span data-stu-id="130dd-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="130dd-129">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="130dd-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="130dd-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="130dd-130">Requirements</span></span>  
 <span data-ttu-id="130dd-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="130dd-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="130dd-132">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="130dd-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="130dd-133">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="130dd-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="130dd-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="130dd-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="130dd-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="130dd-135">See also</span></span>

- [<span data-ttu-id="130dd-136">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="130dd-136">Debugging Interfaces</span></span>](debugging-interfaces.md)
