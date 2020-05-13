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
ms.openlocfilehash: 760f69baf311cf320e9c358ba1c45c942934f1a5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379394"
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="8f056-102">ICorDebugStepper::Deactivate, méthode</span><span class="sxs-lookup"><span data-stu-id="8f056-102">ICorDebugStepper::Deactivate Method</span></span>
<span data-ttu-id="8f056-103">Fait en sorte que ces ICorDebugStepper annulent la dernière commande d’étape qu’il a reçue.</span><span class="sxs-lookup"><span data-stu-id="8f056-103">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f056-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f056-104">Syntax</span></span>  
  
```cpp  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="8f056-105">Notes </span><span class="sxs-lookup"><span data-stu-id="8f056-105">Remarks</span></span>  
 <span data-ttu-id="8f056-106">Une nouvelle commande pas à pas peut être émise après l’annulation de la dernière commande de l’étape reçue.</span><span class="sxs-lookup"><span data-stu-id="8f056-106">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f056-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8f056-107">Requirements</span></span>  
 <span data-ttu-id="8f056-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f056-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f056-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f056-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f056-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f056-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f056-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f056-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
