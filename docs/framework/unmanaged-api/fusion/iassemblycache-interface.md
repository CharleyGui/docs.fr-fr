---
title: IAssemblyCache, interface
ms.date: 03/30/2017
api_name:
- IAssemblyCache
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache
helpviewer_keywords:
- IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type:
- apiref
ms.openlocfilehash: df4f0ba018b55202c22cb90b22b927a9c426c4ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696854"
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="1b2a4-102">IAssemblyCache, interface</span><span class="sxs-lookup"><span data-stu-id="1b2a4-102">IAssemblyCache Interface</span></span>

<span data-ttu-id="1b2a4-103">Représente le Global Assembly Cache pour une utilisation par la technologie de fusion.</span><span class="sxs-lookup"><span data-stu-id="1b2a4-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1b2a4-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="1b2a4-104">Methods</span></span>  
  
|<span data-ttu-id="1b2a4-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="1b2a4-105">Method</span></span>|<span data-ttu-id="1b2a4-106">Description</span><span class="sxs-lookup"><span data-stu-id="1b2a4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b2a4-107">CreateAssemblyCacheItem, méthode</span><span class="sxs-lookup"><span data-stu-id="1b2a4-107">CreateAssemblyCacheItem Method</span></span>](iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="1b2a4-108">Obtient une référence à un nouvel [IAssemblyCacheItem](iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="1b2a4-108">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="1b2a4-109">CreateAssemblyScavenger, méthode</span><span class="sxs-lookup"><span data-stu-id="1b2a4-109">CreateAssemblyScavenger Method</span></span>](iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="1b2a4-110">Réservé à un usage interne par la technologie de fusion.</span><span class="sxs-lookup"><span data-stu-id="1b2a4-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="1b2a4-111">InstallAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="1b2a4-111">InstallAssembly Method</span></span>](iassemblycache-installassembly-method.md)|<span data-ttu-id="1b2a4-112">Installe l’assembly spécifié dans la Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="1b2a4-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="1b2a4-113">QueryAssemblyInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="1b2a4-113">QueryAssemblyInfo Method</span></span>](iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="1b2a4-114">Obtient les données demandées relatives à l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="1b2a4-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="1b2a4-115">UninstallAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="1b2a4-115">UninstallAssembly Method</span></span>](iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="1b2a4-116">Désinstalle l’assembly spécifié du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="1b2a4-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1b2a4-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1b2a4-117">Requirements</span></span>  

 <span data-ttu-id="1b2a4-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b2a4-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b2a4-119">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="1b2a4-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1b2a4-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b2a4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b2a4-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b2a4-121">See also</span></span>

- [<span data-ttu-id="1b2a4-122">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="1b2a4-122">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="1b2a4-123">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="1b2a4-123">Global Assembly Cache</span></span>](../../app-domains/gac.md)
