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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 942c9544a6ce868c3b6296569d4a16a44281cdba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758320"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="86f42-102">CorRuntimeHost, coclasse</span><span class="sxs-lookup"><span data-stu-id="86f42-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="86f42-103">Fournit des interfaces pour la gestion des applications qui sont en cours d’exécution par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="86f42-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86f42-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86f42-104">Syntax</span></span>  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="86f42-105">Interfaces</span><span class="sxs-lookup"><span data-stu-id="86f42-105">Interfaces</span></span>  
  
|<span data-ttu-id="86f42-106">Interface</span><span class="sxs-lookup"><span data-stu-id="86f42-106">Interface</span></span>|<span data-ttu-id="86f42-107">Description</span><span class="sxs-lookup"><span data-stu-id="86f42-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="86f42-108">ICorConfiguration, interface</span><span class="sxs-lookup"><span data-stu-id="86f42-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="86f42-109">Fournit des méthodes pour configurer le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="86f42-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="86f42-110">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="86f42-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="86f42-111">Fournit des méthodes qui permettent à l’hôte démarrer et arrêter le common language runtime explicitement, pour créer et configurer des domaines d’application, pour accéder au domaine par défaut et d’énumérer tous les domaines en cours d’exécution dans le processus.</span><span class="sxs-lookup"><span data-stu-id="86f42-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="86f42-112">IDebuggerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="86f42-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="86f42-113">Fournit des méthodes pour obtenir des informations sur l’état des services de débogage.</span><span class="sxs-lookup"><span data-stu-id="86f42-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="86f42-114">IGCHost, interface</span><span class="sxs-lookup"><span data-stu-id="86f42-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="86f42-115">Fournit des méthodes pour obtenir des informations sur le système de garbage collection et contrôler certains aspects du garbage collection.</span><span class="sxs-lookup"><span data-stu-id="86f42-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="86f42-116">« IValidator »</span><span class="sxs-lookup"><span data-stu-id="86f42-116">"IValidator"</span></span>|<span data-ttu-id="86f42-117">Fournit des méthodes pour la validation d’images exécutables portables et des rapports détaillés d’erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="86f42-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="86f42-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="86f42-118">Requirements</span></span>  
 <span data-ttu-id="86f42-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86f42-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86f42-120">**En-tête :** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="86f42-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="86f42-121">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="86f42-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86f42-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86f42-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86f42-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86f42-123">See also</span></span>

- [<span data-ttu-id="86f42-124">Coclasses d’hébergement</span><span class="sxs-lookup"><span data-stu-id="86f42-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
