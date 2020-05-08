---
title: ICorDebugEnum::GetCount, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::GetCount
helpviewer_keywords:
- ICorDebugEnum::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: d8a74304-1cb2-4977-a21d-e1af48c563ff
topic_type:
- apiref
ms.openlocfilehash: 90ba690897abced2d4f6282eedef91712d8ceeca
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976341"
---
# <a name="icordebugenumgetcount-method"></a><span data-ttu-id="2597a-102">ICorDebugEnum::GetCount, méthode</span><span class="sxs-lookup"><span data-stu-id="2597a-102">ICorDebugEnum::GetCount Method</span></span>
<span data-ttu-id="2597a-103">Obtient le nombre d’éléments dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="2597a-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2597a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2597a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2597a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2597a-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="2597a-106">à Pointeur vers le nombre d’éléments dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="2597a-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2597a-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2597a-107">Requirements</span></span>  
 <span data-ttu-id="2597a-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2597a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2597a-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2597a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2597a-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2597a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2597a-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2597a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
