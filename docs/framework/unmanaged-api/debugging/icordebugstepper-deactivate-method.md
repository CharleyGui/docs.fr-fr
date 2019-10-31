---
title: ICorDebugStepper::Deactivate, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Deactivate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Deactivate
helpviewer_keywords:
- Deactivate method [.NET Framework debugging]
- ICorDebugStepper::Deactivate method [.NET Framework debugging]
ms.assetid: 855f4199-b62d-40ce-998e-1eb4a1772142
topic_type:
- apiref
ms.openlocfilehash: 1d75897e00c36bd5c484e837ee68e54443168e77
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131752"
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="b327a-102">ICorDebugStepper::Deactivate, méthode</span><span class="sxs-lookup"><span data-stu-id="b327a-102">ICorDebugStepper::Deactivate Method</span></span>
<span data-ttu-id="b327a-103">Fait en sorte que ces ICorDebugStepper annulent la dernière commande d’étape qu’il a reçue.</span><span class="sxs-lookup"><span data-stu-id="b327a-103">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b327a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b327a-104">Syntax</span></span>  
  
```cpp  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b327a-105">Notes</span><span class="sxs-lookup"><span data-stu-id="b327a-105">Remarks</span></span>  
 <span data-ttu-id="b327a-106">Une nouvelle commande pas à pas peut être émise après l’annulation de la dernière commande de l’étape reçue.</span><span class="sxs-lookup"><span data-stu-id="b327a-106">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b327a-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="b327a-107">Requirements</span></span>  
 <span data-ttu-id="b327a-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b327a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b327a-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b327a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b327a-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b327a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b327a-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b327a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
