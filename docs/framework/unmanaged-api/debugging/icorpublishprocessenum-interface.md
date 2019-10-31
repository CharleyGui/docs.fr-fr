---
title: ICorPublishProcessEnum, interface
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
ms.openlocfilehash: 3a7267548a957d403cfe02aa3d800a410c14b82a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103418"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="b6aac-102">ICorPublishProcessEnum, interface</span><span class="sxs-lookup"><span data-stu-id="b6aac-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="b6aac-103">Sous-classe de l’interface [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) qui fournit des méthodes pour parcourir une collection d’objets [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b6aac-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b6aac-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b6aac-104">Methods</span></span>  
  
|<span data-ttu-id="b6aac-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="b6aac-105">Method</span></span>|<span data-ttu-id="b6aac-106">Description</span><span class="sxs-lookup"><span data-stu-id="b6aac-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b6aac-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="b6aac-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="b6aac-108">Obtient le nombre spécifié d’instances de `ICorPublishProcess` de la collection, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="b6aac-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6aac-109">Notes</span><span class="sxs-lookup"><span data-stu-id="b6aac-109">Remarks</span></span>  
 <span data-ttu-id="b6aac-110">L’interface `ICorPublishProcessEnum` implémente les méthodes de l’interface abstraite, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b6aac-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="b6aac-111">Une instance `ICorPublishProcessEnum` est créée par la méthode [ICorPublish :: EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b6aac-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="b6aac-112">Le parcours de la collection d’objets `ICorPublishProcess` est basé sur les critères de filtre spécifiés au moment de la création de l’instance de `ICorPublishProcessEnum`.</span><span class="sxs-lookup"><span data-stu-id="b6aac-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6aac-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="b6aac-113">Requirements</span></span>  
 <span data-ttu-id="b6aac-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6aac-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6aac-115">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="b6aac-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b6aac-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6aac-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6aac-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6aac-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6aac-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6aac-118">See also</span></span>

- [<span data-ttu-id="b6aac-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="b6aac-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b6aac-120">CorpubPublish, coclasse</span><span class="sxs-lookup"><span data-stu-id="b6aac-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
