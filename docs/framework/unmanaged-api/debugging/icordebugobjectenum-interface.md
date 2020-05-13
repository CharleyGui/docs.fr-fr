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
ms.openlocfilehash: 0594caf53a889d51ea78e2ee9d6fff4d30f7cff2
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205294"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="71ae4-102">ICorDebugObjectEnum, interface</span><span class="sxs-lookup"><span data-stu-id="71ae4-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="71ae4-103">Implémente les méthodes ICorDebugEnum et énumère les tableaux d’objets par leurs adresses virtuelles relatives (RVA).</span><span class="sxs-lookup"><span data-stu-id="71ae4-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="71ae4-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="71ae4-104">Methods</span></span>  
  
|<span data-ttu-id="71ae4-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="71ae4-105">Method</span></span>|<span data-ttu-id="71ae4-106">Description</span><span class="sxs-lookup"><span data-stu-id="71ae4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="71ae4-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="71ae4-107">Next Method</span></span>](icordebugobjectenum-next-method.md)|<span data-ttu-id="71ae4-108">Obtient les adresses RVA du nombre spécifié d’objets à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="71ae4-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71ae4-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="71ae4-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71ae4-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="71ae4-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71ae4-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="71ae4-111">Requirements</span></span>  
 <span data-ttu-id="71ae4-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71ae4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71ae4-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71ae4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71ae4-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71ae4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71ae4-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71ae4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71ae4-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71ae4-116">See also</span></span>

- [<span data-ttu-id="71ae4-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="71ae4-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
