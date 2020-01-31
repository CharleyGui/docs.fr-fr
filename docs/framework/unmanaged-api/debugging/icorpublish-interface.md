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
ms.openlocfilehash: c4a24d879ebd9e8813ea0ac4597818569f4ae6fa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790727"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="b45db-102">ICorPublish, interface</span><span class="sxs-lookup"><span data-stu-id="b45db-102">ICorPublish Interface</span></span>
<span data-ttu-id="b45db-103">Sert d’interface générale pour la publication d’informations sur les processus et les informations sur les domaines d’application de ces processus.</span><span class="sxs-lookup"><span data-stu-id="b45db-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b45db-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b45db-104">Methods</span></span>  
  
|<span data-ttu-id="b45db-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="b45db-105">Method</span></span>|<span data-ttu-id="b45db-106">Description</span><span class="sxs-lookup"><span data-stu-id="b45db-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b45db-107">EnumProcesses, méthode</span><span class="sxs-lookup"><span data-stu-id="b45db-107">EnumProcesses Method</span></span>](icorpublish-enumprocesses-method.md)|<span data-ttu-id="b45db-108">Obtient une instance [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) qui contient les processus managés en cours d’exécution sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b45db-108">Gets an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="b45db-109">GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="b45db-109">GetProcess Method</span></span>](icorpublish-getprocess-method.md)|<span data-ttu-id="b45db-110">Obtient une instance de [ICorPublishProcess](icorpublishprocess-interface.md) qui représente le processus avec l’identificateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="b45db-110">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b45db-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="b45db-111">Requirements</span></span>  
 <span data-ttu-id="b45db-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b45db-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b45db-113">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="b45db-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b45db-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b45db-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b45db-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b45db-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b45db-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b45db-116">See also</span></span>

- [<span data-ttu-id="b45db-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="b45db-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b45db-118">CorpubPublish, coclasse</span><span class="sxs-lookup"><span data-stu-id="b45db-118">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
