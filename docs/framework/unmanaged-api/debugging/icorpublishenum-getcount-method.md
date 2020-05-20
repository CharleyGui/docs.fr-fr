---
title: ICorPublishEnum::GetCount, méthode
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::GetCount
helpviewer_keywords:
- GetCount method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::GetCount method [.NET Framework debugging]
ms.assetid: d228f684-2be3-4029-93ae-31fe02213c1f
topic_type:
- apiref
ms.openlocfilehash: 7ed4236187fab1c1e81be9ddcdff1f1852e38f70
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421187"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="0e135-102">ICorPublishEnum::GetCount, méthode</span><span class="sxs-lookup"><span data-stu-id="0e135-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="0e135-103">Obtient le nombre d’éléments dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="0e135-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e135-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e135-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e135-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0e135-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="0e135-106">à Pointeur vers le nombre d’éléments dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="0e135-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e135-107">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="0e135-107">Requirements</span></span>  
 <span data-ttu-id="0e135-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e135-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e135-109">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="0e135-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="0e135-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e135-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e135-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e135-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e135-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e135-112">See also</span></span>

- [<span data-ttu-id="0e135-113">ICorPublishEnum, interface</span><span class="sxs-lookup"><span data-stu-id="0e135-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
