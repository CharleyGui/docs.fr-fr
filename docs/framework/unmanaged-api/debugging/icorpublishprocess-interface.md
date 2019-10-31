---
title: ICorPublishProcess, interface
ms.date: 03/30/2017
api_name:
- ICorPublishProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess
helpviewer_keywords:
- ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type:
- apiref
ms.openlocfilehash: 04f6a088c5bbe96e3909ba600aa8ffab937abe2d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140401"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="6cd27-102">ICorPublishProcess, interface</span><span class="sxs-lookup"><span data-stu-id="6cd27-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="6cd27-103">Fournit des méthodes qui accèdent aux informations à afficher sur un processus.</span><span class="sxs-lookup"><span data-stu-id="6cd27-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6cd27-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6cd27-104">Methods</span></span>  
  
|<span data-ttu-id="6cd27-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="6cd27-105">Method</span></span>|<span data-ttu-id="6cd27-106">Description</span><span class="sxs-lookup"><span data-stu-id="6cd27-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6cd27-107">EnumAppDomains, méthode</span><span class="sxs-lookup"><span data-stu-id="6cd27-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="6cd27-108">Obtient une instance de [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) qui contient les domaines d’application dans le processus référencé par cette `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="6cd27-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="6cd27-109">GetDisplayName, méthode</span><span class="sxs-lookup"><span data-stu-id="6cd27-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="6cd27-110">Obtient le chemin d’accès complet de l’exécutable pour le processus référencé par cette `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="6cd27-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="6cd27-111">GetProcessID, méthode</span><span class="sxs-lookup"><span data-stu-id="6cd27-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="6cd27-112">Obtient l’identificateur de système d’exploitation pour le processus référencé par cette `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="6cd27-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="6cd27-113">IsManaged, méthode</span><span class="sxs-lookup"><span data-stu-id="6cd27-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="6cd27-114">Obtient une valeur qui indique si le processus référencé par ce `ICorPublishProcess` est connu comme étant en cours d’exécution du code managé.</span><span class="sxs-lookup"><span data-stu-id="6cd27-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6cd27-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="6cd27-115">Requirements</span></span>  
 <span data-ttu-id="6cd27-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cd27-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cd27-117">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="6cd27-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="6cd27-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cd27-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cd27-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cd27-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd27-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6cd27-120">See also</span></span>

- [<span data-ttu-id="6cd27-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="6cd27-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6cd27-122">CorpubPublish, coclasse</span><span class="sxs-lookup"><span data-stu-id="6cd27-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
