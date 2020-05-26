---
title: IHostControl, interface
ms.date: 03/30/2017
api_name:
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
ms.openlocfilehash: 9dd89abb332853b966aa81dc506099b7af6ca3b2
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804939"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="144b6-102">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="144b6-102">IHostControl Interface</span></span>
<span data-ttu-id="144b6-103">Fournit des méthodes pour la configuration du chargement des assemblys et pour déterminer les interfaces d’hébergement que l’hôte prend en charge.</span><span class="sxs-lookup"><span data-stu-id="144b6-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="144b6-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="144b6-104">Methods</span></span>  
  
|<span data-ttu-id="144b6-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="144b6-105">Method</span></span>|<span data-ttu-id="144b6-106">Description</span><span class="sxs-lookup"><span data-stu-id="144b6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="144b6-107">GetHostManager, méthode</span><span class="sxs-lookup"><span data-stu-id="144b6-107">GetHostManager Method</span></span>](ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="144b6-108">Obtient un pointeur d’interface vers l’implémentation de l’hôte de l’interface avec le spécifié `IID` .</span><span class="sxs-lookup"><span data-stu-id="144b6-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="144b6-109">SetAppDomainManager, méthode</span><span class="sxs-lookup"><span data-stu-id="144b6-109">SetAppDomainManager Method</span></span>](ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="144b6-110">Avertit l’hôte qu’un domaine d’application a été créé.</span><span class="sxs-lookup"><span data-stu-id="144b6-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="144b6-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="144b6-111">Requirements</span></span>  
 <span data-ttu-id="144b6-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="144b6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="144b6-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="144b6-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="144b6-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="144b6-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="144b6-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="144b6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="144b6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="144b6-116">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="144b6-117">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="144b6-117">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="144b6-118">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="144b6-118">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="144b6-119">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="144b6-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
