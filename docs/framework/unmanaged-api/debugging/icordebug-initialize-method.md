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
ms.openlocfilehash: 3d27cf1987d7e9896885f87857554f4039c8d714
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788976"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="f3dbd-102">ICorDebug::Initialize, méthode</span><span class="sxs-lookup"><span data-stu-id="f3dbd-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="f3dbd-103">Initialise l’objet `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="f3dbd-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3dbd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3dbd-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f3dbd-105">Notes</span><span class="sxs-lookup"><span data-stu-id="f3dbd-105">Remarks</span></span>  
 <span data-ttu-id="f3dbd-106">Le débogueur doit appeler `Initialize` au moment de la création pour initialiser les services de débogage.</span><span class="sxs-lookup"><span data-stu-id="f3dbd-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="f3dbd-107">Cette méthode doit être appelée avant que toute autre méthode sur `ICorDebug` soit appelée.</span><span class="sxs-lookup"><span data-stu-id="f3dbd-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3dbd-108">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="f3dbd-108">Requirements</span></span>  
 <span data-ttu-id="f3dbd-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3dbd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3dbd-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f3dbd-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3dbd-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3dbd-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3dbd-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3dbd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3dbd-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3dbd-113">See also</span></span>

- [<span data-ttu-id="f3dbd-114">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="f3dbd-114">ICorDebug Interface</span></span>](icordebug-interface.md)
