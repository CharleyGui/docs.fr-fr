---
title: ICorDebugStepper::SetUnmappedStopMask, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetUnmappedStopMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0a273c54559e8e297e09740ba9c770ce12d72d1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760584"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="bd33c-102">ICorDebugStepper::SetUnmappedStopMask, méthode</span><span class="sxs-lookup"><span data-stu-id="bd33c-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="bd33c-103">Définit une valeur qui spécifie le type de code non mappé dans lequel l’exécution s’arrêtera.</span><span class="sxs-lookup"><span data-stu-id="bd33c-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd33c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd33c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd33c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bd33c-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="bd33c-106">[in] Une valeur de l’énumération CorDebugUnmappedStop qui spécifie le type de code non mappé dans lequel le débogueur arrêtera l’exécution.</span><span class="sxs-lookup"><span data-stu-id="bd33c-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="bd33c-107">La valeur par défaut est STOP_OTHER_UNMAPPED.</span><span class="sxs-lookup"><span data-stu-id="bd33c-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="bd33c-108">La valeur STOP_UNMANAGED est uniquement valide avec le débogage d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="bd33c-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd33c-109">Notes</span><span class="sxs-lookup"><span data-stu-id="bd33c-109">Remarks</span></span>  
 <span data-ttu-id="bd33c-110">Lorsque le débogueur trouve une compilation juste-à-temps (JIT) n’a aucun mappage correspondant à Microsoft intermediate language (MSIL), il arrête l’exécution si l’indicateur qui spécifie ce type de code non mappé a été défini ; le cas contraire, pas à pas détaillé en toute transparence continue.</span><span class="sxs-lookup"><span data-stu-id="bd33c-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="bd33c-111">Si le débogueur n’utilise pas une exécution pas à pas pour une méthode d’entrée, puis il ne sont pas nécessairement effectuer un survol code non mappé.</span><span class="sxs-lookup"><span data-stu-id="bd33c-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd33c-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bd33c-112">Requirements</span></span>  
 <span data-ttu-id="bd33c-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd33c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd33c-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd33c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd33c-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd33c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd33c-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd33c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
