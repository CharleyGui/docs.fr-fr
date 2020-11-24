---
title: IGCHost2, interface
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
ms.openlocfilehash: 7529ecd215d74eb0eedbec8b90eba367ed20d56f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687741"
---
# <a name="igchost2-interface"></a><span data-ttu-id="12007-102">IGCHost2, interface</span><span class="sxs-lookup"><span data-stu-id="12007-102">IGCHost2 Interface</span></span>

<span data-ttu-id="12007-103">Fournit des méthodes pour obtenir des informations sur le système de garbage collection et pour contrôler certains aspects de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="12007-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12007-104">Pour un nouveau développement, nous vous recommandons d’utiliser à la place l’interface [ICLRGCManager2](iclrgcmanager2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="12007-104">For new development, we recommend that you use the [ICLRGCManager2](iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="12007-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="12007-105">Methods</span></span>  
  
|<span data-ttu-id="12007-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="12007-106">Method</span></span>|<span data-ttu-id="12007-107">Description</span><span class="sxs-lookup"><span data-stu-id="12007-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="12007-108">SetGCStartupLimitsEx, méthode</span><span class="sxs-lookup"><span data-stu-id="12007-108">SetGCStartupLimitsEx Method</span></span>](igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="12007-109">Définit la taille du segment et la taille maximale de la génération 0.</span><span class="sxs-lookup"><span data-stu-id="12007-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="12007-110">Active la génération 0 et la taille des segments supérieure à `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="12007-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="12007-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="12007-111">Requirements</span></span>  

 <span data-ttu-id="12007-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12007-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12007-113">**En-tête :** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="12007-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="12007-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="12007-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="12007-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12007-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12007-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12007-116">See also</span></span>

- [<span data-ttu-id="12007-117">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="12007-117">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="12007-118">Interfaces d'hébergement du CLR</span><span class="sxs-lookup"><span data-stu-id="12007-118">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="12007-119">CorRuntimeHost, coclasse</span><span class="sxs-lookup"><span data-stu-id="12007-119">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
