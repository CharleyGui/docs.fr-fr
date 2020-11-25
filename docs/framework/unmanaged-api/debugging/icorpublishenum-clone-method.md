---
title: ICorPublishEnum::Clone, méthode
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Clone
helpviewer_keywords:
- Clone method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::Clone method [.NET Framework debugging]
ms.assetid: c9a26ea3-b8eb-4b8e-854f-9a2ca26b3b39
topic_type:
- apiref
ms.openlocfilehash: 44ecba99999d04603477f411e68834548f6a7cda
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693540"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="b6aa6-102">ICorPublishEnum::Clone, méthode</span><span class="sxs-lookup"><span data-stu-id="b6aa6-102">ICorPublishEnum::Clone Method</span></span>

<span data-ttu-id="b6aa6-103">Crée une copie de cet objet [ICorPublishEnum](icorpublishenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b6aa6-103">Creates a copy of this [ICorPublishEnum](icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6aa6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6aa6-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6aa6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b6aa6-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="b6aa6-106">à Pointeur vers l’adresse d’un `ICorPublishEnum` objet qui est une copie de cet `ICorPublishEnum` objet.</span><span class="sxs-lookup"><span data-stu-id="b6aa6-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6aa6-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b6aa6-107">Requirements</span></span>  

 <span data-ttu-id="b6aa6-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6aa6-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6aa6-109">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="b6aa6-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b6aa6-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6aa6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6aa6-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6aa6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6aa6-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6aa6-112">See also</span></span>

- [<span data-ttu-id="b6aa6-113">ICorPublishEnum, interface</span><span class="sxs-lookup"><span data-stu-id="b6aa6-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
