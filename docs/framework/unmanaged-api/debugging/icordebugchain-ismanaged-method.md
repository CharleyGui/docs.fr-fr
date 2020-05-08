---
title: ICorDebugChain::IsManaged, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugChain.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::IsManaged
helpviewer_keywords:
- ICorDebugChain::IsManaged method [.NET Framework debugging]
- IsManaged method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 17b389a0-1a4d-4e8a-8613-9bc1769930f9
topic_type:
- apiref
ms.openlocfilehash: 55036fcdbd186f91c0e94fb05f3023cf614751f7
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894249"
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="a4312-102">ICorDebugChain::IsManaged, méthode</span><span class="sxs-lookup"><span data-stu-id="a4312-102">ICorDebugChain::IsManaged Method</span></span>
<span data-ttu-id="a4312-103">Obtient une valeur qui indique si cette chaîne exécute du code managé.</span><span class="sxs-lookup"><span data-stu-id="a4312-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4312-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4312-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4312-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a4312-105">Parameters</span></span>  
 `pManaged`  
 <span data-ttu-id="a4312-106">à `true` si cette chaîne exécute du code managé ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="a4312-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4312-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a4312-107">Requirements</span></span>  
 <span data-ttu-id="a4312-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4312-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4312-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a4312-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4312-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4312-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4312-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4312-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
