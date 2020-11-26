---
title: IXCLRDataProcess, interface
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess Interface
helpviewer.keywords:
- IXCLRDataProcess Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 376ec2b840bc17c79ed1f27c17a8ddd22c37a0f4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245351"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="bb532-102">IXCLRDataProcess, interface</span><span class="sxs-lookup"><span data-stu-id="bb532-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="bb532-103">Fournit des méthodes pour interroger les informations relatives à un processus.</span><span class="sxs-lookup"><span data-stu-id="bb532-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="bb532-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="bb532-104">Methods</span></span>

| <span data-ttu-id="bb532-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="bb532-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="bb532-106">Description</span><span class="sxs-lookup"><span data-stu-id="bb532-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="bb532-107">GetRuntimeNameByAddress</span><span class="sxs-lookup"><span data-stu-id="bb532-107">GetRuntimeNameByAddress</span></span>](ixclrdataprocess-getruntimenamebyaddress-method.md)                     | <span data-ttu-id="bb532-108">Obtient un nom pour l’adresse donnée.</span><span class="sxs-lookup"><span data-stu-id="bb532-108">Gets a name for the given address.</span></span>                                                               |
| [<span data-ttu-id="bb532-109">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="bb532-109">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="bb532-110">Obtient un `AppDomain` dans un processus par son ID unique.</span><span class="sxs-lookup"><span data-stu-id="bb532-110">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="bb532-111">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="bb532-111">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="bb532-112">Fournit un handle pour énumérer les modules d’un processus.</span><span class="sxs-lookup"><span data-stu-id="bb532-112">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="bb532-113">EnumModule</span><span class="sxs-lookup"><span data-stu-id="bb532-113">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="bb532-114">Énumère les modules de ce processus.</span><span class="sxs-lookup"><span data-stu-id="bb532-114">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="bb532-115">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="bb532-115">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="bb532-116">Libère les ressources utilisées par les itérateurs internes utilisés pendant l’énumération des modules.</span><span class="sxs-lookup"><span data-stu-id="bb532-116">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="bb532-117">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="bb532-117">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="bb532-118">Fournit un handle pour énumérer les instances de méthode de `AppDomain` à partir d’une adresse donnée.</span><span class="sxs-lookup"><span data-stu-id="bb532-118">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="bb532-119">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="bb532-119">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="bb532-120">Énumère les instances de méthode de ce processus à partir d’un décalage d’adresse.</span><span class="sxs-lookup"><span data-stu-id="bb532-120">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="bb532-121">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="bb532-121">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="bb532-122">Libère les ressources utilisées par les itérateurs internes utilisés pendant l’énumération d’instance.</span><span class="sxs-lookup"><span data-stu-id="bb532-122">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="bb532-123">Notes</span><span class="sxs-lookup"><span data-stu-id="bb532-123">Remarks</span></span>

<span data-ttu-id="bb532-124">Cette interface se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="bb532-124">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="bb532-125">Toutefois, il s’agit d’une interface COM qui dérive de `IUnknown` avec `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` un GUID qui peut être obtenu par le biais des mécanismes com habituels.</span><span class="sxs-lookup"><span data-stu-id="bb532-125">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="bb532-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bb532-126">Requirements</span></span>

<span data-ttu-id="bb532-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb532-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="bb532-128">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="bb532-128">**Header:** None</span></span>  
<span data-ttu-id="bb532-129">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="bb532-129">**Library:** None</span></span>  
<span data-ttu-id="bb532-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bb532-130">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="bb532-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb532-131">See also</span></span>

- [<span data-ttu-id="bb532-132">Débogage</span><span class="sxs-lookup"><span data-stu-id="bb532-132">Debugging</span></span>](index.md)
- [<span data-ttu-id="bb532-133">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="bb532-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
