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
ms.openlocfilehash: 492d4b727ce507340fec47d30a791aa49d0cecb6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693344"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="f53aa-102">ICorPublishEnum, interface</span><span class="sxs-lookup"><span data-stu-id="f53aa-102">ICorPublishEnum Interface</span></span>

<span data-ttu-id="f53aa-103">Sert d’interface de base abstraite pour les énumérateurs utilisés dans la publication d’informations sur les processus et les domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="f53aa-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f53aa-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f53aa-104">Methods</span></span>  
  
|<span data-ttu-id="f53aa-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f53aa-105">Method</span></span>|<span data-ttu-id="f53aa-106">Description</span><span class="sxs-lookup"><span data-stu-id="f53aa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f53aa-107">Clone, méthode</span><span class="sxs-lookup"><span data-stu-id="f53aa-107">Clone Method</span></span>](icorpublishenum-clone-method.md)|<span data-ttu-id="f53aa-108">Crée une copie de cet objet `ICorPublishEnum`.</span><span class="sxs-lookup"><span data-stu-id="f53aa-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="f53aa-109">GetCount, méthode</span><span class="sxs-lookup"><span data-stu-id="f53aa-109">GetCount Method</span></span>](icorpublishenum-getcount-method.md)|<span data-ttu-id="f53aa-110">Obtient le nombre d’éléments dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="f53aa-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="f53aa-111">Reset, méthode</span><span class="sxs-lookup"><span data-stu-id="f53aa-111">Reset Method</span></span>](icorpublishenum-reset-method.md)|<span data-ttu-id="f53aa-112">Déplace le curseur de au début de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="f53aa-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="f53aa-113">Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="f53aa-113">Skip Method</span></span>](icorpublishenum-skip-method.md)|<span data-ttu-id="f53aa-114">Déplace le curseur vers l’avant dans l’énumération d’après le nombre d’éléments spécifié.</span><span class="sxs-lookup"><span data-stu-id="f53aa-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f53aa-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="f53aa-115">Remarks</span></span>  

 <span data-ttu-id="f53aa-116">Les énumérateurs suivants dérivent de `ICorPublishEnum` :</span><span class="sxs-lookup"><span data-stu-id="f53aa-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
- [<span data-ttu-id="f53aa-117">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="f53aa-117">ICorPublishAppDomainEnum</span></span>](icorpublishappdomainenum-interface.md)  
  
- [<span data-ttu-id="f53aa-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="f53aa-118">ICorPublishProcessEnum</span></span>](icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="f53aa-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f53aa-119">Requirements</span></span>  

 <span data-ttu-id="f53aa-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f53aa-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f53aa-121">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="f53aa-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f53aa-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f53aa-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f53aa-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f53aa-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f53aa-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f53aa-124">See also</span></span>

- [<span data-ttu-id="f53aa-125">CorpubPublish (coclasse)</span><span class="sxs-lookup"><span data-stu-id="f53aa-125">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
- [<span data-ttu-id="f53aa-126">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f53aa-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
