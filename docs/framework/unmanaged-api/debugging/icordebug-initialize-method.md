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
ms.openlocfilehash: aeecf19cb85ce5d7781c3dfedca079e97cab76ce
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895357"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="2fc05-102">ICorDebug::Initialize, méthode</span><span class="sxs-lookup"><span data-stu-id="2fc05-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="2fc05-103">Initialise l'objet `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="2fc05-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fc05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fc05-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="2fc05-105">Notes </span><span class="sxs-lookup"><span data-stu-id="2fc05-105">Remarks</span></span>  
 <span data-ttu-id="2fc05-106">Le débogueur doit appeler `Initialize` au moment de la création pour initialiser les services de débogage.</span><span class="sxs-lookup"><span data-stu-id="2fc05-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="2fc05-107">Cette méthode doit être appelée avant l’appel de toute `ICorDebug` autre méthode sur.</span><span class="sxs-lookup"><span data-stu-id="2fc05-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fc05-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2fc05-108">Requirements</span></span>  
 <span data-ttu-id="2fc05-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fc05-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fc05-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fc05-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fc05-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fc05-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fc05-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fc05-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fc05-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fc05-113">See also</span></span>

- [<span data-ttu-id="2fc05-114">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="2fc05-114">ICorDebug Interface</span></span>](icordebug-interface.md)
