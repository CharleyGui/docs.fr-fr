---
title: ICorDebugAppDomainEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum
helpviewer_keywords:
- ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: e9226e6e-ca2c-428e-bb38-0c099210f507
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c48c222a34e2e78f29c33e49da331d97d409bae1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949759"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="633ac-102">ICorDebugAppDomainEnum, interface</span><span class="sxs-lookup"><span data-stu-id="633ac-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="633ac-103">Fournit la `Next` méthode, qui retourne un nombre spécifié de `ICorDebugAppDomainEnum` valeurs à partir de l’emplacement suivant dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="633ac-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="633ac-104">Cette interface est une sous-classe de «ICorDebugEnum».</span><span class="sxs-lookup"><span data-stu-id="633ac-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="633ac-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="633ac-105">Methods</span></span>  
  
|<span data-ttu-id="633ac-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="633ac-106">Method</span></span>|<span data-ttu-id="633ac-107">Description</span><span class="sxs-lookup"><span data-stu-id="633ac-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="633ac-108">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="633ac-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|<span data-ttu-id="633ac-109">Obtient le nombre spécifié de domaines d’application à partir de la collection, en commençant à la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="633ac-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="633ac-110">Notes</span><span class="sxs-lookup"><span data-stu-id="633ac-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="633ac-111">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="633ac-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="633ac-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="633ac-112">Requirements</span></span>  
 <span data-ttu-id="633ac-113">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="633ac-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="633ac-114">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="633ac-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="633ac-115">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="633ac-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="633ac-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="633ac-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="633ac-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="633ac-117">See also</span></span>

- [<span data-ttu-id="633ac-118">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="633ac-118">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="633ac-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="633ac-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
