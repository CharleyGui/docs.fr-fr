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
ms.openlocfilehash: 3cf2a945607bf85a51dbec35342ff5ac46878bca
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703570"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="d4ee7-102">ICLRHostBindingPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="d4ee7-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="d4ee7-103">Fournit des méthodes pour que l’hôte évalue la stratégie de liaison actuelle et communique les modifications de stratégie pour un assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="d4ee7-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d4ee7-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d4ee7-104">Methods</span></span>  
  
|<span data-ttu-id="d4ee7-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d4ee7-105">Method</span></span>|<span data-ttu-id="d4ee7-106">Description</span><span class="sxs-lookup"><span data-stu-id="d4ee7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d4ee7-107">EvaluatePolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="d4ee7-107">EvaluatePolicy Method</span></span>](iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="d4ee7-108">Évalue la stratégie de liaison pour le compte de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="d4ee7-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="d4ee7-109">ModifyApplicationPolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="d4ee7-109">ModifyApplicationPolicy Method</span></span>](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="d4ee7-110">Modifie la stratégie de liaison pour l’assembly spécifié et crée une nouvelle version de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="d4ee7-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d4ee7-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="d4ee7-111">Requirements</span></span>  
 <span data-ttu-id="d4ee7-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4ee7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4ee7-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d4ee7-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4ee7-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d4ee7-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4ee7-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4ee7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4ee7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4ee7-116">See also</span></span>

- [<span data-ttu-id="d4ee7-117">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="d4ee7-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="d4ee7-118">IHostAssemblyStore, interface</span><span class="sxs-lookup"><span data-stu-id="d4ee7-118">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="d4ee7-119">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="d4ee7-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
