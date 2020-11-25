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
ms.openlocfilehash: 50fad8b38a6b33d0ddbb2f0f20676296c3d66737
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698732"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="ec055-102">ICorDebugStepper::SetUnmappedStopMask, méthode</span><span class="sxs-lookup"><span data-stu-id="ec055-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>

<span data-ttu-id="ec055-103">Définit une valeur qui spécifie le type de code non mappé dans lequel l’exécution s’arrêtera.</span><span class="sxs-lookup"><span data-stu-id="ec055-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec055-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec055-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec055-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ec055-105">Parameters</span></span>  

 `mask`  
 <span data-ttu-id="ec055-106">dans Valeur de l’énumération CorDebugUnmappedStop, qui spécifie le type de code non mappé dans lequel le débogueur arrêtera l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ec055-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="ec055-107">La valeur par défaut est STOP_OTHER_UNMAPPED.</span><span class="sxs-lookup"><span data-stu-id="ec055-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="ec055-108">La valeur STOP_UNMANAGED est valide uniquement avec le débogage d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="ec055-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec055-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="ec055-109">Remarks</span></span>  

 <span data-ttu-id="ec055-110">Quand le débogueur trouve une compilation juste-à-temps (JIT) qui n’a pas de mappage correspondant au langage MSIL (Microsoft Intermediate Language), il interrompt l’exécution si l’indicateur spécifiant ce type de code non mappé a été défini ; dans le cas contraire, l’exécution pas à pas se poursuit en toute transparence.</span><span class="sxs-lookup"><span data-stu-id="ec055-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="ec055-111">Si le débogueur n’utilise pas de pas à pas pour entrer dans une méthode, il n’effectuera pas nécessairement un pas à pas principal dans le code non mappé.</span><span class="sxs-lookup"><span data-stu-id="ec055-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec055-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ec055-112">Requirements</span></span>  

 <span data-ttu-id="ec055-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec055-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec055-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec055-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec055-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec055-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec055-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec055-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
