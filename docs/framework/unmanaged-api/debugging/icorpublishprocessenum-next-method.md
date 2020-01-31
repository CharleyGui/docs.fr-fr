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
ms.openlocfilehash: 084af87acd73ef65739ba69ef2bd66d10d7c27c2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790510"
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="d1a29-102">ICorPublishProcessEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="d1a29-102">ICorPublishProcessEnum::Next Method</span></span>
<span data-ttu-id="d1a29-103">Obtient le nombre spécifié de processus à partir de la collection, en commençant à la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="d1a29-103">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1a29-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1a29-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1a29-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="d1a29-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="d1a29-106">dans Nombre de processus à récupérer.</span><span class="sxs-lookup"><span data-stu-id="d1a29-106">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="d1a29-107">à Pointeur vers le tableau d’objets [ICorPublishProcess](icorpublishprocess-interface.md) récupérés, chacun représentant un processus.</span><span class="sxs-lookup"><span data-stu-id="d1a29-107">[out] A pointer to the array of retrieved [ICorPublishProcess](icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d1a29-108">à Pointeur vers le nombre de processus réellement retournés.</span><span class="sxs-lookup"><span data-stu-id="d1a29-108">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="d1a29-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="d1a29-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1a29-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d1a29-110">Requirements</span></span>  
 <span data-ttu-id="d1a29-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1a29-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1a29-112">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="d1a29-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d1a29-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1a29-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1a29-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1a29-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1a29-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1a29-115">See also</span></span>

- [<span data-ttu-id="d1a29-116">ICorPublishProcessEnum, interface</span><span class="sxs-lookup"><span data-stu-id="d1a29-116">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)
