---
title: ICorDebugObjectEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum
helpviewer_keywords:
- ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type:
- apiref
ms.openlocfilehash: 0526c050bcf1316eccf2c756a404fbb971e6d7d0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792742"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="e434e-102">ICorDebugObjectEnum, interface</span><span class="sxs-lookup"><span data-stu-id="e434e-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="e434e-103">Implémente les méthodes ICorDebugEnum et énumère les tableaux d’objets par leurs adresses virtuelles relatives (RVA).</span><span class="sxs-lookup"><span data-stu-id="e434e-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e434e-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e434e-104">Methods</span></span>  
  
|<span data-ttu-id="e434e-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="e434e-105">Method</span></span>|<span data-ttu-id="e434e-106">Description</span><span class="sxs-lookup"><span data-stu-id="e434e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e434e-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="e434e-107">Next Method</span></span>](icordebugobjectenum-next-method.md)|<span data-ttu-id="e434e-108">Obtient les adresses RVA du nombre spécifié d’objets à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="e434e-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e434e-109">Notes</span><span class="sxs-lookup"><span data-stu-id="e434e-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e434e-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="e434e-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e434e-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e434e-111">Requirements</span></span>  
 <span data-ttu-id="e434e-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e434e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e434e-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e434e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e434e-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e434e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e434e-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e434e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e434e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e434e-116">See also</span></span>

- [<span data-ttu-id="e434e-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e434e-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
