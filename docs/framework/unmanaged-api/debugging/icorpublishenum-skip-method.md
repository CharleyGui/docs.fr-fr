---
title: ICorPublishEnum::Skip, méthode
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Skip
helpviewer_keywords:
- ICorPublishEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 1680ec06-4ab0-447e-93ad-cdb8693fde5c
topic_type:
- apiref
ms.openlocfilehash: bd62fb38352022f69c45d2a5921973cfbec1c6e4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790591"
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="b5b03-102">ICorPublishEnum::Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="b5b03-102">ICorPublishEnum::Skip Method</span></span>
<span data-ttu-id="b5b03-103">Déplace le curseur vers l’avant dans l’énumération d’après le nombre d’éléments spécifié.</span><span class="sxs-lookup"><span data-stu-id="b5b03-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5b03-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5b03-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5b03-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="b5b03-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b5b03-106">dans Nombre d’éléments par lequel déplacer le curseur vers l’avant.</span><span class="sxs-lookup"><span data-stu-id="b5b03-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5b03-107">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="b5b03-107">Requirements</span></span>  
 <span data-ttu-id="b5b03-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5b03-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5b03-109">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="b5b03-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b5b03-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5b03-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5b03-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5b03-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5b03-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5b03-112">See also</span></span>

- [<span data-ttu-id="b5b03-113">ICorPublishEnum, interface</span><span class="sxs-lookup"><span data-stu-id="b5b03-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
