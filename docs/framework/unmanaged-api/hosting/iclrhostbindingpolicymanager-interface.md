---
title: ICLRHostBindingPolicyManager, interface
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager
helpviewer_keywords:
- ICLRHostBindingPolicyManager interface [.NET Framework hosting]
ms.assetid: f9da168b-366b-4b2b-bdb9-330b6bad5a6b
topic_type:
- apiref
ms.openlocfilehash: 9ed317a451e6e35aeac3bc1b83f78d1400ea5c07
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136441"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="e3e1d-102">ICLRHostBindingPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="e3e1d-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="e3e1d-103">Fournit des méthodes pour que l’hôte évalue la stratégie de liaison actuelle et communique les modifications de stratégie pour un assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="e3e1d-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e3e1d-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e3e1d-104">Methods</span></span>  
  
|<span data-ttu-id="e3e1d-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="e3e1d-105">Method</span></span>|<span data-ttu-id="e3e1d-106">Description</span><span class="sxs-lookup"><span data-stu-id="e3e1d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e3e1d-107">EvaluatePolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="e3e1d-107">EvaluatePolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="e3e1d-108">Évalue la stratégie de liaison pour le compte de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="e3e1d-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="e3e1d-109">ModifyApplicationPolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="e3e1d-109">ModifyApplicationPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="e3e1d-110">Modifie la stratégie de liaison pour l’assembly spécifié et crée une nouvelle version de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="e3e1d-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e3e1d-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="e3e1d-111">Requirements</span></span>  
 <span data-ttu-id="e3e1d-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3e1d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3e1d-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e3e1d-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e3e1d-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e3e1d-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3e1d-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3e1d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3e1d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3e1d-116">See also</span></span>

- [<span data-ttu-id="e3e1d-117">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="e3e1d-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="e3e1d-118">IHostAssemblyStore, interface</span><span class="sxs-lookup"><span data-stu-id="e3e1d-118">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="e3e1d-119">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="e3e1d-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
