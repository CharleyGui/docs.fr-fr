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
ms.openlocfilehash: 6cc3ec1c802c28b74248380aa7f686e675a92f1d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088839"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="e685f-102">ICorDebugAppDomainEnum, interface</span><span class="sxs-lookup"><span data-stu-id="e685f-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="e685f-103">Fournit la méthode `Next`, qui retourne un nombre spécifié de valeurs `ICorDebugAppDomainEnum` en commençant à l’emplacement suivant dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="e685f-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="e685f-104">Cette interface est une sous-classe de « ICorDebugEnum ».</span><span class="sxs-lookup"><span data-stu-id="e685f-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e685f-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e685f-105">Methods</span></span>  
  
|<span data-ttu-id="e685f-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="e685f-106">Method</span></span>|<span data-ttu-id="e685f-107">Description</span><span class="sxs-lookup"><span data-stu-id="e685f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e685f-108">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="e685f-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|<span data-ttu-id="e685f-109">Obtient le nombre spécifié de domaines d’application à partir de la collection, en commençant à la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="e685f-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e685f-110">Notes</span><span class="sxs-lookup"><span data-stu-id="e685f-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e685f-111">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="e685f-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e685f-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="e685f-112">Requirements</span></span>  
 <span data-ttu-id="e685f-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e685f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e685f-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e685f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e685f-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e685f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e685f-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e685f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e685f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e685f-117">See also</span></span>

- [<span data-ttu-id="e685f-118">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="e685f-118">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="e685f-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e685f-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
