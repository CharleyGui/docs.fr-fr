---
title: ICorDebugObjectEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
ms.openlocfilehash: 70514464f27d6123a4de1d5800ed016a39541287
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207556"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="df6ab-102">ICorDebugObjectEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="df6ab-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="df6ab-103">Obtient les adresses virtuelles relatives (RVA) du nombre d’objets spécifié à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="df6ab-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df6ab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df6ab-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df6ab-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="df6ab-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="df6ab-106">[in] Nombre d'objets à récupérer.</span><span class="sxs-lookup"><span data-stu-id="df6ab-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="df6ab-107">à Tableau de pointeurs, chacun pointant vers un objet CORDB_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="df6ab-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="df6ab-108">à Pointeur vers le nombre d’objets réellement retournés.</span><span class="sxs-lookup"><span data-stu-id="df6ab-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="df6ab-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="df6ab-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df6ab-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="df6ab-110">Requirements</span></span>  
 <span data-ttu-id="df6ab-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df6ab-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df6ab-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df6ab-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df6ab-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df6ab-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df6ab-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df6ab-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df6ab-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df6ab-115">See also</span></span>
