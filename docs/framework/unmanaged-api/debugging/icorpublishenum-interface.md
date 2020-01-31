---
title: ICorPublishEnum, interface
ms.date: 03/30/2017
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
ms.openlocfilehash: f54bb99df60d7b3fb7bb98de75fbae210597e45c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790625"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="17f35-102">ICorPublishEnum, interface</span><span class="sxs-lookup"><span data-stu-id="17f35-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="17f35-103">Sert d’interface de base abstraite pour les énumérateurs utilisés dans la publication d’informations sur les processus et les domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="17f35-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="17f35-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="17f35-104">Methods</span></span>  
  
|<span data-ttu-id="17f35-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="17f35-105">Method</span></span>|<span data-ttu-id="17f35-106">Description</span><span class="sxs-lookup"><span data-stu-id="17f35-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="17f35-107">Clone, méthode</span><span class="sxs-lookup"><span data-stu-id="17f35-107">Clone Method</span></span>](icorpublishenum-clone-method.md)|<span data-ttu-id="17f35-108">Crée une copie de cet objet `ICorPublishEnum`.</span><span class="sxs-lookup"><span data-stu-id="17f35-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="17f35-109">GetCount, méthode</span><span class="sxs-lookup"><span data-stu-id="17f35-109">GetCount Method</span></span>](icorpublishenum-getcount-method.md)|<span data-ttu-id="17f35-110">Obtient le nombre d’éléments dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="17f35-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="17f35-111">Reset, méthode</span><span class="sxs-lookup"><span data-stu-id="17f35-111">Reset Method</span></span>](icorpublishenum-reset-method.md)|<span data-ttu-id="17f35-112">Déplace le curseur de au début de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="17f35-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="17f35-113">Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="17f35-113">Skip Method</span></span>](icorpublishenum-skip-method.md)|<span data-ttu-id="17f35-114">Déplace le curseur vers l’avant dans l’énumération d’après le nombre d’éléments spécifié.</span><span class="sxs-lookup"><span data-stu-id="17f35-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17f35-115">Notes</span><span class="sxs-lookup"><span data-stu-id="17f35-115">Remarks</span></span>  
 <span data-ttu-id="17f35-116">Les énumérateurs suivants dérivent de `ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="17f35-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
- [<span data-ttu-id="17f35-117">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="17f35-117">ICorPublishAppDomainEnum</span></span>](icorpublishappdomainenum-interface.md)  
  
- [<span data-ttu-id="17f35-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="17f35-118">ICorPublishProcessEnum</span></span>](icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="17f35-119">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="17f35-119">Requirements</span></span>  
 <span data-ttu-id="17f35-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17f35-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17f35-121">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="17f35-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="17f35-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17f35-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17f35-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17f35-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17f35-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17f35-124">See also</span></span>

- [<span data-ttu-id="17f35-125">CorpubPublish, coclasse</span><span class="sxs-lookup"><span data-stu-id="17f35-125">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
- [<span data-ttu-id="17f35-126">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="17f35-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
