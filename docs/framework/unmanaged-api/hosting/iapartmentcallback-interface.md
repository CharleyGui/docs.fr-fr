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
ms.openlocfilehash: 4424509c16dd1d9f83db117ae7343fa03995297e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126913"
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="ea00c-102">IApartmentCallback, interface</span><span class="sxs-lookup"><span data-stu-id="ea00c-102">IApartmentCallback Interface</span></span>
<span data-ttu-id="ea00c-103">Fournit des méthodes pour effectuer des rappels dans un cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="ea00c-103">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="ea00c-104">Un *cloisonnement* est un conteneur logique au sein d’un processus pour les objets qui partagent les mêmes exigences d’accès aux threads.</span><span class="sxs-lookup"><span data-stu-id="ea00c-104">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ea00c-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ea00c-105">Methods</span></span>  
  
|<span data-ttu-id="ea00c-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="ea00c-106">Method</span></span>|<span data-ttu-id="ea00c-107">Description</span><span class="sxs-lookup"><span data-stu-id="ea00c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ea00c-108">DoCallback, méthode</span><span class="sxs-lookup"><span data-stu-id="ea00c-108">DoCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-docallback-method.md)|<span data-ttu-id="ea00c-109">Exécute la fonction spécifiée dans un cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="ea00c-109">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ea00c-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="ea00c-110">Requirements</span></span>  
 <span data-ttu-id="ea00c-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea00c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea00c-112">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ea00c-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ea00c-113">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ea00c-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea00c-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea00c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea00c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea00c-115">See also</span></span>

- [<span data-ttu-id="ea00c-116">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="ea00c-116">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
