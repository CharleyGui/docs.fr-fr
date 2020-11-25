---
title: ICorDebugCode4, interface
ms.date: 03/30/2017
api_name:
- ICorDebugCode4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4
helpviewer_keywords:
- ICorDebugCode4 interface [.NET Framework debugging]
ms.assetid: a3fdf523-274a-449c-920b-9fcb0aed1d97
topic_type:
- apiref
ms.openlocfilehash: 8a373afdf41590ec44a7cbac7360719a12faa82e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720722"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="9b753-102">ICorDebugCode4, interface</span><span class="sxs-lookup"><span data-stu-id="9b753-102">ICorDebugCode4 Interface</span></span>

<span data-ttu-id="9b753-103">Fournit une méthode qui permet à un débogueur d’énumérer les variables et les arguments locaux dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="9b753-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9b753-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9b753-104">Methods</span></span>  
  
|<span data-ttu-id="9b753-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="9b753-105">Method</span></span>|<span data-ttu-id="9b753-106">Description</span><span class="sxs-lookup"><span data-stu-id="9b753-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9b753-107">EnumerateVariableHomes, méthode</span><span class="sxs-lookup"><span data-stu-id="9b753-107">EnumerateVariableHomes Method</span></span>](icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="9b753-108">Obtient un énumérateur pour les variables locales et les arguments dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="9b753-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b753-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="9b753-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b753-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="9b753-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b753-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9b753-111">Requirements</span></span>  

 <span data-ttu-id="9b753-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b753-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b753-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b753-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b753-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b753-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b753-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b753-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b753-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b753-116">See also</span></span>

- [<span data-ttu-id="9b753-117">ICorDebugCode3, interface</span><span class="sxs-lookup"><span data-stu-id="9b753-117">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="9b753-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9b753-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
