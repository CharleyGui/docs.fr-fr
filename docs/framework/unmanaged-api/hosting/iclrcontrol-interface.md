---
title: ICLRControl, interface
ms.date: 03/30/2017
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
ms.openlocfilehash: 54748fdeaf911591c21f4495335e54c777878f04
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615835"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="659cc-102">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="659cc-102">ICLRControl Interface</span></span>
<span data-ttu-id="659cc-103">Fournit des méthodes qui permettent à un hôte d’obtenir des références à, et de configurer des aspects de, le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="659cc-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="659cc-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="659cc-104">Methods</span></span>  
  
|<span data-ttu-id="659cc-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="659cc-105">Method</span></span>|<span data-ttu-id="659cc-106">Description</span><span class="sxs-lookup"><span data-stu-id="659cc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="659cc-107">GetCLRManager, méthode</span><span class="sxs-lookup"><span data-stu-id="659cc-107">GetCLRManager Method</span></span>](iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="659cc-108">Obtient un pointeur d’interface vers une instance de l’un des types de gestionnaires que l’hôte peut utiliser pour configurer le CLR.</span><span class="sxs-lookup"><span data-stu-id="659cc-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="659cc-109">SetAppDomainManagerType, méthode</span><span class="sxs-lookup"><span data-stu-id="659cc-109">SetAppDomainManagerType Method</span></span>](iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="659cc-110">Définit un type dérivé de <xref:System.AppDomainManager> comme type pour les gestionnaires de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="659cc-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="659cc-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="659cc-111">Requirements</span></span>  
 <span data-ttu-id="659cc-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="659cc-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="659cc-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="659cc-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="659cc-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="659cc-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="659cc-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="659cc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="659cc-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="659cc-116">See also</span></span>

- [<span data-ttu-id="659cc-117">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="659cc-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="659cc-118">ICLRDebugManager, interface</span><span class="sxs-lookup"><span data-stu-id="659cc-118">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="659cc-119">ICLRGCManager, interface</span><span class="sxs-lookup"><span data-stu-id="659cc-119">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="659cc-120">ICLRHostBindingPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="659cc-120">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="659cc-121">ICLRHostProtectionManager, interface</span><span class="sxs-lookup"><span data-stu-id="659cc-121">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="659cc-122">ICLROnEventManager, interface</span><span class="sxs-lookup"><span data-stu-id="659cc-122">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="659cc-123">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="659cc-123">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="659cc-124">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="659cc-124">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="659cc-125">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="659cc-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
