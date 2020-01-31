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
ms.openlocfilehash: 188ff8feabd704d828256a09aca20f9db2227f2c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790509"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="131d4-102">ICorPublishProcessEnum, interface</span><span class="sxs-lookup"><span data-stu-id="131d4-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="131d4-103">Sous-classe de l’interface [ICorPublishEnum](icorpublishenum-interface.md) qui fournit des méthodes pour parcourir une collection d’objets [ICorPublishProcess](icorpublishprocess-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="131d4-103">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="131d4-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="131d4-104">Methods</span></span>  
  
|<span data-ttu-id="131d4-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="131d4-105">Method</span></span>|<span data-ttu-id="131d4-106">Description</span><span class="sxs-lookup"><span data-stu-id="131d4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="131d4-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="131d4-107">Next Method</span></span>](icorpublishprocessenum-next-method.md)|<span data-ttu-id="131d4-108">Obtient le nombre spécifié d’instances de `ICorPublishProcess` de la collection, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="131d4-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="131d4-109">Notes</span><span class="sxs-lookup"><span data-stu-id="131d4-109">Remarks</span></span>  
 <span data-ttu-id="131d4-110">L’interface `ICorPublishProcessEnum` implémente les méthodes de l’interface abstraite, [ICorPublishEnum](icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="131d4-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="131d4-111">Une instance `ICorPublishProcessEnum` est créée par la méthode [ICorPublish :: EnumProcesses](icorpublish-enumprocesses-method.md) .</span><span class="sxs-lookup"><span data-stu-id="131d4-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="131d4-112">Le parcours de la collection d’objets `ICorPublishProcess` est basé sur les critères de filtre spécifiés au moment de la création de l’instance de `ICorPublishProcessEnum`.</span><span class="sxs-lookup"><span data-stu-id="131d4-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="131d4-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="131d4-113">Requirements</span></span>  
 <span data-ttu-id="131d4-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="131d4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="131d4-115">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="131d4-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="131d4-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="131d4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="131d4-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="131d4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="131d4-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="131d4-118">See also</span></span>

- [<span data-ttu-id="131d4-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="131d4-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="131d4-120">CorpubPublish, coclasse</span><span class="sxs-lookup"><span data-stu-id="131d4-120">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
