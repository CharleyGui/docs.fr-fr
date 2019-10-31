---
title: ICorPublishProcessEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum::Next
helpviewer_keywords:
- ICorPublishProcessEnum::Next method [.NET Framework debugging]
- Next method, ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: 6c399f37-1e38-4ca1-b70d-8ae41f7228b7
topic_type:
- apiref
ms.openlocfilehash: d79b642735543ff84f6211fe5ca2e5b424be1f2e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103446"
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="19efa-102">ICorPublishProcessEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="19efa-102">ICorPublishProcessEnum::Next Method</span></span>
<span data-ttu-id="19efa-103">Obtient le nombre spécifié de processus à partir de la collection, en commençant à la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="19efa-103">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19efa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19efa-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19efa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="19efa-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="19efa-106">dans Nombre de processus à récupérer.</span><span class="sxs-lookup"><span data-stu-id="19efa-106">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="19efa-107">à Pointeur vers le tableau d’objets [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) récupérés, chacun représentant un processus.</span><span class="sxs-lookup"><span data-stu-id="19efa-107">[out] A pointer to the array of retrieved [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="19efa-108">à Pointeur vers le nombre de processus réellement retournés.</span><span class="sxs-lookup"><span data-stu-id="19efa-108">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="19efa-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="19efa-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19efa-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="19efa-110">Requirements</span></span>  
 <span data-ttu-id="19efa-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19efa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19efa-112">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="19efa-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="19efa-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19efa-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19efa-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19efa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19efa-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19efa-115">See also</span></span>

- [<span data-ttu-id="19efa-116">ICorPublishProcessEnum, interface</span><span class="sxs-lookup"><span data-stu-id="19efa-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)
