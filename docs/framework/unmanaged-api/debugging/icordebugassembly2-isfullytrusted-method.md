---
title: ICorDebugAssembly2::IsFullyTrusted, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2.IsFullyTrusted
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type:
- apiref
ms.openlocfilehash: dd82709064fe7f7d912d93f4b3f0248769f02b9e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894889"
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="ba0e2-102">ICorDebugAssembly2::IsFullyTrusted, méthode</span><span class="sxs-lookup"><span data-stu-id="ba0e2-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>
<span data-ttu-id="ba0e2-103">Obtient une valeur qui indique si le système de sécurité du runtime a accordé un niveau de confiance totale à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ba0e2-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba0e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba0e2-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba0e2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ba0e2-105">Parameters</span></span>  
 `pbFullyTrusted`  
 <span data-ttu-id="ba0e2-106">à `true` si le système de sécurité du runtime a accordé une confiance totale à l’assembly ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="ba0e2-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba0e2-107">Notes </span><span class="sxs-lookup"><span data-stu-id="ba0e2-107">Remarks</span></span>  
 <span data-ttu-id="ba0e2-108">Cette méthode retourne un HRESULT de CORDBG_E_NOTREADY si la stratégie de sécurité de l’assembly n’a pas encore été résolue, autrement dit, si aucun code de l’assembly n’a encore été exécuté.</span><span class="sxs-lookup"><span data-stu-id="ba0e2-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba0e2-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ba0e2-109">Requirements</span></span>  
 <span data-ttu-id="ba0e2-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba0e2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba0e2-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba0e2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba0e2-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba0e2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba0e2-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba0e2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
