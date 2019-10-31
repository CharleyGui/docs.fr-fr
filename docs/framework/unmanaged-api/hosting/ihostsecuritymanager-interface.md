---
title: IHostSecurityManager, interface
ms.date: 03/30/2017
api_name:
- IHostSecurityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager
helpviewer_keywords:
- IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type:
- apiref
ms.openlocfilehash: 9b7cc41848e41976f388e38bf22c9ea0f90abbae
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121480"
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager, interface
Fournit des méthodes qui autorisent l’accès et le contrôle sur le contexte de sécurité du thread en cours d’exécution.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetSecurityContext, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|Obtient le [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) demandé à partir de l’hôte.|  
|[ImpersonateLoggedOnUser, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|Demande que le code soit exécuté à l’aide des informations d’identification de l’identité de l’utilisateur actuel.|  
|[OpenThreadToken, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|Ouvre le jeton d’accès discrétionnaire associé au thread actuel.|  
|[RevertToSelf, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|Termine l’emprunt d’identité de l’identité de l’utilisateur actuel et retourne le jeton de thread d’origine.|  
|[SetSecurityContext, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|Définit le contexte de sécurité pour le thread en cours d’exécution.|  
|[SetThreadToken, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|Définit un handle pour le thread en cours d’exécution.|  
  
## <a name="remarks"></a>Notes  
 Un hôte peut contrôler tout l’accès du code aux jetons de thread à la fois par le common language runtime (CLR) et le code utilisateur. Il peut également s’assurer que les informations de contexte de sécurité complètes sont transmises sur des opérations asynchrones ou des points de code avec accès restreint au code. `IHostSecurityContext` encapsule ces informations de contexte de sécurité, qui sont opaques pour le CLR.  
  
 Le CLR gère le contexte de thread managé en interne. Il interroge l' `IHostSecurityManager` spécifique au processus dans les cas suivants :  
  
- Sur le thread finaliseur, pendant l’exécution du finaliseur.  
  
- Pendant l’exécution du constructeur de module et de classe.  
  
- À des points asynchrones sur le thread de travail, dans les appels à la méthode [IHostThreadPoolManager :: QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) .  
  
- Dans la maintenance des ports de terminaison d’e/s.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostSecurityContext, interface](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
