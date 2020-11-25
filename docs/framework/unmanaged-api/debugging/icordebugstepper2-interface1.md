---
title: ICorDebugStepper2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2
helpviewer_keywords:
- ICorDebugStepper2 interface [.NET Framework debugging]
ms.assetid: 7a191c2a-95ea-4d47-83b0-44de2b632d63
topic_type:
- apiref
ms.openlocfilehash: ecbedfbca37a3630fc6d40c173f8a6cd05b4d3fb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727638"
---
# <a name="icordebugstepper2-interface"></a><span data-ttu-id="94306-102">ICorDebugStepper2, interface</span><span class="sxs-lookup"><span data-stu-id="94306-102">ICorDebugStepper2 Interface</span></span>

<span data-ttu-id="94306-103">Prend en charge le débogage uniquement mon code (uniquement mon code).</span><span class="sxs-lookup"><span data-stu-id="94306-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="94306-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="94306-104">Methods</span></span>  
  
|<span data-ttu-id="94306-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="94306-105">Method</span></span>|<span data-ttu-id="94306-106">Description</span><span class="sxs-lookup"><span data-stu-id="94306-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="94306-107">SetJMC, méthode</span><span class="sxs-lookup"><span data-stu-id="94306-107">SetJMC Method</span></span>](icordebugstepper2-setjmc-method.md)|<span data-ttu-id="94306-108">Définit une valeur qui spécifie si cet effectue des étapes uniquement par le biais du code créé par le développeur d’une application.</span><span class="sxs-lookup"><span data-stu-id="94306-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94306-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="94306-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94306-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="94306-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94306-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="94306-111">Requirements</span></span>  

 <span data-ttu-id="94306-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94306-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94306-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94306-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94306-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94306-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94306-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94306-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94306-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94306-116">See also</span></span>

- [<span data-ttu-id="94306-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="94306-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
