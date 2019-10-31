---
title: ICorDebugAppDomain::Attach, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.Attach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::Attach
helpviewer_keywords:
- ICorDebugAppDomain::Attach method [.NET Framework debugging]
- Attach method [.NET Framework debugging]
ms.assetid: 0358b84a-4236-4c34-945b-4babff7df570
topic_type:
- apiref
ms.openlocfilehash: 66ec64b1a855a3d31f14f3ef29dde0b82361f5d7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133981"
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="946eb-102">ICorDebugAppDomain::Attach, méthode</span><span class="sxs-lookup"><span data-stu-id="946eb-102">ICorDebugAppDomain::Attach Method</span></span>
<span data-ttu-id="946eb-103">Attache le débogueur au domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="946eb-103">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="946eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="946eb-104">Syntax</span></span>  
  
```cpp  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="946eb-105">Notes</span><span class="sxs-lookup"><span data-stu-id="946eb-105">Remarks</span></span>  
 <span data-ttu-id="946eb-106">Le débogueur doit être attaché au domaine d’application pour recevoir des événements et activer le débogage du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="946eb-106">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="946eb-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="946eb-107">Requirements</span></span>  
 <span data-ttu-id="946eb-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="946eb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="946eb-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="946eb-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="946eb-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="946eb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="946eb-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="946eb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
