---
title: ICorPublishAppDomainEnum, interface
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum
helpviewer_keywords:
- ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type:
- apiref
ms.openlocfilehash: cbe2aa48a8b67b0b6e88f7b5267bc70848fe3cec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140329"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="624a6-102">ICorPublishAppDomainEnum, interface</span><span class="sxs-lookup"><span data-stu-id="624a6-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="624a6-103">Sous-classe de l’interface [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) qui fournit des méthodes pour parcourir une collection d’objets [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) qui existent actuellement dans un processus.</span><span class="sxs-lookup"><span data-stu-id="624a6-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="624a6-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="624a6-104">Methods</span></span>  
  
|<span data-ttu-id="624a6-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="624a6-105">Method</span></span>|<span data-ttu-id="624a6-106">Description</span><span class="sxs-lookup"><span data-stu-id="624a6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="624a6-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="624a6-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="624a6-108">Obtient le nombre spécifié d’instances de `ICorPublishAppDomain` de la collection, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="624a6-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="624a6-109">Notes</span><span class="sxs-lookup"><span data-stu-id="624a6-109">Remarks</span></span>  
 <span data-ttu-id="624a6-110">L’interface `ICorPublishAppDomainEnum` implémente les méthodes de l’interface abstraite, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="624a6-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="624a6-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="624a6-111">Requirements</span></span>  
 <span data-ttu-id="624a6-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="624a6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="624a6-113">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="624a6-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="624a6-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="624a6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="624a6-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="624a6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="624a6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="624a6-116">See also</span></span>

- [<span data-ttu-id="624a6-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="624a6-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="624a6-118">CorpubPublish, coclasse</span><span class="sxs-lookup"><span data-stu-id="624a6-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
