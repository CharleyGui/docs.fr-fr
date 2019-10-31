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
ms.openlocfilehash: a5cda98cac0bc3fc6fb101fd0404b062224cb578
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134082"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="f74ae-102">ICorDebug::Initialize, méthode</span><span class="sxs-lookup"><span data-stu-id="f74ae-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="f74ae-103">Initialise l’objet `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="f74ae-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f74ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f74ae-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f74ae-105">Notes</span><span class="sxs-lookup"><span data-stu-id="f74ae-105">Remarks</span></span>  
 <span data-ttu-id="f74ae-106">Le débogueur doit appeler `Initialize` au moment de la création pour initialiser les services de débogage.</span><span class="sxs-lookup"><span data-stu-id="f74ae-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="f74ae-107">Cette méthode doit être appelée avant que toute autre méthode sur `ICorDebug` soit appelée.</span><span class="sxs-lookup"><span data-stu-id="f74ae-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f74ae-108">spécifications</span><span class="sxs-lookup"><span data-stu-id="f74ae-108">Requirements</span></span>  
 <span data-ttu-id="f74ae-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f74ae-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f74ae-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f74ae-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f74ae-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f74ae-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f74ae-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f74ae-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f74ae-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f74ae-113">See also</span></span>

- [<span data-ttu-id="f74ae-114">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="f74ae-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
