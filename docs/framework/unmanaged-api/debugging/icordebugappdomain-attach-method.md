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
ms.openlocfilehash: 92cc6c3ce15d8391a43ff130a82476a4363ff5bd
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895297"
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="95b4c-102">ICorDebugAppDomain::Attach, méthode</span><span class="sxs-lookup"><span data-stu-id="95b4c-102">ICorDebugAppDomain::Attach Method</span></span>
<span data-ttu-id="95b4c-103">Attache le débogueur au domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="95b4c-103">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95b4c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95b4c-104">Syntax</span></span>  
  
```cpp  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="95b4c-105">Notes </span><span class="sxs-lookup"><span data-stu-id="95b4c-105">Remarks</span></span>  
 <span data-ttu-id="95b4c-106">Le débogueur doit être attaché au domaine d’application pour recevoir des événements et activer le débogage du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="95b4c-106">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95b4c-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="95b4c-107">Requirements</span></span>  
 <span data-ttu-id="95b4c-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95b4c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95b4c-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95b4c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95b4c-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95b4c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95b4c-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95b4c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
