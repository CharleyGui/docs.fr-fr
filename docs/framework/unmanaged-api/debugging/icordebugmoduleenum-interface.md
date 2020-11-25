---
title: ICorDebugModuleEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum
helpviewer_keywords:
- ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type:
- apiref
ms.openlocfilehash: 08d16393a04888cd3f1a03fa209a1fceac28520b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724752"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="75821-102">ICorDebugModuleEnum, interface</span><span class="sxs-lookup"><span data-stu-id="75821-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="75821-103">Implémente les méthodes ICorDebugEnum et énumère les tableaux ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="75821-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="75821-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="75821-104">Methods</span></span>  
  
|<span data-ttu-id="75821-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="75821-105">Method</span></span>|<span data-ttu-id="75821-106">Description</span><span class="sxs-lookup"><span data-stu-id="75821-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="75821-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="75821-107">Next Method</span></span>](icordebugmoduleenum-next-method.md)|<span data-ttu-id="75821-108">Obtient le nombre d' `ICorDebugModule` instances spécifié à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="75821-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75821-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="75821-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75821-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="75821-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75821-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="75821-111">Requirements</span></span>  

 <span data-ttu-id="75821-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75821-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75821-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="75821-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75821-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75821-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75821-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75821-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75821-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75821-116">See also</span></span>

- [<span data-ttu-id="75821-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="75821-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
