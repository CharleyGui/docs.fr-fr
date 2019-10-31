---
title: ICLRHostProtectionManager, interface
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
ms.openlocfilehash: 0487a87420c888cf5466f54c28c2d89623260add
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141053"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="cd7dc-102">ICLRHostProtectionManager, interface</span><span class="sxs-lookup"><span data-stu-id="cd7dc-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="cd7dc-103">Permet à l’hôte de bloquer des classes, des méthodes, des propriétés et des champs managés spécifiques de s’exécuter dans du code de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="cd7dc-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cd7dc-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="cd7dc-104">Methods</span></span>  
  
|<span data-ttu-id="cd7dc-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="cd7dc-105">Method</span></span>|<span data-ttu-id="cd7dc-106">Description</span><span class="sxs-lookup"><span data-stu-id="cd7dc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd7dc-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="cd7dc-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="cd7dc-108">Fournit une garantie que certaines conditions de concurrence rares qui peuvent provoquer des erreurs d’common language runtime fatales (CLR) ne se produiront jamais.</span><span class="sxs-lookup"><span data-stu-id="cd7dc-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="cd7dc-109">SetProtectedCategories, méthode</span><span class="sxs-lookup"><span data-stu-id="cd7dc-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="cd7dc-110">Spécifie les catégories de types et de membres managés dont l’exécution doit être bloquée dans du code de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="cd7dc-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd7dc-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="cd7dc-111">Requirements</span></span>  
 <span data-ttu-id="cd7dc-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd7dc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd7dc-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cd7dc-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd7dc-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cd7dc-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd7dc-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd7dc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd7dc-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd7dc-116">See also</span></span>

- [<span data-ttu-id="cd7dc-117">EApiCategories, énumération</span><span class="sxs-lookup"><span data-stu-id="cd7dc-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="cd7dc-118">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="cd7dc-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
