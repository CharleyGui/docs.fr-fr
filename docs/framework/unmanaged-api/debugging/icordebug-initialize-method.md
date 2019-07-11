---
title: ICorDebug::Initialize, méthode
ms.date: 03/30/2017
api_name:
- ICorDebug.Initialize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Initialize
helpviewer_keywords:
- Initialize method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Initialize method [.NET Framework debugging]
ms.assetid: 6fae3b23-5c9f-47c0-85d8-6bb75e050786
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80465c8d1f1f9e09c0675de1667b999b332b9f6b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738145"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="e0c1a-102">ICorDebug::Initialize, méthode</span><span class="sxs-lookup"><span data-stu-id="e0c1a-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="e0c1a-103">Initialise le `ICorDebug` objet.</span><span class="sxs-lookup"><span data-stu-id="e0c1a-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0c1a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0c1a-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e0c1a-105">Notes</span><span class="sxs-lookup"><span data-stu-id="e0c1a-105">Remarks</span></span>  
 <span data-ttu-id="e0c1a-106">Le débogueur doit appeler `Initialize` lors de la création de temps pour s’initialiser le débogage de services.</span><span class="sxs-lookup"><span data-stu-id="e0c1a-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="e0c1a-107">Cette méthode doit être appelée avant toute autre méthode sur `ICorDebug` est appelée.</span><span class="sxs-lookup"><span data-stu-id="e0c1a-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0c1a-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e0c1a-108">Requirements</span></span>  
 <span data-ttu-id="e0c1a-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0c1a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0c1a-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0c1a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0c1a-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0c1a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0c1a-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0c1a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0c1a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0c1a-113">See also</span></span>

- [<span data-ttu-id="e0c1a-114">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="e0c1a-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
