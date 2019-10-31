---
title: CorRuntimeHost, coclasse
ms.date: 03/30/2017
api_name:
- CorRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRuntimeHost
helpviewer_keywords:
- CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type:
- apiref
ms.openlocfilehash: 512009e053605e2018f1fcbafa422c1a36ddecc1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136907"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="405e7-102">CorRuntimeHost, coclasse</span><span class="sxs-lookup"><span data-stu-id="405e7-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="405e7-103">Fournit des interfaces pour la gestion des applications exécutées par l’common language runtime.</span><span class="sxs-lookup"><span data-stu-id="405e7-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="405e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="405e7-104">Syntax</span></span>  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="405e7-105">Interfaces</span><span class="sxs-lookup"><span data-stu-id="405e7-105">Interfaces</span></span>  
  
|<span data-ttu-id="405e7-106">Interface</span><span class="sxs-lookup"><span data-stu-id="405e7-106">Interface</span></span>|<span data-ttu-id="405e7-107">Description</span><span class="sxs-lookup"><span data-stu-id="405e7-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="405e7-108">ICorConfiguration, interface</span><span class="sxs-lookup"><span data-stu-id="405e7-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="405e7-109">Fournit des méthodes pour configurer le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="405e7-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="405e7-110">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="405e7-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="405e7-111">Fournit des méthodes qui permettent à l’hôte de démarrer et d’arrêter le common language runtime explicitement, de créer et configurer des domaines d’application, d’accéder au domaine par défaut et d’énumérer tous les domaines qui s’exécutent dans le processus.</span><span class="sxs-lookup"><span data-stu-id="405e7-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="405e7-112">IDebuggerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="405e7-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="405e7-113">Fournit des méthodes pour obtenir des informations sur l’état des services de débogage.</span><span class="sxs-lookup"><span data-stu-id="405e7-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="405e7-114">IGCHost, interface</span><span class="sxs-lookup"><span data-stu-id="405e7-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="405e7-115">Fournit des méthodes pour obtenir des informations sur le système de garbage collection et pour contrôler certains aspects de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="405e7-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="405e7-116">IValidator</span><span class="sxs-lookup"><span data-stu-id="405e7-116">"IValidator"</span></span>|<span data-ttu-id="405e7-117">Fournit des méthodes pour la validation des images exécutables portables et un rapport détaillé des erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="405e7-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="405e7-118">spécifications</span><span class="sxs-lookup"><span data-stu-id="405e7-118">Requirements</span></span>  
 <span data-ttu-id="405e7-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="405e7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="405e7-120">**En-tête :** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="405e7-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="405e7-121">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="405e7-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="405e7-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="405e7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="405e7-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="405e7-123">See also</span></span>

- [<span data-ttu-id="405e7-124">Coclasses d’hébergement</span><span class="sxs-lookup"><span data-stu-id="405e7-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
