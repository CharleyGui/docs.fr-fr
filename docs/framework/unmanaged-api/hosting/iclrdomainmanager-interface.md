---
title: ICLRDomainManager, interface
ms.date: 03/30/2017
api_name:
- ICLRDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager
helpviewer_keywords:
- ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
ms.openlocfilehash: aa874205cf14232e7a69ed2215086e33c0beab4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129341"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="99dbb-102">ICLRDomainManager, interface</span><span class="sxs-lookup"><span data-stu-id="99dbb-102">ICLRDomainManager Interface</span></span>
<span data-ttu-id="99dbb-103">Permet à l’hôte de spécifier le gestionnaire de domaine d’application qui sera utilisé pour initialiser le domaine d’application par défaut et pour spécifier les propriétés d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="99dbb-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99dbb-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="99dbb-104">Methods</span></span>  
  
|<span data-ttu-id="99dbb-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="99dbb-105">Method</span></span>|<span data-ttu-id="99dbb-106">Description</span><span class="sxs-lookup"><span data-stu-id="99dbb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99dbb-107">SetAppDomainManagerType, méthode</span><span class="sxs-lookup"><span data-stu-id="99dbb-107">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="99dbb-108">Spécifie le type, dérivé de la classe <xref:System.AppDomainManager?displayProperty=nameWithType>, du gestionnaire de domaine d’application qui sera utilisé pour initialiser le domaine d’application par défaut.</span><span class="sxs-lookup"><span data-stu-id="99dbb-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="99dbb-109">SetPropertiesForDefaultAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="99dbb-109">SetPropertiesForDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="99dbb-110">Définit les propriétés qui seront utilisées pour initialiser le domaine d’application par défaut.</span><span class="sxs-lookup"><span data-stu-id="99dbb-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99dbb-111">Notes</span><span class="sxs-lookup"><span data-stu-id="99dbb-111">Remarks</span></span>  
 <span data-ttu-id="99dbb-112">Pour récupérer une instance de cette interface, appelez la méthode [ICLRControl :: GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) avec l’IID de type Manager `IID_ICLRDomainManager`.</span><span class="sxs-lookup"><span data-stu-id="99dbb-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99dbb-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="99dbb-113">Requirements</span></span>  
 <span data-ttu-id="99dbb-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99dbb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99dbb-115">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="99dbb-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="99dbb-116">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="99dbb-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99dbb-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99dbb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99dbb-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99dbb-118">See also</span></span>

- [<span data-ttu-id="99dbb-119">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="99dbb-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="99dbb-120">Hébergement</span><span class="sxs-lookup"><span data-stu-id="99dbb-120">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
