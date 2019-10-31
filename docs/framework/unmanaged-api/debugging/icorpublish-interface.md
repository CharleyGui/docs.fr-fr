---
title: ICorPublish, interface
ms.date: 03/30/2017
api_name:
- ICorPublish
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish
helpviewer_keywords:
- ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type:
- apiref
ms.openlocfilehash: 70cf2d76c7c5d1c3431506685f8506e44ab9ec4a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121767"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="6dfb0-102">ICorPublish, interface</span><span class="sxs-lookup"><span data-stu-id="6dfb0-102">ICorPublish Interface</span></span>
<span data-ttu-id="6dfb0-103">Sert d’interface générale pour la publication d’informations sur les processus et les informations sur les domaines d’application de ces processus.</span><span class="sxs-lookup"><span data-stu-id="6dfb0-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6dfb0-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6dfb0-104">Methods</span></span>  
  
|<span data-ttu-id="6dfb0-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="6dfb0-105">Method</span></span>|<span data-ttu-id="6dfb0-106">Description</span><span class="sxs-lookup"><span data-stu-id="6dfb0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6dfb0-107">EnumProcesses, méthode</span><span class="sxs-lookup"><span data-stu-id="6dfb0-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="6dfb0-108">Obtient une instance [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) qui contient les processus managés en cours d’exécution sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6dfb0-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="6dfb0-109">GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="6dfb0-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="6dfb0-110">Obtient une instance de [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) qui représente le processus avec l’identificateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="6dfb0-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6dfb0-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="6dfb0-111">Requirements</span></span>  
 <span data-ttu-id="6dfb0-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dfb0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dfb0-113">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="6dfb0-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="6dfb0-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6dfb0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6dfb0-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dfb0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dfb0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6dfb0-116">See also</span></span>

- [<span data-ttu-id="6dfb0-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="6dfb0-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6dfb0-118">CorpubPublish, coclasse</span><span class="sxs-lookup"><span data-stu-id="6dfb0-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
