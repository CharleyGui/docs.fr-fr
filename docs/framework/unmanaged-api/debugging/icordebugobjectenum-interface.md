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
ms.openlocfilehash: 9400c4fa3ddcefef923d7bcfaae80e2cef62dc7d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695463"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="d738c-102">ICorDebugObjectEnum, interface</span><span class="sxs-lookup"><span data-stu-id="d738c-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="d738c-103">Implémente les méthodes ICorDebugEnum et énumère les tableaux d’objets par leurs adresses virtuelles relatives (RVA).</span><span class="sxs-lookup"><span data-stu-id="d738c-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d738c-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d738c-104">Methods</span></span>  
  
|<span data-ttu-id="d738c-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d738c-105">Method</span></span>|<span data-ttu-id="d738c-106">Description</span><span class="sxs-lookup"><span data-stu-id="d738c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d738c-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="d738c-107">Next Method</span></span>](icordebugobjectenum-next-method.md)|<span data-ttu-id="d738c-108">Obtient les adresses RVA du nombre spécifié d’objets à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="d738c-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d738c-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="d738c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d738c-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="d738c-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d738c-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d738c-111">Requirements</span></span>  

 <span data-ttu-id="d738c-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d738c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d738c-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d738c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d738c-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d738c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d738c-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d738c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d738c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d738c-116">See also</span></span>

- [<span data-ttu-id="d738c-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d738c-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
