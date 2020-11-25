---
title: IApartmentCallback, interface
ms.date: 03/30/2017
api_name:
- IApartmentCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IApartmentCallback
helpviewer_keywords:
- IApartmentCallback interface [.NET Framework hosting]
ms.assetid: 57c33c58-bf0b-4533-b569-e6a682d02cba
topic_type:
- apiref
ms.openlocfilehash: 0f38314df766b74164bf5e98d9b2153d2dddbcc1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721736"
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="356d7-102">IApartmentCallback, interface</span><span class="sxs-lookup"><span data-stu-id="356d7-102">IApartmentCallback Interface</span></span>

<span data-ttu-id="356d7-103">Fournit des méthodes pour effectuer des rappels dans un cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="356d7-103">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="356d7-104">Un *cloisonnement* est un conteneur logique au sein d’un processus pour les objets qui partagent les mêmes exigences d’accès aux threads.</span><span class="sxs-lookup"><span data-stu-id="356d7-104">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="356d7-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="356d7-105">Methods</span></span>  
  
|<span data-ttu-id="356d7-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="356d7-106">Method</span></span>|<span data-ttu-id="356d7-107">Description</span><span class="sxs-lookup"><span data-stu-id="356d7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="356d7-108">DoCallback, méthode</span><span class="sxs-lookup"><span data-stu-id="356d7-108">DoCallback Method</span></span>](iapartmentcallback-docallback-method.md)|<span data-ttu-id="356d7-109">Exécute la fonction spécifiée dans un cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="356d7-109">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="356d7-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="356d7-110">Requirements</span></span>  

 <span data-ttu-id="356d7-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="356d7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="356d7-112">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="356d7-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="356d7-113">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="356d7-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="356d7-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="356d7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="356d7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="356d7-115">See also</span></span>

- [<span data-ttu-id="356d7-116">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="356d7-116">Hosting Interfaces</span></span>](hosting-interfaces.md)
