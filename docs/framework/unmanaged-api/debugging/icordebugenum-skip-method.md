---
title: ICorDebugEnum::Skip, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Skip
helpviewer_keywords:
- ICorDebugEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: e925d88a-67a5-4f76-88b8-09cedeed0232
topic_type:
- apiref
ms.openlocfilehash: ae88336b9640b68b97522d252b3e8334c20ed9bc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705863"
---
# <a name="icordebugenumskip-method"></a><span data-ttu-id="bcdef-102">ICorDebugEnum::Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="bcdef-102">ICorDebugEnum::Skip Method</span></span>

<span data-ttu-id="bcdef-103">Déplace le curseur vers l’avant dans l’énumération d’après le nombre d’éléments spécifié.</span><span class="sxs-lookup"><span data-stu-id="bcdef-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcdef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcdef-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcdef-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bcdef-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="bcdef-106">dans Nombre d’éléments par lequel déplacer le curseur vers l’avant.</span><span class="sxs-lookup"><span data-stu-id="bcdef-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcdef-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bcdef-107">Requirements</span></span>  

 <span data-ttu-id="bcdef-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcdef-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcdef-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bcdef-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bcdef-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bcdef-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcdef-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcdef-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcdef-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bcdef-112">See also</span></span>

- [<span data-ttu-id="bcdef-113">ICorDebugEnum, interface</span><span class="sxs-lookup"><span data-stu-id="bcdef-113">ICorDebugEnum Interface</span></span>](icordebugenum-interface1.md)
