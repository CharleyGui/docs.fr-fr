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
ms.openlocfilehash: 38603fb53b9cd6548595437b05c1e99ef208d940
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895093"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="fc1f0-102">ICorDebugAppDomainEnum, interface</span><span class="sxs-lookup"><span data-stu-id="fc1f0-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="fc1f0-103">Fournit la `Next` méthode, qui retourne un nombre spécifié de `ICorDebugAppDomainEnum` valeurs à partir de l’emplacement suivant dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="fc1f0-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="fc1f0-104">Cette interface est une sous-classe de « ICorDebugEnum ».</span><span class="sxs-lookup"><span data-stu-id="fc1f0-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fc1f0-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="fc1f0-105">Methods</span></span>  
  
|<span data-ttu-id="fc1f0-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="fc1f0-106">Method</span></span>|<span data-ttu-id="fc1f0-107">Description</span><span class="sxs-lookup"><span data-stu-id="fc1f0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fc1f0-108">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="fc1f0-108">Next Method</span></span>](icordebugappdomainenum-next-method.md)|<span data-ttu-id="fc1f0-109">Obtient le nombre spécifié de domaines d’application à partir de la collection, en commençant à la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="fc1f0-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc1f0-110">Notes </span><span class="sxs-lookup"><span data-stu-id="fc1f0-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc1f0-111">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="fc1f0-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc1f0-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fc1f0-112">Requirements</span></span>  
 <span data-ttu-id="fc1f0-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc1f0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc1f0-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc1f0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc1f0-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc1f0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc1f0-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc1f0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc1f0-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc1f0-117">See also</span></span>

- [<span data-ttu-id="fc1f0-118">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="fc1f0-118">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="fc1f0-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="fc1f0-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
