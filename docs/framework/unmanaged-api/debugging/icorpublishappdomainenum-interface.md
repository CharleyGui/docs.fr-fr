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
ms.openlocfilehash: 5b5a901bef779948467cfcc3d71a1fcd057c1aeb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693708"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="4141e-102">ICorPublishAppDomainEnum, interface</span><span class="sxs-lookup"><span data-stu-id="4141e-102">ICorPublishAppDomainEnum Interface</span></span>

<span data-ttu-id="4141e-103">Sous-classe de l’interface [ICorPublishEnum](icorpublishenum-interface.md) qui fournit des méthodes pour parcourir une collection d’objets [ICorPublishAppDomain](icorpublishappdomain-interface.md) qui existent actuellement dans un processus.</span><span class="sxs-lookup"><span data-stu-id="4141e-103">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4141e-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4141e-104">Methods</span></span>  
  
|<span data-ttu-id="4141e-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="4141e-105">Method</span></span>|<span data-ttu-id="4141e-106">Description</span><span class="sxs-lookup"><span data-stu-id="4141e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4141e-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="4141e-107">Next Method</span></span>](icorpublishappdomainenum-next-method.md)|<span data-ttu-id="4141e-108">Obtient le nombre d' `ICorPublishAppDomain` instances spécifié à partir de la collection, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="4141e-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4141e-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="4141e-109">Remarks</span></span>  

 <span data-ttu-id="4141e-110">L' `ICorPublishAppDomainEnum` interface implémente les méthodes de l’interface abstraite, [ICorPublishEnum](icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="4141e-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4141e-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4141e-111">Requirements</span></span>  

 <span data-ttu-id="4141e-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4141e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4141e-113">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="4141e-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="4141e-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4141e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4141e-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4141e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4141e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4141e-116">See also</span></span>

- [<span data-ttu-id="4141e-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="4141e-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4141e-118">CorpubPublish (coclasse)</span><span class="sxs-lookup"><span data-stu-id="4141e-118">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
