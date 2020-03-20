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
ms.openlocfilehash: e7e53615e38d0ab76f9e7c0a753be3c13780057d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178373"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="0012e-102">IXCLRDataProcess, interface</span><span class="sxs-lookup"><span data-stu-id="0012e-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="0012e-103">Fournit des méthodes pour interroger des informations sur un processus.</span><span class="sxs-lookup"><span data-stu-id="0012e-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="0012e-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0012e-104">Methods</span></span>

| <span data-ttu-id="0012e-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="0012e-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="0012e-106">Description</span><span class="sxs-lookup"><span data-stu-id="0012e-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="0012e-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="0012e-107">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="0012e-108">Obtient `AppDomain` un dans un processus par son id unique.</span><span class="sxs-lookup"><span data-stu-id="0012e-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="0012e-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="0012e-109">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="0012e-110">Fournit une poignée pour énumérer les modules d’un processus.</span><span class="sxs-lookup"><span data-stu-id="0012e-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="0012e-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="0012e-111">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="0012e-112">Énumère les modules de ce processus.</span><span class="sxs-lookup"><span data-stu-id="0012e-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="0012e-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="0012e-113">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="0012e-114">Libère les ressources utilisées par les itérateurs internes utilisés lors du recensement du module.</span><span class="sxs-lookup"><span data-stu-id="0012e-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="0012e-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="0012e-115">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="0012e-116">Fournit une poignée pour énumérer `AppDomain` les instances de méthode de commencer à une adresse donnée.</span><span class="sxs-lookup"><span data-stu-id="0012e-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="0012e-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="0012e-117">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="0012e-118">Énumère les instances de méthode de ce processus à partir d’une compensation d’adresse.</span><span class="sxs-lookup"><span data-stu-id="0012e-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="0012e-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="0012e-119">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="0012e-120">Libère les ressources utilisées par les itérateurs internes utilisés lors du recensement par exemple.</span><span class="sxs-lookup"><span data-stu-id="0012e-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="0012e-121">Notes </span><span class="sxs-lookup"><span data-stu-id="0012e-121">Remarks</span></span>

<span data-ttu-id="0012e-122">Cette interface vit à l’intérieur du temps d’exécution et n’est pas exposée à travers des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="0012e-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="0012e-123">Cependant, c’est une interface COM `IUnknown` qui `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` dérive avec GUID qui peut être obtenue grâce aux mécanismes COM habituels.</span><span class="sxs-lookup"><span data-stu-id="0012e-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="0012e-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0012e-124">Requirements</span></span>

<span data-ttu-id="0012e-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0012e-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="0012e-126">**En-tête:** Aucun</span><span class="sxs-lookup"><span data-stu-id="0012e-126">**Header:** None</span></span>  
<span data-ttu-id="0012e-127">**Bibliothèque:** Aucun</span><span class="sxs-lookup"><span data-stu-id="0012e-127">**Library:** None</span></span>  
<span data-ttu-id="0012e-128">**.NET Versions-cadre:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0012e-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0012e-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0012e-129">See also</span></span>

- [<span data-ttu-id="0012e-130">Débogage</span><span class="sxs-lookup"><span data-stu-id="0012e-130">Debugging</span></span>](index.md)
- [<span data-ttu-id="0012e-131">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0012e-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
