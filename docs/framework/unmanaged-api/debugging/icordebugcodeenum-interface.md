---
title: ICorDebugCodeEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum
helpviewer_keywords:
- ICorDebugCodeEnum interface [.NET Framework debugging]
ms.assetid: b5589171-a4a0-4c00-bbdc-6e0a42233b75
topic_type:
- apiref
ms.openlocfilehash: 127022fb8e9f9559ccb0f0c877d25db67eea3037
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784013"
---
# <a name="icordebugcodeenum-interface"></a><span data-ttu-id="fe44f-102">ICorDebugCodeEnum, interface</span><span class="sxs-lookup"><span data-stu-id="fe44f-102">ICorDebugCodeEnum Interface</span></span>

<span data-ttu-id="fe44f-103">Implémente les méthodes « ICorDebugEnum » et énumère les tableaux « ICorDebugCode ».</span><span class="sxs-lookup"><span data-stu-id="fe44f-103">Implements "ICorDebugEnum" methods, and enumerates "ICorDebugCode" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fe44f-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="fe44f-104">Methods</span></span>  
  
|<span data-ttu-id="fe44f-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="fe44f-105">Method</span></span>|<span data-ttu-id="fe44f-106">Description</span><span class="sxs-lookup"><span data-stu-id="fe44f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fe44f-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="fe44f-107">Next Method</span></span>](icordebugcodeenum-next-method.md)|<span data-ttu-id="fe44f-108">Obtient le nombre spécifié d’instances de `ICorDebugCode` à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="fe44f-108">Gets the specified number of `ICorDebugCode` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe44f-109">Notes</span><span class="sxs-lookup"><span data-stu-id="fe44f-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe44f-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="fe44f-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe44f-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="fe44f-111">Requirements</span></span>  
 <span data-ttu-id="fe44f-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe44f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe44f-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe44f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe44f-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe44f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe44f-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe44f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe44f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe44f-116">See also</span></span>

- [<span data-ttu-id="fe44f-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="fe44f-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
