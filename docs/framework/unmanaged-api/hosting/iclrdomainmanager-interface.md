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
ms.openlocfilehash: a5abb601fe795a0c615403eec69f68ad9f66f00f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681169"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="194b3-102">ICLRDomainManager, interface</span><span class="sxs-lookup"><span data-stu-id="194b3-102">ICLRDomainManager Interface</span></span>

<span data-ttu-id="194b3-103">Permet à l’hôte de spécifier le gestionnaire de domaine d’application qui sera utilisé pour initialiser le domaine d’application par défaut et pour spécifier les propriétés d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="194b3-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="194b3-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="194b3-104">Methods</span></span>  
  
|<span data-ttu-id="194b3-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="194b3-105">Method</span></span>|<span data-ttu-id="194b3-106">Description</span><span class="sxs-lookup"><span data-stu-id="194b3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="194b3-107">SetAppDomainManagerType, méthode</span><span class="sxs-lookup"><span data-stu-id="194b3-107">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="194b3-108">Spécifie le type, dérivé de la <xref:System.AppDomainManager?displayProperty=nameWithType> classe, du gestionnaire de domaine d’application qui sera utilisé pour initialiser le domaine d’application par défaut.</span><span class="sxs-lookup"><span data-stu-id="194b3-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="194b3-109">SetPropertiesForDefaultAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="194b3-109">SetPropertiesForDefaultAppDomain Method</span></span>](iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="194b3-110">Définit les propriétés qui seront utilisées pour initialiser le domaine d’application par défaut.</span><span class="sxs-lookup"><span data-stu-id="194b3-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="194b3-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="194b3-111">Remarks</span></span>  

 <span data-ttu-id="194b3-112">Pour récupérer une instance de cette interface, appelez la méthode [ICLRControl :: GetCLRManager](iclrcontrol-getclrmanager-method.md) avec l’IID de type Manager `IID_ICLRDomainManager` .</span><span class="sxs-lookup"><span data-stu-id="194b3-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="194b3-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="194b3-113">Requirements</span></span>  

 <span data-ttu-id="194b3-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="194b3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="194b3-115">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="194b3-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="194b3-116">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="194b3-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="194b3-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="194b3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="194b3-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="194b3-118">See also</span></span>

- [<span data-ttu-id="194b3-119">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="194b3-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="194b3-120">Hébergement</span><span class="sxs-lookup"><span data-stu-id="194b3-120">Hosting</span></span>](index.md)
