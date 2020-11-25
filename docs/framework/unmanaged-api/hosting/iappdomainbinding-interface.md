---
title: IAppDomainBinding, interface
ms.date: 03/30/2017
api_name:
- IAppDomainBinding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainBinding
helpviewer_keywords:
- IAppDomainBinding interface [.NET Framework hosting]
ms.assetid: 368881ab-c4ea-4731-bf22-c596aac7c66c
topic_type:
- apiref
ms.openlocfilehash: 652739ad51e0a177f7b0fc6c0c9a11508c820bb3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721723"
---
# <a name="iappdomainbinding-interface"></a><span data-ttu-id="d95f0-102">IAppDomainBinding, interface</span><span class="sxs-lookup"><span data-stu-id="d95f0-102">IAppDomainBinding Interface</span></span>

<span data-ttu-id="d95f0-103">Fournit une méthode appelée par le common language runtime (CLR) pour notifier l’application hôte qu’un domaine d’application a été créé.</span><span class="sxs-lookup"><span data-stu-id="d95f0-103">Provides a method that is called by the common language runtime (CLR) to notify the host application that an application domain has been created.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d95f0-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d95f0-104">Methods</span></span>  
  
|<span data-ttu-id="d95f0-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d95f0-105">Method</span></span>|<span data-ttu-id="d95f0-106">Description</span><span class="sxs-lookup"><span data-stu-id="d95f0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d95f0-107">OnAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="d95f0-107">OnAppDomain Method</span></span>](iappdomainbinding-onappdomain-method.md)|<span data-ttu-id="d95f0-108">Appelée par le common language runtime (CLR) pour notifier l’hôte qu’un domaine d’application a été créé.</span><span class="sxs-lookup"><span data-stu-id="d95f0-108">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d95f0-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d95f0-109">Requirements</span></span>  

 <span data-ttu-id="d95f0-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d95f0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d95f0-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d95f0-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d95f0-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d95f0-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d95f0-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d95f0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d95f0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d95f0-114">See also</span></span>

- [<span data-ttu-id="d95f0-115">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="d95f0-115">Hosting Interfaces</span></span>](hosting-interfaces.md)
