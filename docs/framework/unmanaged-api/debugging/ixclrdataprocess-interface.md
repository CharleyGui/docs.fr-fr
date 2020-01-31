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
ms.openlocfilehash: a5d707d61513b030e5968af28db3c2a606e4419b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790374"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="789b4-102">IXCLRDataProcess, interface</span><span class="sxs-lookup"><span data-stu-id="789b4-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="789b4-103">Fournit des méthodes pour interroger les informations relatives à un processus.</span><span class="sxs-lookup"><span data-stu-id="789b4-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="789b4-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="789b4-104">Methods</span></span>

| <span data-ttu-id="789b4-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="789b4-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="789b4-106">Description</span><span class="sxs-lookup"><span data-stu-id="789b4-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="789b4-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="789b4-107">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="789b4-108">Obtient un `AppDomain` dans un processus par son ID unique.</span><span class="sxs-lookup"><span data-stu-id="789b4-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="789b4-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="789b4-109">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="789b4-110">Fournit un handle pour énumérer les modules d’un processus.</span><span class="sxs-lookup"><span data-stu-id="789b4-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="789b4-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="789b4-111">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="789b4-112">Énumère les modules de ce processus.</span><span class="sxs-lookup"><span data-stu-id="789b4-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="789b4-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="789b4-113">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="789b4-114">Libère les ressources utilisées par les itérateurs internes utilisés pendant l’énumération des modules.</span><span class="sxs-lookup"><span data-stu-id="789b4-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="789b4-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="789b4-115">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="789b4-116">Fournit un handle pour énumérer les instances de méthode de `AppDomain` à partir d’une adresse donnée.</span><span class="sxs-lookup"><span data-stu-id="789b4-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="789b4-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="789b4-117">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="789b4-118">Énumère les instances de méthode de ce processus à partir d’un décalage d’adresse.</span><span class="sxs-lookup"><span data-stu-id="789b4-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="789b4-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="789b4-119">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="789b4-120">Libère les ressources utilisées par les itérateurs internes utilisés pendant l’énumération d’instance.</span><span class="sxs-lookup"><span data-stu-id="789b4-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="789b4-121">Notes</span><span class="sxs-lookup"><span data-stu-id="789b4-121">Remarks</span></span>

<span data-ttu-id="789b4-122">Cette interface se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="789b4-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="789b4-123">Toutefois, il s’agit d’une interface COM qui dérive de `IUnknown` avec GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` qui peuvent être obtenus par le biais des mécanismes COM habituels.</span><span class="sxs-lookup"><span data-stu-id="789b4-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="789b4-124">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="789b4-124">Requirements</span></span>

<span data-ttu-id="789b4-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="789b4-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="789b4-126">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="789b4-126">**Header:** None</span></span>  
<span data-ttu-id="789b4-127">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="789b4-127">**Library:** None</span></span>  
<span data-ttu-id="789b4-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="789b4-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="789b4-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="789b4-129">See also</span></span>

- [<span data-ttu-id="789b4-130">Débogage</span><span class="sxs-lookup"><span data-stu-id="789b4-130">Debugging</span></span>](index.md)
- [<span data-ttu-id="789b4-131">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="789b4-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
